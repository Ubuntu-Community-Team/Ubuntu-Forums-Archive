---
title: "Xgl and Compiz on Ubuntu Breezy"
date: 2006-03-10
forum: Desktop Environments
---

### Post by Jaimolistico on 2006-03-10
Recently, I followed the instructions for install Xgl and Compiz on my Ubuntu Breezy . When I type in a terminal:

```
sudo ln -sf /usr/X11R6/bin/Xgl /etc/X11/X
```

and then I restart the X server, I have the following error:

The X file is not executable... (or something similar)

I fix this error typing "sudo ln -sf /usr/bin/Xorg /etc/X11/X" but I can't see the incredible effects of this application!!

How can I configure Xgl?? (I have an ATI Radeon X300 using the 8.23.07 version of the proprietary drivers)

---

### Post by ronmarley1 on 2006-03-10
As far as I know, it doesn't work on Breezy.  I might be wrong, though...

---

### Post by Jaimolistico on 2006-03-11
Well... In this [web]("http://guia-ubuntu.org/breezy/personalizar_ubuntu?DokuWiki=987d2851bb6f849b73df81048b6c9026#como_agregar_sombras_efectos_tridimensionales_y_otras_cosas_a_gnome_instalar_xgl") (it is in spanish, so you can translate it to english) they explain how to install Xgl on Ubuntu Breezy. But now I know the meaning of my error, I uninstalled Xgl with the link active. When I have already the Xgl and the link active, the screen turns black. Any ideas??

---

### Post by frodon on 2006-03-11
You will find useful infos in this thread if you didn't read it already : [http://www.ubuntuforums.org/showthread.php?t=133772](http://www.ubuntuforums.org/showthread.php?t=133772)

---

### Post by ronmarley1 on 2006-03-11
[QUOTE=Jaimolistico]Well... In this [web]("http://guia-ubuntu.org/breezy/personalizar_ubuntu?DokuWiki=987d2851bb6f849b73df81048b6c9026#como_agregar_sombras_efectos_tridimensionales_y_otras_cosas_a_gnome_instalar_xgl") (it is in spanish, so you can translate it to english) they explain how to install Xgl on Ubuntu Breezy. But now I know the meaning of my error, I uninstalled Xgl with the link active. When I have already the Xgl and the link active, the screen turns black. Any ideas??[/QUOTE]

Hi Jaimolistico,
I stand corrected.  Sorry, I can't help.  However, now that I know it can work in Breezy, I'm gonna give it a try.  I may come looking for you for advice!
Good luck!

---

### Post by Predius on 2006-03-11
```
sudo chmod a+x /etc/X11/X
``` 

That should fix it.

---

