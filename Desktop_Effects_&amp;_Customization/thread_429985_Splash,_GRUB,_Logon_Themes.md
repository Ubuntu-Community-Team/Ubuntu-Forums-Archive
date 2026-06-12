---
title: "Splash, GRUB, Logon Themes?"
date: 2007-05-01
forum: Desktop Effects &amp; Customization
---

### Post by Xanderfoxx on 2007-05-01
Is there an easier way to customize Splash, GRUB, and/or Logon screens?
Some kind of Theme Manager that will change those styles and images?



.

---

### Post by DezSP on 2007-05-01
Splash is easy. Just copy over the images in /usr/share/pixmaps/splash/ with whatever you like.

Logon themes are quite easy to install if you find one that you like, I'm not sure what goes into making one of them, but I bet Google has the answers.

I've never heard of GRUB themes though. How exactly, beyond colouring the text, do you apply a theme to something like that?

---

### Post by FuturePilot on 2007-05-01
You can find some Grub splash images on gnomelook.org. There's also some floating around the forums here. All you do is move the splash.xpm.gz (note: it must be titled splash.xpm.gz or else it won't work) to /boot/grub then do ```
sudo update-grub
``` The next time you boot you'll have a background image in the Grub menu.

---

### Post by Xanderfoxx on 2007-05-03
> **DezSP said:**
> How exactly, beyond colouring the text, do you apply a theme to something like that?


Well, I was thinking a simple DOSish setup, but oh, well, this is a noob your talkin' to.
Splash? Ok, thanks.

Really appreciate it. I'm not yet familiar with LInux archetecture in general, so I'm kinda tiptowing around the file systems. In Windows, I usually know exactly what not to touch, and what is free game. LInux, or specifically, Ubuntu, forget it.

Thanks, man!

---

### Post by DezSP on 2007-05-04
/bin, /boot, /dev, /etc, /lib, /proc, /sbin, /sys, /var are probably the ones you want to be wary of. Still, that's what nano and lynx are for. :)

---

### Post by Xanderfoxx on 2007-05-08
Nano? Lynx? Like the names. What, exactly, are they?

Please explain further?

---

### Post by Drooling Iguana on 2007-05-08
Nano is a text editor, Lynx is a web browser. Not sure how they apply to this discussion, though.

---

### Post by Xanderfoxx on 2007-05-26
> **Drooling Iguana said:**
> Nano is a text editor, Lynx is a web browser. Not sure how they apply to this discussion, though.

I'm not familiar with either, but I'm addicted to Firefox. Everything from the name to the features is really well done. But, you're right, it is off-topic.

---

### Post by FuturePilot on 2007-05-26
> **maurin.alex@gmail.com said:**
> 

Really appreciate it. I'm not yet familiar with LInux archetecture in general, so I'm kinda tiptowing around the file systems. In Windows, I usually know exactly what not to touch, and what is free game. LInux, or specifically, Ubuntu, forget it.

Thanks, man!
Linux is pretty safe when it comes to this. Unless you have root privileges you cannot modify anything in the File System. Whereas Windows lets you do whatever you want. For example, if you delete something out of your System32 directory, Windows won't complain.......until the next time you boot.

---

### Post by Xanderfoxx on 2008-01-04
> **DezSP said:**
> /bin, /boot, /dev, /etc, /lib, /proc, /sbin, /sys, /var are probably the ones you want to be wary of. Still, that's what nano and lynx are for. :)

I did not understand at the time, but nonetheless, you advice was helpful.

You deserve my thanks.

Thank you!:lolflag:

---

### Post by Xanderfoxx on 2008-01-04
> **FuturePilot said:**
> You can find some Grub splash images on gnomelook.org. There's also some floating around the forums here. All you do is move the splash.xpm.gz (note: it must be titled splash.xpm.gz or else it won't work) to /boot/grub then do ```
sudo update-grub
``` The next time you boot you'll have a background image in the Grub menu.

Excellent! This was exactly what I was looking for!

Okay!

Thank you! :lolflag:

---

### Post by Xanderfoxx on 2008-05-01
> **FuturePilot said:**
> You can find some Grub splash images on gnomelook.org. There's also some floating around the forums here. All you do is move the splash.xpm.gz (note: it must be titled splash.xpm.gz or else it won't work) to /boot/grub then do ```
sudo update-grub
``` The next time you boot you'll have a background image in the Grub menu.

Awesome. Thanks, man.

---

### Post by Xanderfoxx on 2008-05-01
> **Xanderfoxx said:**
> I'm not familiar with either, but I'm addicted to Firefox. Everything from the name to the features is really well done. But, you're right, it is off-topic.

Actually, I realized that they were indicating the programs used to edit core operating system files safely.

Sorry.

---

