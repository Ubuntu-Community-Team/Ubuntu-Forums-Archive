---
title: "How do you set 3D/OpenGl"
date: 2006-01-27
forum: Gaming &amp; Leisure
---

### Post by reaper32hell on 2006-01-27
Oi with Mandriva2005/Mandrake10.2 3D and OpenGL is very very very good but when im on ubuntu breezy it is so slow and with glxgear its like 5-20 fps a second :mad: 

Please give me a solution[-o<  (I have a intel 810 16 megabyte chip card)
The rest of the other games i play uses software so its smoth.

---

### Post by PLAY3ER on 2006-01-27
[QUOTE=reaper32hell]Oi with Mandriva2005/Mandrake10.2 3D and OpenGL is very very very good but when im on ubuntu breezy it is so slow and with glxgear its like 5-20 fps a second :mad: 

Please give me a solution[-o<  (I have a intel 810 16 megabyte chip card)
The rest of the other games i play uses software so its smoth.[/QUOTE]

are you talking about it being in game? or just on the Destop?

PS: sorry im tried tonight, all i had to do was do this 
do you know how to edit in consle? then do 

cd /etc/X11/
look for a file called xorg.conf
type  vi xorg.conf

and find the line where it says "nv" now change it to nvidia 

and  do  :wq and enter to save, and logout, and Ctrl+Alt+Delete to restart the X server, then log back on and as its starting you should see an Nvidia Screen

---

### Post by leech on 2006-01-27
There IS an easier way...  'sudo nvidia-glx-config enable'

Leech

---

### Post by PLAY3ER on 2006-01-27
sorry im just getting use to Ubuntu

---

### Post by reaper32hell on 2006-01-27
Man i dont use NVIDIA

i use a dumb old friggin intel 810 chipset with 16 memory and 32bit ram

only works with 16 bit colour games (mostly windows games use 16bit so i use cedega) with 24 bit its slow!
so any solutions? thanks,

(MSN [email]reaper32hell@hotmail.com[/email])

---

