---
title: "touchscreen installation"
date: 2009-05-06
forum: General Help
---

### Post by mario1 on 2009-05-06
hey guys im new to ubuntu and im trying to install it on a PioneerPOS system with a tocuh screen, im able to get everything except the proper display driver and the touch screen to work. 

i contacted the hardware department at Pioneer and they gave me the instructions below but I'm very new to linux and i dont know exactly how to do everything they are describing, is there anyone who could give me a "dumbed down" version of these instruction of exactly what i have to type in terminal to get it to work? 

im using a standard installation and directory structure with ubuntu version 8.10


[instructions from pioneer]


If you are installing Ubuntu, all of the system drivers can be detected and installed automatically. But because Ubuntu is using intel's latest VGA driver it causes some problem. So you will have to edit the X configuration file, xorg.conf. Change the line with "Intel" to "i810" then restart the X windows and you should be fine. 

The other driver that you have to install yourself is the touchscreen driver. You can download the drivers from : [http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm). Choose the driver according to your X server version. 
 
Now the solution on how to make the internal serial interface to work under Linux -- All you have to do is to
configure the Linux kernel to recognize more than 4 serial ports. Add the following kernel boot option to /boot/grub/menu.lst file. 

8250.nr_uarts=6

 Also add the followings to /etc/rc.local:

setserial /dev/ttyS4 port 0X2F0 irq 11 uart 16550A baud_base 115200
setserial /dev/ttyS5 port 0X2E0 irq 10 uart 16550A baud_base 115200

Then follow the Driver Guide to install the touchscreen drivers. Then make sure that COM5 is used for the touchscreen. Check the x configuration file, xorg.conf and make sure under InputDevice section you see this line : 

Option "Device" "/dev/ttyS4"

Once the driver installation is complete then you can reboot the system. 



any tips or advice would be much appreciated.

---

### Post by mario1 on 2009-05-11
bump

---

### Post by mario1 on 2009-05-12
anyone?

---

