# Graficacion-practica1
practica de mapa de bits para que una imagen cambie a una escala de grises
# codigo 
package Proceso;

import java.awt.Color;

import java.awt.image.BufferedImage;

import java.io.File;

import javax.imageio.ImageIO;

import javax.swing.JFileChooser;

import javax.swing.filechooser.FileNameExtensionFilter;


public class proceso {
    
    /**************************se carga la imagen****************************/
    private BufferedImage imageActual;
    
    /*************************metod
	 * @return o************************************/
    public BufferedImage abrirImagen(){
      //                  varibles 
        BufferedImage bmp=null;
        //                         cuadro de diálogo para la imagen
        JFileChooser selector=new JFileChooser();
   
        selector.setDialogTitle("Eliga la  imagen");                   //titulo 
    
        FileNameExtensionFilter filtroImagen = new FileNameExtensionFilter("JPG & GIF & BMP", "jpg", "gif", "bmp");
        selector.setFileFilter(filtroImagen);
	
      
        int flag=selector.showOpenDialog(null);
	
        /***********************comprueva la aceptacion ********************************/
        if(flag==JFileChooser.APPROVE_OPTION){
            try {
                
                File imagenSeleccionada=selector.getSelectedFile();
                bmp = ImageIO.read(imagenSeleccionada);
            } catch (Exception e) {
            }
                 
        }
        /****************************************la funcion de imageActual hace que la imagen cargada pasa a la imagen actual*****************************************/
        imageActual=bmp;
        return bmp;
    }
    
    //                                           se declaran las variables donde se almacenaran los pixeles 
    public BufferedImage escalaGrises(){
        int mediaPixel,colorSRGB;
        Color colorAux;
                
   
        for( int i = 0; i < imageActual.getWidth(); i++ ){
            for( int j = 0; j < imageActual.getHeight(); j++ ){
		    
		    
                //                                 funcion de Almacenamiento del color del píxel
                colorAux=new Color(this.imageActual.getRGB(i, j));
               //                                  funcion para lograr los grises 
                mediaPixel=(int)((colorAux.getRed()+colorAux.getGreen()+colorAux.getBlue())/3);
                colorSRGB=(mediaPixel << 16) | (mediaPixel << 8) | mediaPixel;
                imageActual.setRGB(i, j,colorSRGB);
            }
        }
        return imageActual;
    }
}
# Ejecucion 
![Captura de pantalla (27)](https://user-images.githubusercontent.com/73785441/97923544-c4ef2580-1d23-11eb-943c-a2376ed438fe.png)

![Captura de pantalla (28)](https://user-images.githubusercontent.com/73785441/97923583-d7695f00-1d23-11eb-893f-55e163d08819.png)

![Captura de pantalla (29)](https://user-images.githubusercontent.com/73785441/97923634-ec45f280-1d23-11eb-8299-fb37591d7117.png)
