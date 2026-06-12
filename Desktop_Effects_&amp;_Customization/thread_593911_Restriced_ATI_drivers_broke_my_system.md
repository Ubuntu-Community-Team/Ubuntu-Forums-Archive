---
title: "Restriced ATI drivers broke my system"
date: 2007-10-27
forum: Desktop Effects &amp; Customization
---

### Post by Yes on 2007-10-27
I enabled the restricted drivers for ATI cards, and now when I start GDm all I get is a black screen.  I can boot into a command line, but I don't know how to fix it from there.  Is it possible?

Thanks.

---

### Post by jimrz on 2007-10-27
> **Yes said:**
> I enabled the restricted drivers for ATI cards, and now when I start GDm all I get is a black screen.  I can boot into a command line, but I don't know how to fix it from there.  Is it possible?

Thanks.

yes.

did you backup your xorg.conf before enabling the restricted drivers? 

if so, from the command line prompt type (if you do not show as "root" you will need "sudo")
```
cp <path to your backup conf file> /etc/X11/xorg.conf
```
then shutdown
```
shutdown -P now
```
and when you restart you will be back to your previous xorg and driver.

if you did not manually backup xorg.conf I believe, though am not certain, that restricted manager makes one. so type
```
ls /etc/X11
```
look for an extra xorg.conf file with probably a bunch of numbers appended (maybe like a dtae/time thing) to the end of the name and if you find one do the same as above except use that file to copy the backup from
```
cp /etc/X11/<name of new file you found> /etc/X11/xorg .conf
```

---

### Post by Crafty Kisses on 2007-10-27
Try the following command:
```
sudo dpkg-reconfigure xserver-xorg
```

This will pop up a text-based graphical "wizard" that will ask you questions about your keyboard, your mouse, your graphics card, and your monitor. Answer the questions as best you can. If you don't know the answer to a question, just go with the default and press Enter. 

When you're done, press Cntrl+ Alt+F7 to get back to graphical mode and then Cntrl+Alt+7 Backspace to reset the X server (so your changes can take effect).

---

### Post by Maestro23 on 2007-10-27
> **Codename said:**
> Try the following command:
```
sudo dpkg-reconfigure xserver-xorg
```

This will pop up a text-based graphical "wizard" that will ask you questions about your keyboard, your mouse, your graphics card, and your monitor. Answer the questions as best you can. If you don't know the answer to a question, just go with the default and press Enter. 

When you're done, press Cntrl+ Alt+F7 to get back to graphical mode and then Cntrl+Alt+7 Backspace to reset the X server (so your changes can take effect).

Make sure to pick your desired resolutions as well.

---

### Post by Crafty Kisses on 2007-10-27
> **Maestro23 said:**
> Make sure to pick your desired resolutions as well.

Yep. :)

---

### Post by Yes on 2007-10-27
Great, it worked.  Thanks.

---

### Post by jtesolin on 2007-10-29
I had the problem to and I will try the above to fix it. However, do you need ATI  restricted driver for compiz desktop effects?

---

### Post by kshane on 2007-10-29
> **jtesolin said:**
> I had the problem to and I will try the above to fix it. However, do you need ATI  restricted driver for compiz desktop effects?

No.  But, in *my experience*, it works better than using XGL.  I have an ATI X1650 and it does not handle desktop effects well without the restricted driver.  It involves a little tweaking, but the restricted driver does well on *my box*.  I was trying for about 5 months to get it going and had no real success until the new restricted driver was released.

Kevin

---

