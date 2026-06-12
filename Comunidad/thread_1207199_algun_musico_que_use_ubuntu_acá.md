---
title: "algun musico que use ubuntu acá?"
date: 2009-07-07
forum: Comunidad
---

### Post by clave on 2009-07-07
hola, bueno yo ya tengo un thread puesto en hardware y la verdad se vendran mas por la misma clases de dudas: para trabajar en audio en ubuntu, por lo que me pregunte, habra algun musico trabajando en ubuntu de quienes me leen aqui? si es asi porfavor que responda!, he encontrado a musicos con problemas similares pero de otros lugares y seria genial encontrar algun musico que use ubuntu y hable español, para asi poder saber mejor donde ir para lograr lo que quiero.

siempre con las ganas de aprender y hacer la mejor musica posible en esta plataforma exquisita, dejo este mensaje flotando para que alguien lo responda.

---

### Post by augias on 2009-07-08
Yo pase un rato usando mi programa de musica bajo wine. No funcionaba mal, pero salio una nueva version y wine ya no aguantaba los updates. El programa es [jeskola buzz]("http://www.jeskola.net"), por si acaso. 

Ahora lo que hago es usar una particion de XP dedicada a la musica, sin programas en absoluto salvo los que ocupo para producir. Tambien me preocupé de apagar todos los procesos inecesarios de seguridad, conectividad, actualizacion etcetera, y en verdad corre excelente, todo el poder del cpu y la ram dedicados a la aplicacion. 

Si tienes curiosidad, te podria recomendar el clon de buzz para linux. Es para secuenciar y armar musica electronica. Son [aldrin]("http://aldrin-sequencer.googlecode.com/files/aldrin-0.13.tar.gz") y la libreria de fondo que es [armstrong]("http://aldrin-sequencer.googlecode.com/files/armstrong-0.2.6.tar.gz"). Velos en [http://code.google.com/p/aldrin-sequencer/downloads/list](http://code.google.com/p/aldrin-sequencer/downloads/list)

Para instalarlos: 
1, Crea una carpeta que se llame "Source" en tu home. 

2, Desempaquetea ambos archivos .tar.gz en la carpeta "Source" para que tengas asi dos carpetas nuevas adentro, "armstrong" y "aldrin"

3, baja los paquetes que te van a faltar
```
sudo apt-get install python python-ctypes python-gtk2 librsvg2-common scons libsndfile1-dev zlib1g-dev libasound2-dev jackd libjack-dev libsamplerate0-dev libfftw3-dev
```

4, Entra a la carpeta armstrong en la consola.
```
cd ~/Source/armstrong
```
ahora se configura armstrong pa tu maquina.
```
scons configure
```
si te sale un error y no puede seguir, va a ser porque te falta una dependencia. anota el programa que te dice que falta, buscalo con 
```
aptitude search nombredelpaquete
```
y cuando lo encuentras, bajalo con
```
sudo apt-get install nombredelpaquete
```
generalmente, y esto es importante, baja los archivos complementarios que terminan con "-dev" si estas atascado, siempre faltan estos archivos -dev cuando crees que ya tienes un paquete instalado. por ejemplo libfftw3-3 y libfftw3-dev. 

5, Cuando scons configure termine de configurar y te sale un resultado positivo, al fin, escribes
```
scons
```
para construir, y luego 
```
sudo scons install
```
para instalar. 

6, ya tienes la libreria de sonido de buzz, la libreria armstrong, que es poderosa. es hora de instalar Aldrin. 
```
cd ~/Source/aldrin
```
entras a la carpeta aldrin y repites lo que hiciste para armstrong:
```
scons configure
```
bajando cualquier archivo -dev u otra dependencia que te falte con "aptitude search nombredelpaquete".
cuando scons configure termine exitosamente, escribes
```
scons
```
y finalmente
```
sudo scons install
```

7, verás el icono de aldrin en tu menu de sonidos. elige tu driver de sonido. si algo anda mal, comienza jack control e inicialo. 

8, si quieres desinstalar cualquiera de estos programas, te vas al directorio del programa en Source y escribes ```
sudo scons install -c
```

Dejame saber que te parece este programa. Hasta el momento, aunque esté en Beta, lo encuentro muy poderoso y entretenido para hacer musica electronica.

---

### Post by Carlos C on 2009-07-09
bueno, hablé con augias y le pedí que hiciera un thread independiente para tratar el tema de aldrin. De esa manera no mezclamos todo y este hilo se queda acá en comunidad.
Saludos.

---

### Post by jci on 2009-07-14
Hola!

Yo vengo usando UbuntuStudio desde 8.04 con resultados buenos (y marginales en 9.04 :-/ ). Asi que puedo echar una mano cuando se necesite.

Saludos!
--j

---

### Post by Patriciologico on 2009-07-19
Hola te puede servir revisar [http://www.musix.org.ar/](http://www.musix.org.ar/) [http://es.wikipedia.org/wiki/Musix](http://es.wikipedia.org/wiki/Musix)

Puedes encontrar ayuda en [http://foros.musix.es/](http://foros.musix.es/) y en [http://www.musix.org.ar/wiki/index.php?title=Ayuda](http://www.musix.org.ar/wiki/index.php?title=Ayuda)

Esa distro no se basa en Ubuntu, pero si en Debían, por lo que se asemeja bastante en funcionamiento y ahí podrás encontrar mas gente dedica a la música con SL como tu.

Saludos!

---

### Post by AnalogIC on 2009-08-15
hola, yo uso xubuntu 8.4 con una tarjeta de audio firewire (focusrite saffireLE), y corro solo aplicaciones open source (en wine tb).

He estado grabando algunas cosas, acostumbrandome al software y he grabado algunas usando vst libres (mediante dssi/vst), ardour compilado, hydrogen release candidate y otras cosillas más.

Soy guitarrista eléctrico y compositor. Utilizo Puredata en la compañía de teatro donde trabajo y me interesaría comenzar a usar el arduino, me llama mucho la atención.

Bueno, ya me "presenté". espero que podamos generar discusión interesante en torno a nuestros intereses. ^_^

saludos

---

