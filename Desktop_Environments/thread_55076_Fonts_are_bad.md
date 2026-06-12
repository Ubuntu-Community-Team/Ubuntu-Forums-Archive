---
title: "Fonts are bad"
date: 2005-08-07
forum: Desktop Environments
---

### Post by ghostryder on 2005-08-07
Hi,

I wanted to edit my fonts because they look so bad. It did it as described in:

[http://www.ubuntuforums.org/showthread.php?t=20976&page=1&pp=10&highlight=helvetica](http://www.ubuntuforums.org/showthread.php?t=20976&page=1&pp=10&highlight=helvetica)

But when I edit my xorg.conf and add 'DisplaySize 440 280' to my MonitorSection the command 

xdpyinfo | grep resolution 

alsways gives me 100x100 dpi. I have also tried DisplaySize 300 150 to see if that has any effect but that doesn't change anything. What's wrong?

g.

---

### Post by Gezzer on 2005-08-07
[QUOTE=][/QUOTE]
 try in a konsole
kdesu kate
when kate is open do your editing & save the changes

you can also try in a konsole
sudo dpkg-reconfigure xserver-xorg
follow the on screen instructions ...

---

### Post by ghostryder on 2005-08-07
Got it to work. The resolution is now 96x96dpi. But the fonts are still ugly. They are not really sharp. I was using Gentoo before and there was no problem with my fonts. What is the problem here, that fonts are ugly?

g.

---

### Post by drizek on 2005-08-07
[QUOTE=ghostryder]Got it to work. The resolution is now 96x96dpi. But the fonts are still ugly. They are not really sharp. I was using Gentoo before and there was no problem with my fonts. What is the problem here, that fonts are ugly?

g.[/QUOTE]
 go to appearence/themes in kcontrol then fonts, then turn off/decrease antialiasing. make sure it is set to greyscale if you have a crt.

also, i would recommend you download the longhorn fonts and use those instead. they are very nice. [http://ubuntuforums.org/showthread.php?t=53281](http://ubuntuforums.org/showthread.php?t=53281)

---

