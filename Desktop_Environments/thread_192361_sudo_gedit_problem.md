---
title: "sudo gedit problem"
date: 2006-06-08
forum: Desktop Environments
---

### Post by jmcarter on 2006-06-08
Hi,

I am unable to open any file using ```
sudo gedit
```.  Nothing happens, the terminal just hangs.  Can anyone help?

Thanks in advance

---

### Post by aysiu on 2006-06-08
What about this? ```
gksudo gedit
```

---

### Post by jmcarter on 2006-06-08
I forgot to mention already trying this - it goes a little further by opening up a window but then hangs before displaying any of the file contents.

---

### Post by Hanj on 2006-06-08
I had this problem in breezy, [http://ubuntuforums.org/showthread.php?t=80870]("http://ubuntuforums.org/showthread.php?t=80870"),  and it seems some other people had it as well. Still don't know what caused it, and I don't remember what I did to fix it (sorry).

---

### Post by effoff on 2006-06-08
One should never use "sudo" in Ubuntu to open a GUI app. One must use "gksudo" to bring up a graphical sudo login window.

---

### Post by u-blunt-2 on 2007-03-07
I get the same problem, whether I use sudo or gksudo. I should point out the problem only occured after I changes my session theme to one from gnome-art.org

Here is the error message I get after waiting quite some time after pressing enter.:
```
** (gedit:17772): WARNING **: Invalid borders specified for theme pixmap:
        /home/martin/.themes/Cillop-Midnite/gtk-2.0/slider-h.svg,

```

---

