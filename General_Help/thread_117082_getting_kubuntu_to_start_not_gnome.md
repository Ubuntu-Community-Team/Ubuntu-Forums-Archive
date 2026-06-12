---
title: "getting kubuntu to start not gnome"
date: 2006-01-14
forum: General Help
---

### Post by helmet on 2006-01-14
okay i don't know what happened to my other post but whatever.

i want to start kubuntu desktop from the command line, like after a console login. if i use the startx command, gnome cranks up. how to i start the kubuntu desktop? yes i'm new.

---

### Post by sharke on 2006-01-14
Not sure but you could try startkde
Regards
Sharke

---

### Post by JAwuku on 2006-01-14
Hi there,

if the computer boots up into the brown gnome login screen, there should be a Sessions button in the middle of the screen. From there you can select KDE and make it the default.

If you have both gnome and KDE on your system, you can make your computer boot up to the blue kubuntu login screen, by running the command:

**sudo dpkg-reconfigure kdm**

and select kdm (the kubuntu login screen).

---

### Post by helmet on 2006-01-14
the startkde gives me a bunch of errors about unable to open display, can't connect to X server, and a bunch of other things, and then just shuts down the startkde scripts and puts me back at the command line

---

### Post by helmet on 2006-01-14
kubuntu pops up and i log into that by default but if i do a console login and run startx it starts gnome. that's what i want to change

i tried sudo dpkg-reconfigure kdm and selected kdm but startx still cranks up gnome

---

### Post by aysiu on 2006-01-14
[QUOTE=helmet]kubuntu pops up and i log into that by default but if i do a console login and run startx it starts gnome. that's what i want to change

i tried sudo dpkg-reconfigure kdm and selected kdm but startx still cranks up gnome[/QUOTE] Try ```
sudo nano /etc/X11/default-display-manager
``` and change it from ```
/usr/sbin/gdm
``` to ```
/usr/bin/kdm
```

---

### Post by Strongbad on 2006-01-15
ok, here's what you need to do, get into synaptic (in kde or gnome), and find "kdm" install that, and when it's finished, you will get a message asking if you wan't to use kdm or gdm display manager. Select kdm, restart X, and you should be good to go! Good luck! 

P.S. You can also use the command "sudo apt-get kdm" it's just easier to use Synaptic.

---

