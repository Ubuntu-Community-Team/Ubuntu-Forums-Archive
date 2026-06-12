---
title: "Cosas que me gusta Karmic Koala 9.10"
date: 2010-03-19
forum: Centroamerica Team
---

### Post by riomacho on 2010-03-19
No es para rajar, pero tengo varios años de usar Ubuntu y hay unas cosas que realmente me gusta, particularmente en la nueva edición.  Pense en hacer una lista para referencia, principiantes ó personas que estan pensando cambiar a Ubuntu. Agarra sus palomitas para disfrutar el espectaculo

  :popcorn:

Yo utilizo una AMD 64 bit sistema en el PC, y tambien un laptop Dell 32bit.  

[LIST]
[*]**Rythmbox -** Ya he grabado mis CDs y convertido los mp3 a formato abierto - OGG.  Tengo varios listas de canciones, se puede poner reciente tocados para una larga jornada.  Ahora que tengo Acelera en la casa escucho emisoras por Internet - [http://dir.xiph.org/index.php](http://dir.xiph.org/index.php)  
[*] **Login automatico.  **No debe usarse en laptop, ni en la oficina. Pero es bonito la opción en la casa. 
[*] **Foto pantalla** En el menu de acesorios o la tecla imprir pantalla.  Se abre un dialogo, para escoger entre pantalla entera, ventana o una area del pantalla que uno dibuja con el raton.  Me fascina para ayudar gente o mostrar algo que estoy viendo en el browser. 
[*]  **Espacios de Trabajo**  Puede tener multiples escritorios, 2, 4, 6 ,  8.  Yo lo uso mucho cuando abro el GIMP, que tiene muchas ventanas.   Pero tambien cuando estoy trabajando en algo y tengo que de repente ver un correo o sitio en Internet.
[*] **Lanzadores - Gavetas ** Puede lanzar uno, dos, o mas aplicaciones.  Hasta un menu entero.   haga clic en "agrega a panel, y después en lanzador de aplicaciones. Se lanza un menu o un software desde el panel.  O ... puede selecionar "gaveta"  En una gaveta se puede lanzar un menu, o un software.  ¡Que Chiva! 
[*] **Open Office** Muy bueno, ya casi no hay diferencia entre esto y MS Office.  Particularmente me fascina que se puede guardar como FLASH y PDF cualquier hoja de calculo, documento o presentación para compartir. 
[*] **GIMP** No soy muy adepto digamos con los graficos, pero este programa es muy potente.  Hablan que reemplaza PHOTOSHOP, pero no he usado este para comparar.  Es excelente para retocar fotos, cambiar de tamaño o resolución, o formatear - por ejemplo de cambiar un JPEG a GIF o PNG. Hace image maps o banners de GIF si tiene un sitio en Internet es excelente. 
[*] **Evolution** Estuve probando muchos programas que antes el Evolution no me funcionó bien en el 64bit.  Ahora si es excelente, y esta muy integrado con el Gnome Desktop.  Estoy muy complacido de poder usarlo, y que algunas de las cositas que me molestaba ya son arreglados. 
[/LIST]

Bueno, ya esto es bueno para empezar, agrege sus trucos aquí para que compartimos

---

### Post by ubuntu27 on 2010-03-19
Hola riomacho. Gusto en saber que te gusta Ubuntu Linux.

Buenos puntos, aunque la mayoría son cosas que se podía hacer en las versiones anteriores.


Acerca de la música. Realmente no recomiendo que cambies el MP3 a ogg, puesto que la calidad del sonido se deteriora.
En mi caso, si tenia una colección mp3, lo dejo sin cambiar. Y si tengo un CD, lo extraigo con formato abierto como Flac o Vorbis (ogg, oga).

---

### Post by riomacho on 2010-03-25
Otra cosa que me gusta de Linux es el uso del terminal y linea de comanda. Aunque para el usuario nuevo puede sentir incomodo, hay muchas cosas muy útiles que se puede hacer: configurar aspectos del sistema, programas utiles que no usan el interfaz gráfico, y ayudas rápidas sobre estas mismas.  

Aquí hay unas cosas cualquier persona puede probar (si tiene priviligeos) para mojarse las patas digamos. :p

**Un generador de palabras claves **
Ya todo el mundo esta preocupado por seguridad o manejar membresías. En un sitio de redes sociales, por ejemplo, es tentador utilizar cualquier clave.  Pero lo más recomendable es usar claves que tienen letras mayúsculas, letras minúsculas, y numeros, si no simbolos también. Pero son dificiles de acordar, y es muy útil tener memorizadas sus claves. También es difícil inventar nuevas cada rato.  El "automatic password generator" (apg) resuelve ambos casos.  A continuación le explico como instalar lo y usarlo con el terminal.  

**Abrir Terminal**
En su panel haga clic en Programas,--> Acesorios --> Terminal . Le abre una venta pequeña con unas letras diciendo algo así: 
```
su-nombre-usuario@su-equipo:~$ 
```

**Instalar APG**
Tecla el siguente en su terminal:
```
sudo apt-get install apg 
```

Su equipo le pide el password, hay que teclarlo y presionar <enter>.  No se preocupa que no se mueve el cursor, es normal.  Ya empieza a trabajar el sistema y rapidamente esta instalado.  

**Utilizar APG**
Suponemos que ya expiró su clave en el Banco Nacional o BCR.  Abre terminal y tecla apg y <enter>  Aparece unas intrucciones, basicamente que hay que teclar 16 carácters y presionar <enter>.  Por ejemplo, "Banco Nacional de Costa Rica" 

Ya aparece sus claves, por ejemplo:
> BegIlIk1 (Beg-Il-Ik-ONE)
ClimVuv3 (Clim-Vuv-THREE)
AyHokBob0 (Ay-Hok-Bob-ZERO)
yokAryeed9 (yok-Ar-yeed-NINE)
1FlowAgseco (ONE-Flow-Ags-ec-o)
7Obagconuv (SEVEN-Ob-ag-con-uv)


El parte interesante es que son pronunciables, así que son más faciles de acordar.  Escoge uno que le gusta y listo  =D>

**Que pasa si ... ? **
¡Que bueno! ¿Pero que pasa si quiere cambiar un poco lo que sale? En estas programas hay manuales, abre un otro terminal y pone:
```
man apg
```
Allí aparece el manual del programa, que le da opciones.  Por ejemplo, si necesita claves de 12 digitos, el manual le explique que puedes arrancar el APG así: 
```
apg -m 12 -x 12
```
> tusckoajVeep
pryapAdMybs$
KazyowtixLyb
MitAxvoubsye
AdumsoabOdVa
ViAgCoybvir0

**Nota importante:** para salir del manual, presione ```
q
```

**Otras cosas divertidos del terminal**
Prueba teclando algunas de estas comandas para seguir jugando con el terminal: 

```
ping -c 5 192.168.1.1
``` (podría ser un maquina en su red local, tal vez el router)
```
ping 209.191.122.70 -c 5
``` (yahoo.com)

```
whois ubuntuforums.org
```
La información del registrante 
```
dir
```
y despues
```
cd Documentos
```
y despues
```
dir
```
Se ve su sistema de archivos in el directorio donde esta.  

Como se puede ver, el terminal esta conectado a Internet, y puede ser utilizado para manejar equipos remotos sobre largas distancias.  Es una herramienta sorprendamente poderosa, y vale la pena ir utilizando cada vez más.  

**Trucos con Terminal**
Varios particularidades muy útiles de saber sobre el terminal:
Para ver comandas que se han utilizado antes, presione la tecla "flecha arriba". Cada vez que lo presiona pasa otra comanda de la historia.  Para repitir una, presione <enter> (¡no lo hagas si no sabe que hace!) Usa la tecla "flecha abajo" para volverse. 

Si esta siguendo un tutorial, digamos en ubuntuforums.org y las comandas son muy largas, puedes copiar y pegar.  Copia el texto en su browser, y depués haga un clic en la ventana del terminal.  En el menu arriba presiona Editar --> pegar  También puede usar el teclado <ctrl> + <shift> + <v>
Igual para copiar desde Terminal a un documento o formulario:
Agarra el texto con su mouse, y en el menu arriba presiona Editar --> o con el teclado <ctrl> + <shift> + <c>

Para salir de terminal, tecla ```
exit
```

---

### Post by gabo.cr on 2010-03-27
Muy útiles las recomendaciones.
No conocía los generadores de claves, vale la pena probarlos.

;)

---

