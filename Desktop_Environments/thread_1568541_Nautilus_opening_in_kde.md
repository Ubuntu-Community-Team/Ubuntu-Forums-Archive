---
title: "Nautilus opening in kde"
date: 2010-09-05
forum: Desktop Environments
---

### Post by someitalian123 on 2010-09-05
When every I insert an sd card into my computer nautilus automatically opens to view the files on that sd card. The problem with this is that I'm in kde and I don't want nautilus to open, just because it doesn't belong in kde. I don't know how this happened but i was wondering is their anyway to switch this feature on and off?

---

### Post by someitalian123 on 2010-09-05
I tried

gconftool --type Boolean --set /apps/nautilus/preferences/media_automount  false
[FONT=monospace]
And it keep it from automatically opening it but when I click open in file manager it opens both Nautilus and Dolphin. My default file manager is Dolphin. [/FONT][FONT=monospace]
[/FONT]

---

### Post by 3Miro on 2010-09-05
Is this pure kubuntu or kubuntu + gnome (ubuntu-desktop) or ubuntu + kde (kubuntu-desktop).

---

### Post by someitalian123 on 2010-09-05
It's kubuntu with gnome installed later on. But I've had gnome installed for a little while now with out these problems.

---

### Post by someitalian123 on 2010-09-05
[FONT=monospace]As a test i tried switching my default file manger to [/FONT][FONT=monospace]Nautilus and then when I clicked open in file manger it opened two [/FONT][FONT=monospace]Nautilus windows. After that I switched back to dolphin again and the problem was gone.

Edit false alarm, the [/FONT][FONT=monospace]Nautilus window opened I just didn't notice it.
[/FONT]

---

### Post by 3Miro on 2010-09-05
Glad to hear that you have resolved the issue. The problem must have been with Gnome overwriting some KDE setting. Those two don't always play nice with each other especially since Ubuntu is rather Gnome-centric in general.

---

### Post by someitalian123 on 2010-09-05
I didn't solve the issue didn't you see my edit

---

### Post by someitalian123 on 2010-09-06
bump

---

### Post by someitalian123 on 2010-09-07
I completely uninstalled gnome using this method, only i used aptitude instead because it wasn't working with apt-get, had i used aptitude from the start I wouldn't have this problem

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

and Nautilus still remains to open in kde

I tried

sudo apt-get remove Nautilus

and i get
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package Nautilus

I tried that with aptitude and I get

Couldn't find any package matching "Nautilus", and more than 40
packages contain "Nautilus" in their description.
Couldn't find any package matching "Nautilus", and more than 40
packages contain "Nautilus" in their description.
The following packages will be REMOVED:
  apport-hooks-medibuntu{u} freepats{u} libass4{u} libavutil-extra-49{u} libcdaudio1{u} 
  libcelt0-0{u} libdca0{u} libdirac-encoder0{u} libenca0{u} libfftw3-3{u} libflite1{u} 
  libgme0{u} libgsm1{u} libiptcdata0{u} libkate1{u} libmimic0{u} libmms0{u} libofa0{u} 
  libopencore-amrnb0{u} libopencore-amrwb0{u} libopenjpeg2{u} libopenspc0{u} liborc-0.4-0{u} 
  libswscale0{u} libwildmidi0{u} libxvidcore4{u} 

I didn't remove those packages because I already removed enough packages that I use, just to get rid of gnome just to fix this problem,  but apparently gnome isn't all gone because Nautilus is still here! How do I get rid of Nautilus!

Edit: O.k after restarting the computer the problem seems to have disappeared, now I have stuff to reinstall, and whats weird is that my knetworkmanager is slower to load on start up, any idea on why that is. I got rid of close to 700 packages. Any idea of what packages being removed made it slower.

EDit 2: ok never mind what i said about the network manager it's fine now.

---

