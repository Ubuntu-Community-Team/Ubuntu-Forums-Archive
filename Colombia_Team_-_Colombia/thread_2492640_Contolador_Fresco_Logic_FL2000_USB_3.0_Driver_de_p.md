---
title: "Contolador Fresco Logic FL2000 USB 3.0 Driver de pantalla"
date: 2023-11-18
forum: Colombia Team - Colombia
---

### Post by miguramc on 2023-11-18
Un saludo a todos.


Este es mi historia:
Tengo un monitor VGA que deseo conectar a mi portátil para trabajarcon 3 pantallas.  Conseguí un adaptador de VGA a USB 3.0 que viene con un CD de Drivers.  Estos se instalan y funcionan perfectamente en Windows10.  Ahora quiero hacer lo mismo en Ubuntu 22.04.  Buscando en la red encontré una pagina de GitHub donde esta un archivo que dicen que permite ejecutar los drivers ([https://github.com/FrescoLogic/FL2000](https://github.com/FrescoLogic/FL2000)).  


Descargue este archivo y utilizando el VSCode abrí y edite el archivo Makefile, tal y como indican las instrucciones:


***6. How do I compile & test the kernel driver?***
***6a. Compile the driver***
***Find your kernel source tree, and edit src/Makefile. Locate the following line:***
****
***KERNEL_PATH = /usr/src/linux-headers-4.4.0-72-generic`***
***Modify this line so that it points to the correct source tree. After that, run make to create fl2000.ko and run insmod fl2000.ko to load the driver.***
****
***6b. Test the driver***
***In the sample folder, run make to create fltest. If you you are using a cross compiler to build the binary for specific platforms, you need to specify that specific compiler in src/Makefile.***
****
***Run ./fltest 0 as superuser to run the test. The driver provides several user mode buffer access methods (e.g copy to kernel internal buffer, or directly locking down user buffer). Look at fl2000_ioctl.h for detailed information.***
****




Cambie la ruta del PATH poniendo mi versión del kernel.


***#KERNEL_PATH = ../../../kernel/linux-3.10.0-327.13.1.el7***
***#KERNEL_PATH = /usr/src/kernels/`uname -r`***
***#KERNEL_PATH = /usr/src/kernels/3.10.0-327.13.1.el7.x86_64***
***#KERNEL_PATH = /usr/src/linux-headers-`uname -r`***
***#KERNEL_PATH = /usr/src/linux-headers-4.4.0-72-generic`***
***KERNEL_PATH = /usr/src/linux-headers-6.2.0-36-generic`***


Aquí empieza mi problema.  No se como ejecutar esta modificación y que mi Ubuntu reconozca este archivo.   Dice que debe correrse para crear un archivo "fl2000.ko", pero no se como llegar a este punto.

No pude pegar imagenes de los programas:(


Si alguien puede ayudarme dándome unas indicaciones estaré muy agradecido.

---

### Post by alanscelza on 2024-07-02
Hola! 

¿Pudiste solucionarlo? 

Tengo el mismo adaptador, en Ubuntu 22.04 LTS con kernel 6.5.0-41-generic y tampoco pude instalarlo de momento.

---

