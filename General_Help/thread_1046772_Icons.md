---
title: "Icons"
date: 2009-01-21
forum: General Help
---

### Post by JesseJones on 2009-01-21
Hey,

all right so I'm pretty new to Ubuntu and...

I downloaded the art manager from the Add/Remove applications program. Everything works fine except for the icons. When I download or install the icon package I want using art manager everything seems to go okay but when ever I try to use one of my downloaded icon sets I just get the plain old boring grey folders. All the window frames and other things I download off art manager work why wont the icons?

btw I'm running 8.10 Intrepid Ibex

Thanks in advance!

---

### Post by Wartender on 2009-01-21
there's a link in my sig for a tutorial on this. see if that helps

---

### Post by FAMUgolfer on 2009-01-21
unpackage the icon folder into /usr/share/icons
then go to system>>preference>>appearance>>customize>>icon tab
from here make sure the name of the icon set is highlighted and exit out

Hope this works!!

---

### Post by JesseJones on 2009-01-21
@FAMU

I cant unpackage the archive in /usr/share/icons because I get an error saying I don't have permission to edit the folder.

@War

I followed the link in you sig and downloaded a new set of Icons and installed them according to your direction. (dragging the .tar into the appearance preferences window) the file installed correctly so I went to customize - Icons and selected my new Icon set. I'm still getting grey folders, all the other Icons changed to the new set except the basic folder Icon. 

Any Ideas?

---

### Post by FAMUgolfer on 2009-01-22
open a terminal and type w/o quotes "sudo nautilus"

this will bring up another window which will allow you to move the desired theme into usr/share/icons

good luck!

---

