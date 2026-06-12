---
title: "gnome doesn start!!! (URGENT!)"
date: 2005-09-08
forum: Gaming &amp; Leisure
---

### Post by rafakl on 2005-09-08
Hi all!!

I installed thr TORCS (or trocs) racing game, first from apt-get, but i dont get many tracks or cars, so i decided to go to the page and dowload the source.

I started with ./configure and it started giving me tons of errors of missing libraries... so i started downloading all them with apt-get....

when i finished compilind the game and started playing, the game was very slow and crappy, like the first time i installed ubuntu without the nvidia 3d acceleration, so i started "glxgears" and get ULTRA LOW fps.  ](*,) 

I searched with synaptic for my nvidia drivers and nvidia-glx wasn installed !!! (i think it was removed with apt-get when i installed soemthing for TORCS), i did a restart, and gnome didnt start only command-line.

Then i used apt-get install nvidia-glx to get the drivers again, but gnome nor startx works.

What can i do?? im on thesis work and need to use my ubuntu!!!!  :-|

---

### Post by rafakl on 2005-09-08
Solved it!!!

sudo apt-get ubuntu-desktop

thats all!!

 :)

---

