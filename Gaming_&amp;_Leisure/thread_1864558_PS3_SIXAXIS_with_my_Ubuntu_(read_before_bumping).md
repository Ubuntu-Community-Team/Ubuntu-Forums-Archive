---
title: "PS3 SIXAXIS with my Ubuntu (read before bumping)"
date: 2011-10-19
forum: Gaming &amp; Leisure
---

### Post by SuicyanidePillz on 2011-10-19
OK... So i have read in these forums and all over the internet and can't figure this out. 
I am trying to use my  SIXAXIS controller to play games on my Ubuntu 11.04 (games lie Sauerbraten Cibe 2, Tremulous, Alien Arena, etc...) but I dont have a bluetooth adapter. I kno there is a way to use the SIXAXIS in Usb mode, but everytime I find a related search on the interwebz it tells me how to do it in bluetooth mode. 
Can someone plz provide a good tutorial on how to pair my SIXAXIS in USB mode? it is now 3 in the morning my time and I have been at this for a couple hours. Thx in advance!!!

SuicyanidePillz    <------- also my PSN ID

---

### Post by LERecords on 2011-10-19
well... i have been recently playing around and got my sixaxis ps3 controler to work only in usb mode.. so i'll try to help you out here

assumptions: your ps3 controler is plugged in via usb to a usb port.

my how to: I downloaded the following:

sudo apt-get install libusb-dev libusb-0.1-4
sudo apt-get install xserver-xorg-input-joystick

then, restart everything, you can leave the controller plugged in.
when you get back to the desktop, you can hit the ps button on the controller (the lights will blink constantly, this is normal)
if you want to make sure that your computer is recognizing the controller, go to /dev/input/ and look for a file 
called js01.. if you see it then its connected..

otherwise thats about all i know for connecting it via usb.. hope that helps

---

### Post by SuicyanidePillz on 2011-10-20
thank You so much dude. I hve looked everywhere and could only find bluetoothe tutorials... you really helped

---

