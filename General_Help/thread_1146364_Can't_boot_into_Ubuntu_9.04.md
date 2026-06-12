---
title: "Can't boot into Ubuntu 9.04"
date: 2009-05-02
forum: General Help
---

### Post by kseunder84 on 2009-05-02
So, I was dumb and went to system package manger (I think that's what it's called) and I did ctrl f and searched for cairo. I had previously installed basically everything in there that said cairo, so I couldn't get cairo dock to work so I figured I'd start it over. I removed all installations that had cairo in the description and after it did this my wireless went off, couldn't even get into any network devices. My firefox was gone, then a lot of different programs were gone. So, I booted and it can't boot into a visual desktop now, saysresume  image unavailable and gives me the command line. Is there anyway to fix this? I also have a separate partition of windows xp, is there anyway I can access folders and files on the partition with ubuntu so I can back them up if I have to reinstall ubuntu?

---

### Post by delcypher on 2009-05-02
Sounds like removed something you shouldn't have. To remove it in the first place you should of probably done this in the terminal

```
sudo aptitude remove cairo-dock
``` or removed just cairo-dock from within synaptic. Synaptic should take care of the rest.

Looking through synaptic a lot of other things have the cairo in their title. e.g. Cairo graphics library. I don't know how essential that library is for GNOME to work though.

What happens when you type ```
startx
``` at the command-line?

If you have a working net connection from within the command-line (wireless probably won't work, but a wired connection probably will) you can run ```
sudo aptitude
``` which is a text based package manager which you can use to reinstall the packages you removed. Press ? to get a list of keyboard commands you can use in aptitude.


**Accessing your filesystem from windows**
Assuming you used ext3 as your file system you can use [this driver]("http://www.fs-driver.org/index.html") to access an ext3/2 filesystem from within windows.

Sorry I can't be more helpful

---

### Post by Arrorn on 2009-05-02
i also installed cairo-dock and it also screwed up my computer... though in a different way... it now displayes empty boxes as all the fonts... the recovery command prompt was still in english so i removed cairo-dock but the damage was done and now i cant do anything...

---

### Post by kseunder84 on 2009-05-02
Ok with the start command I get
Exec:5: /usr/bin/x11/x: not found
Giving up

I'm now doing the aptitude

---

### Post by Tipped OuT on 2009-05-02
Hmm..Cairo Dock. This is a lesson to all, use AWN instead :lolflag:.

---

### Post by Arrorn on 2009-05-02
i thought it was cairo...

---

### Post by kseunder84 on 2009-05-02
I did aptitude and updated and installed but still nothing new. I download the driver to get the files but when I open the disk it says the drive has not been formatted do you want to now.

---

### Post by kseunder84 on 2009-05-02
ok so I've got it partially fixed. I ran aptitude and did search for cairo, I have no idea what I deleted, so I marked everything to do with cairo to install, then I did X, and installed almost everything to do with X, after install I rebooted and it is now working except for a few missing programs, I got my wireless to work again and display for monitor ays unknown so everything looks big and not as smooth. Anyone know how to fix this?

---

