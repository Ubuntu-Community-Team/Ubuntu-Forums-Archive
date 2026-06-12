---
title: "Desktop effects can not be enabled"
date: 2007-11-14
forum: Desktop Effects &amp; Customization
---

### Post by bigstoo on 2007-11-14
I have a Dell Latitude C840 with a GeForce 440 Go card. I've finally got it running with the restricted drivers.

If I go to a terminal and run "glxgears" it works fine.

However, if I try to enable desktop effects I get "Desktop Effects could not be enabled".

Could anyone point me to the log file that it written to when starting desktop effects, then I can see how and why it's falling over?

---

### Post by mr_pro_2020 on 2008-02-04
Oh .. I have the exactly same problem with my 

GeoForce4 420 with 32 MB 

But when i treied

> "glxgears" it works fine.


Plz Help??!!

---

### Post by Ub1476 on 2008-02-04
Post the output of

```
lspci | grep VGA

compiz

glxinfo | grep direct
```

---

### Post by SIXAXIS on 2008-02-09
I have the same problem. Here are the outputs.

```

andrew@andrew-laptop:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
andrew@andrew-laptop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
andrew@andrew-laptop:~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```

---

### Post by dboot on 2008-02-09
Same laptop, same problem for me too.

```
nick@utop:~$ glxgears
6995 frames in 5.1 seconds = 1385.095 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
nick@utop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0174 (rev a3) (prog-if 00 [VGA])
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 248, IRQ 11
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1600x1200) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity 

nick@utop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go] (rev a3)
nick@utop:~$ glxinfo | grep direct
direct rendering: Yes

```

Thanks for any suggestions!

---

### Post by angeljr on 2008-02-09
I'm getting the same output as dboot.  I've been chasing this issue for quite a while now and I can't seem to find any resolutions.  I hope to find help here!

---

### Post by dboot on 2008-02-11
Same with me, angeljr. None of the tutorials that explain how to fix this problem seem to be consistent or work. It's been hard enough for me to enable my nvidia driver and "impossible" for me to get compiz/desktop effects to work.

Here's a thread that has someone who says that he was able to get compiz to work with his Dell Latitude C840:

[http://ubuntuforums.org/showthread.php?t=681746]("http://ubuntuforums.org/showthread.php?t=681746")

Hopefully, somewhere, it can be figured out (finally!).

If anyone knows, please share. :)

---

### Post by dboot on 2008-02-11
The problem is suppsedly the LCD monitor that is shipped with the laptop and not the graphics card.

The following post suggests that you add a custom EDID file and point to it in your xorg.conf file:
 
[http://www.nvnews.net/vbulletin/showpost.php?p=1068062&postcount=26]("http://www.nvnews.net/vbulletin/showpost.php?p=1068062&postcount=26")

I downloaded the .raw file and did this with no change. :(

---

### Post by angeljr on 2008-02-11
Same here... tried it without any different results... so if it is the monitor, then I should try hooking up to an external monitor to confirm.  Have you tried that, dboot?

---

### Post by mrmiserable on 2008-02-11
dboot your problem relates to the memory on your graphics card (compiz requires 64meg)

possible solution is to 

gksudo /usr/bin/compiz (line 44 states memory for nvidia change to 32)

now the problem maybe compiz will run 
A really slow
B crash your system
C ok

hope it is c and dont blame me if it all ggoes pear shaped

good luck

---

### Post by angeljr on 2008-02-11
Ok, that worked... but... don't get excited yet....

I have a 1600x1200 screen and it starts malfunctioning at 1280x1024 (entire desktop area goes black, some applications launched will appear completely black).  At 1024x768 it works flawlessly.  So my question is, can anything be done to fine tune Compiz or get some better performance out of it with the amount of memory I have?

I LOVE my 1600x1200 screen, help me!!!

:)

---

### Post by mrmiserable on 2008-02-11
it works great 
as for your I LOVE my 1600x1200 screen, help me!!!

you could try the compiz forum

[http://forum.compiz-fusion.org/showthread.php?t=1762](http://forum.compiz-fusion.org/showthread.php?t=1762)

good luck glad it works if only very poor

---

### Post by angeljr on 2008-02-11
Almost there!  That fixed my black windows problem.  Now the content of the window is not displaying properly.  Any suggestions?

---

### Post by angeljr on 2008-02-11
And by not displaying properly, I mean that it appears frozen or does not draw completely.  The window is most usable when it is as small as possible, the larger the window gets, the worse the problem gets.

---

### Post by mrmiserable on 2008-02-11
im out of ideas 

try using only a few plugins and maybe that could help but ultimately you have an old graphics card with only 32meg of memory and compiz is working at least that a plus 

good luck in your quest

---

### Post by dboot on 2008-02-12
Thanks mrmiserable! Now I have something new to work with.

After enabling desktop effects, my desktop is black and compiz works. Obviously something is still wrong.

---

### Post by mrmiserable on 2008-02-12
try the link i gave earlier

glad it also works for you

---

### Post by angeljr on 2008-02-12
dboot,

After following mrmiserable's link, the next problem you'll probably run into is that the windows will be blank or missing part of the contents.  I've started a thread on the compiz forums in hopes that we can get smoe help.  At the end of the day, mrmiserable has a point that I'm trying to ignore as much as possible and that is that we've got 32 MB video cards.  What I'm confused about is that the crummy Intel on-board cards can do it... why can't the upgraded cards even if they have only 32 MB RAM????

[http://forum.compiz-fusion.org/showthread.php?t=7026](http://forum.compiz-fusion.org/showthread.php?t=7026)

Cheers!

---

### Post by dboot on 2008-02-12
I can confirm the same outcome, angeljr. Right now I'm at 1280x1024 with compiz working. For some reason 1600x1200 will not work (black desktop).

I sorta got it work at 1600x1200 when I ran (using Alt+F2) "compiz --indirect-rendering" like it says in the link that mrmiserable provided. Some windows worked fine, other had black sections, and others didn't respond to my keyboard input.

I'll keep checking on the thread you made on the compiz-forms.

We're making progress!

---

### Post by mrmiserable on 2008-02-12
ok guys found this maybe of some help

[http://openradix.org/archives/317](http://openradix.org/archives/317)

---

### Post by dboot on 2008-02-12
That did it! :KS

I had to edit the new /usr/bin/compiz file to use 32Mb in order to enable desktop effects. After that, there's no black screen with 1600x1200. However, it's obvious that the computer is not having fun (it became unusable when I switched screen resolutions from 1600x1200 to 1280x1024 back to 1600x1200).

I might just suck it up and use 1280x1024.

Thanks again, mrmiserable.

---

### Post by mrmiserable on 2008-02-12
great news please post as sort of solved on this thread it makes it easy to find people in need 

glad it is working

---

### Post by angeljr on 2008-02-14
1280x1024 was pretty painful for me... I may just go on eBay and buy a video card upgrade for the laptop!

> **dboot said:**
> That did it! :KS

I had to edit the new /usr/bin/compiz file to use 32Mb in order to enable desktop effects. After that, there's no black screen with 1600x1200. However, it's obvious that the computer is not having fun (it became unusable when I switched screen resolutions from 1600x1200 to 1280x1024 back to 1600x1200).

I might just suck it up and use 1280x1024.

Thanks again, mrmiserable.

---

