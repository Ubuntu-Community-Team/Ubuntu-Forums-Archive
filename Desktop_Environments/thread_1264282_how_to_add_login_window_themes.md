---
title: "how to add login window themes"
date: 2009-09-12
forum: Desktop Environments
---

### Post by futureal2032 on 2009-09-12
Hi,

i know we can change the Ubuntu default "login window" theme from

System/Administration/Login Window - Local

and Ubuntu has provided some good login screens...

but there is an "Add" button there which lets you add a new theme..

My questions are:
1. where can i get new themes for Login Window?
2. If possible how can i make my own login window themes?
3. what type of files are used for login window themes (file extention) and where are login window themes installed/stored (location)?

its not a critical issue..but iw ould like to have a different login window.

:o

---

### Post by staf0048 on 2009-09-12
[www.gnome-look.org](www.gnome-look.org)

Lots of GDM themes to browse through.  I've never played with it so I'm not sure on the file formats or making my own, but I don't see why you couldn't use one of the themes from this sight as a template - since it's open source and all . . .

---

### Post by ithinkitschad on 2009-09-12
> **futureal2032 said:**
> Hi,

i know we can change the Ubuntu default "login window" theme from

System/Administration/Login Window - Local

and Ubuntu has provided some good login screens...

but there is an "Add" button there which lets you add a new theme..

My questions are:
1. where can i get new themes for Login Window?
2. If possible how can i make my own login window themes?
3. what type of files are used for login window themes (file extention) and where are login window themes installed/stored (location)?

its not a critical issue..but iw ould like to have a different login window.

:o

[URL="http://www.gnome-look.org/"]
http://www.gnome-look.org/[/URL] :D

---

### Post by futureal2032 on 2009-09-12
> **staf0048 said:**
> [www.gnome-look.org](www.gnome-look.org)

Lots of GDM themes to browse through.  I've never played with it so I'm not sure on the file formats or making my own, but I don't see why you couldn't use one of the themes from this sight as a template - since it's open source and all . . .

Thanks ... i will do that. Any idea whats Ubuntu's default store path for these themes?

---

### Post by akakingess on 2009-09-12
The only other thing that I will mention is that I think that in Ubuntu the "login screen" is referred to as "usplash", so maybe a search for "usplash" might come up with some results, and I know that you can change that screen (as in create your own) without having to change your entire Theme.

---

### Post by staf0048 on 2009-09-12
> The only other thing that I will mention is that I think that in Ubuntu the "login screen" is referred to as "usplash"

The "login" screen, where you put your username and password is known as GDM.  At gnome-look.org click on the GDM themes link to find login screens.

The Usplash screen is what comes up right after grub - you know that screen that has a progress bar and just before the log in screen?

To change your usplash, I'd suggest installing "StartUp-Manager" through synaptic as if you do something wrong it _will_ mess up your system.

> Any idea whats Ubuntu's default store path for these themes?

I've never messed around with it, but I believe they're under:

/usr/share/gdm/themes

---

### Post by futureal2032 on 2009-09-12
> **staf0048 said:**
> The "login" screen, where you put your username and password is known as GDM.  At gnome-look.org click on the GDM themes link to find login screens.

The Usplash screen is what comes up right after grub - you know that screen that has a progress bar and just before the log in screen?

To change your usplash, I'd suggest installing "StartUp-Manager" through synaptic as if you do something wrong it _will_ mess up your system.



I've never messed around with it, but I believe they're under:

/usr/share/gdm/themes

Thanks guys...its all i needed. Apreciate the replies

---

