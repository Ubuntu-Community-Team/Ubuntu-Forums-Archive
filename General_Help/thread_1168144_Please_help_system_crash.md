---
title: "Please help system crash"
date: 2009-05-23
forum: General Help
---

### Post by BeeDeeGee on 2009-05-23
I upgraded to jaunty and it told me my ATI drivers were not available, later I tried to use them anyway and apparently i messed it all up and now I'M getting funky lines and colors at start up and I cant see anything, guess it my video card. So i went in through recovery mode and I was going to try to downgrade back to intrepid but I dont know the terminal commands to do this, can anyone help???? right now I working off my 8.10 CD

---

### Post by taurus on 2009-05-23
Don't think you can downgrade from jaunty to intrepid without reinstalling the whole thing.

---

### Post by BeeDeeGee on 2009-05-23
is there anyway to do that and save my files.




 or how can I fix the video drivers in the recovery mode

---

### Post by taurus on 2009-05-23
```
dpkg-reconfigure xserver-xorg
```
Or pick the xfix option to reconfigure your X server when you boot into recovery mode from GRUB menu.

---

### Post by BeeDeeGee on 2009-05-23
i'll try that


i already tried the xfix and it didnt work

---

### Post by BeeDeeGee on 2009-05-23
i tried dpkg, it did notwork, I still get flashing colors and lines when I try to boot normally. I had tried to enable to fglrx drivers in jaunty and it must have screwed something up. I really dont want to lose all my files and have to install off the cd again.

---

### Post by taurus on 2009-05-23
Either remove that ATI driver or post your /etc/X11/xorg.conf.

```
cat /etc/X11/xorg.conf
```

---

### Post by BeeDeeGee on 2009-05-23
how do i remove the driver I cant see anything, and I dont know the command to do so in recovery mode

---

### Post by BeeDeeGee on 2009-05-23
is ther anyway i can disable these drivers from the command line and go back to default settings or something???

---

### Post by ALIENDUDE5300 on 2009-05-23
> **BeeDeeGee said:**
> is ther anyway i can disable these drivers from the command line and go back to default settings or something???

This should work... go into recovery mode and choose root or netroot. Then type:
```
sudo apt-get remove fglrx* -y
```

---

### Post by miegiel on 2009-05-23
> **BeeDeeGee said:**
> is ther anyway i can disable these drivers from the command line and go back to default settings or something???

If you installed the driver from ATI's site, there's a pdf with (un)installation instructions on the same page.

---

### Post by BeeDeeGee on 2009-05-23
thanks alot, i will try this

---

### Post by BeeDeeGee on 2009-05-23
> **ALIENDUDE5300 said:**
> This should work... go into recovery mode and choose root or netroot. Then type:
```
sudo apt-get remove fglrx* -y
```


It worked! thanks for the help guys.

---

