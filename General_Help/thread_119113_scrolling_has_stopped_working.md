---
title: "scrolling has stopped working"
date: 2006-01-18
forum: General Help
---

### Post by Choad on 2006-01-18
i can middle click, but i cant scroll?

where do i set up my mouse? and what should it be set to for a standard 2 button 1 wheel mouse?

---

### Post by linuxden on 2006-01-18
you need to edit your xorg.conf to setup your mouse to be a 5 button mouse, ie the scroll up is button 4 and scroll down is button 5.... you could just 

```
 sudo dpkg-reconfigure xserver-xorg 
``` and that will set it up graphically...

---

### Post by Choad on 2006-01-18
[QUOTE=ubuntulifestyle]you need to edit your xorg.conf to setup your mouse to be a 5 button mouse, ie the scroll up is button 4 and scroll down is button 5.... you could just 

```
 sudo dpkg-reconfigure xserver-xorg 
``` and that will set it up graphically...[/QUOTE]
cheers, that would be what confused me :)

---

### Post by linuxden on 2006-01-18
[QUOTE=Choad]cheers, that would be what confused me :)[/QUOTE]

Hope it works out... Keep us posted...

---

