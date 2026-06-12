---
title: "Lubuntu 11.04 Taskbar color change"
date: 2011-04-29
forum: Desktop Environments
---

### Post by Foxter on 2011-04-29
Hello

I just installed Lubuntu 11.04. However I find the color of the taskbar a bit annoing (the aplication menu sign is almost not visible on blue). The Lubuntu 10.10 default taskbar was gray (more like the classic Win XP version) and the sign was blue and white and cleary more visible. After I checked the panel options it looks like the color is determined by a png type file (lubuntu-background.png). It's possile to get the the 10.10 file version from somewere  and replace the one default for 11.04 ?

Thank you and I apologise for my bad english.

LE: I changed the color of the lubuntu-background.png file but sadly I can't make it look like the attached picture taskbar.

---

### Post by SteveDee on 2011-04-30
> **Foxter said:**
> ... It's possile to get the the 10.10 file version from somewere  and replace the one default for 11.04?...

Put the attached in: /usr/share/lxpanel/images to over-write the 11.04 original

---

### Post by Foxter on 2011-04-30
Thank you **SteveDee**. 

I hope it's not too much of a problem if I ask you for the default 10.10 file from /usr/share/lubuntu/images/lubuntu-logo.png.

---

### Post by N4RPS on 2011-08-26
Having recently installed both Ubuntu and Lubuntu, I've noticed that the desktop in Lubuntu 11.04 runs a lot faster than its Unity counterpart.

In regards to the taskbar, I tried what you suggested, but after rebooting, I still have that unreadable blue taskbar. 

As for myself, I'd like something darker, with, perhaps, white letters if possible...

Also, is it possible to install a different clock, one that doesn't use military time?

Thanks in advance, for all your help. :confused:

73 DE N4RPS

Rob

---

### Post by whatthefunk on 2011-08-26
You can also make your own panel.  Go to a graphics program and create a file the same size as your panel and do what ever you want.  Or of course you can simply change the color in the panel settings window.  My current panel is transparent black.  LXDE is pretty cool....

---

### Post by kerry_s on 2011-08-26
> Also, is it possible to install a different clock, one that doesn't use military time?


just change the settings.

---

### Post by N4RPS on 2011-08-27
It won't let me transfer the file to the affected directory. It must require me to be root to do it. I'll try to log in as root, and try this again before I holler 'uncle'. 

The funny thing is that File Manager did not prompt me for the root password; it just denied the request. Adding sudo to a cp request in a terminal seems to have made no differerence, either. But who knows? Maybe lubuntu locks that directory by default or something.

There's nothing like great help available to get started with.

73 DE N4RPS

Rob

---

### Post by kerry_s on 2011-08-27
> **N4RPS said:**
> It won't let me transfer the file to the affected directory. It must require me to be root to do it. I'll try to log in as root, and try this again before I holler 'uncle'. 

The funny thing is that File Manager did not prompt me for the root password; it just denied the request. Adding sudo to a cp request in a terminal seems to have made no differerence, either. But who knows? Maybe lubuntu locks that directory by default or something.

There's nothing like great help available to get started with.

73 DE N4RPS

Rob

In the file manager under "tools" you can switch to root. Any thing outside the home folder you need to be root. You should not need to, just put it in your pics folder & point to it, same goes if you want to change the lubuntu icon.

---

### Post by N4RPS on 2011-08-29
My thanks to all who answered. You folks have taught me quite a bit in a short time.

It sure is nice to have an OS that runs completely off a 4 GB flash drive with room to spare - especially one that's as easy to install as this one proved to be. 

:popcorn:

73 DE N4RPS
Rob

---

### Post by amjjawad on 2011-09-10
> **N4RPS said:**
> My thanks to all who answered. You folks have taught me quite a bit in a short time.

It sure is nice to have an OS that runs completely off a 4 GB flash drive with room to spare - especially one that's as easy to install as this one proved to be. 

:popcorn:

73 DE N4RPS
Rob

Lubuntu 11.04 is a very good OS indeed and it can be customizable and work the way you want.
It's so simple, easy and work out-of-the box :)

Enjoy and have fun!

---

### Post by Gaygerbil on 2011-09-11
I think you wanted to change the menu color? That can be done by going into appearance and changing the GTK theme. Different themes will have different colors for their menus which the Lubuntu menu will use, just find one you like.

---

### Post by amjjawad on 2012-04-16
> **Lanzaman said:**
> I am posting here because it's the closest thread to my problem so I hope I'm in the right place!

I have Lubuntu 11 on my two computers, an acer one and a custom built desktop.  Both have Cairo-Dock running and although slightly different in detail I am really pleased with both.  However on the acer I have one small problem with the taskbar and it irritates me! 

I want the taskbar panel background to be transparent so in 'Appearance' I have set the colour to solid by putting zeros in the seven boxes on the 'Pick a Colour' panel.  This works but things go slightly wrong in the course of use.  On boot the taskbar starts off transparent but changes to blue when fully booted.  I can however get it back to transparent by changing the wallpaper and it then remains transparent until the next re-boot (It's ok on hibernate) when the whole process repeats itself.  I do not use a built in wallpaper.

Any suggestions welcome.

Hello and Welcome to Ubuntu Forum :)

I'll request to move this post to its own thread :)

---

