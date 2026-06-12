---
title: "gnome/kde and trying to get 5.1 sound to work"
date: 2008-05-13
forum: Desktop Environments
---

### Post by eyeonthewinner on 2008-05-13
Ok, so here's the thing... I have a realtek integrated sound card with 5.1 surround sound. My motherboard is an asus a8n-sli deluxe.

wayne@deathstar:~$ lspci | grep AC
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)

so thats the sound device. so, its recognized, but it won't give me 5.1

I purged the alsa stuff
sudo apt-get --purge remove linux-sound base alsa-base alsa-utils
and reinstalled it(and gdm for whatever reason), then the this happened:

In gnome:
It also works with vlc player and noatun but, oddly enough not with amarok in gnome. it gives an error about illegal xine parameters, then no parameters. No gnome based players work such as Rythmbox or totem. Flash sound doesn't work either.

In KDE:
All sound works...

I know its something with one of the /home/wayne/.* and most likely .gnome and .gnome2 but if someone can help, that would be awesome!

Thanks!!

---

### Post by eyeonthewinner on 2008-05-14
shamless bump...

---

### Post by eyeonthewinner on 2008-05-16
shamless bump number 2...

---

### Post by eyeonthewinner on 2008-05-19
come on anyone help please? this can't be that hard...

---

### Post by eyeonthewinner on 2008-05-22
is there anyone out there with my chipset that has it working, PLEASE HELP!!
nVidia Corporation CK804 AC'97

---

