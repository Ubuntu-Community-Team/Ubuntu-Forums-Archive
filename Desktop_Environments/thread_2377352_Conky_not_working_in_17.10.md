---
title: "Conky not working in 17.10 ?"
date: 2017-11-12
forum: Desktop Environments
---

### Post by mrouilla515 on 2017-11-12
I install conky, conky-all from synaptics in Xubuntu 17.10. The installation went fine apparently however conky-all is nowhere to be found. No menu entry and no command line call. No ".conky" home folder was created either.  Typing "conky" in the command line produce an ugly dark window with writing on the left border. I tried to create a .conky folder myself with a valid conky inside but no effect. Is conky suppose to work in Xubuntu 17.10 ?

---

### Post by Frogs Hair on 2017-11-12
The window you saw is the default conky window and if are new to conky I'd suggest experimenting with some completed themes . There is no menu icon for conky though it can be added to startup applications once the theme/syntax is installed. Make sure the themes are compatible with  version 1.10 because older themes may  not work and instructions are often included though not always easy for beginners depending on the theme/syntax.      


[https://www.gnome-look.org/search?projectSearchText=conky](https://www.gnome-look.org/search?projectSearchText=conky)

---

### Post by vasa1 on 2017-11-12
You can create your own *~/.config/conky/conky.conf* based on */etc/conky/conky.conf*. There's no reason for conky not to work in Xubuntu 17.10.

---

### Post by mrouilla515 on 2017-11-12
Hello, yes I am a bit familiar with conky but I confuse conky-all for conky-manager installed on my Manjaro XFCE. It is much easier to setup conky using the manager but It is not in the repo here ???. I copied the .conky folder form Manjaro and was able to start a conky with the conky-startup.sh. 
Can I find the manager somewhere else ?

I found the usual ppa for the manager here [COLOR=#4A4A4A]ppa:teejee2008/ppa but it stop at 16.04, nothing higher.[/COLOR]

---

### Post by mrouilla515 on 2017-11-12
Ok I found this way to install the manager in 17. Works fine now.

[https://www.linuxbabe.com/ubuntu/install-conky-manager-ubuntu-16-04-17-04](https://www.linuxbabe.com/ubuntu/install-conky-manager-ubuntu-16-04-17-04)

---

