---
title: "What are they using? Desktop"
date: 2009-08-31
forum: Desktop Environments
---

### Post by ductiletoaster on 2009-08-31
Ok so i came across this them... Mire V2

Here is the gnomelook deal:
[http://www.gnome-look.org/content/show.php/Mire+v2+themepack?content=51023]("http://www.gnome-look.org/content/show.php/Mire+v2+themepack?content=51023")

Here is a picture also gnome look:
[http://www.gnome-look.org/content/preview.php?preview=2&id=51023&file1=51023-1.png&file2=51023-2.jpg&file3=&name=Mire+v2+themepack]("http://www.gnome-look.org/content/preview.php?preview=2&id=51023&file1=51023-1.png&file2=51023-2.jpg&file3=&name=Mire+v2+themepack")

Now i know that the top bar is more than likely conky. What about the panel on the Bottom? Is that just gnome panel or could it be tint2? Also on the left side there is a "window" kinda like start menu how did they get that so simple? Thanks in advanced

One last think would it be better to use emerald them manager or the ubuntu default

---

### Post by mexlinux on 2009-08-31
Thats no gnome, is Xfwm

---

### Post by ductiletoaster on 2009-08-31
Ok well i have never used anything sep gnome or XFCE.... is that availible to ubuntu? How good is it? any limitations? And would i still be able to install programs like gparted (cus i thought those are gnome apps)?

Sorry for all the questions i just am a little new to the whole desktop mang systems

Hold on isnt Xfwm a windo manager? or is it a Desktop manager?

---

### Post by ductiletoaster on 2009-08-31
Anyone? XFWM is a windo manager so im not quite fallowing waht you said....
Enless you meant XFCE not Gnome? because i think XFWM is the window manager for Xubuntu isnt it?

---

### Post by ductiletoaster on 2009-08-31
Hate to reply to my own thread but i think i figure it out! Its XFCE and XFWM windo manager.... so im goin to install Xubuntu because it has XFCE and i think XFWM

---

### Post by blackened on 2009-08-31
From the first link:

> 2nd Preview Screenshot ingredients:
Running fluxbox,
Wallpaper: [http://img54.exs.cx/img54/8420/onreturning.jpg](http://img54.exs.cx/img54/8420/onreturning.jpg)
Gqview
Thunar
gnome-terminal
gmrun
pypanel (patched)
Conky by me (see download link below)

--------------------

Fluxbox and openbox themes are available at box-look.org.

The panel at the bottom is pypanel. The "Startmenu" is the fluxbox right-click menu.

Fluxbox is installable through synaptic and can be installed alongside gnome, XFCE, KDE, or any other desktop environment/window manager. Once installed, you can choose it from the "Session" menu in GDM.

---

### Post by steveneddy on 2009-09-01
> **blackened said:**
> From the first link:



The panel at the bottom is pypanel. The "Startmenu" is the fluxbox right-click menu.

Fluxbox is installable through synaptic and can be installed alongside gnome, XFCE, KDE, or any other desktop environment/window manager. Once installed, you can choose it from the "Session" menu in GDM.

I was just about to post that.

I prefer Fluxbox due to the simplicity and ease of use.

Also the themes are very elegant.

If I wasn't so lazy I would use Flux all the time.

EDIT:

Thanks for the link.

I'm kinda of a theme freak lately and I really like this one.

---

### Post by ductiletoaster on 2009-09-01
Yeah no problem... thank you guys for the info that will help!
I will post back here once i get it all setup

Actually before i get started what about the absence of a gnome or xfce panel..... in all my endevours with theses two i have never been able to remove the panels..... Now i have hear of ways to completely hide gnome panels should i stick with regualr ubuntu and gnome or should i go to something else

---

### Post by baubusiukas on 2009-09-01
I have removed gnome-panel package to completely get rid of gnome panel. Btw, you would lose ALT+F2 "quick run" after that.
But it's no problem if you use gnome-do.

---

### Post by ductiletoaster on 2009-09-01
See i did that once and i lost gnome-do.... fluxbox allows me acces to everything i need like a start menu doesnt it? so would i even need Gnome-Do? See i know there are wasys to just hide completely and permently gnome panels... i just can think of what it was

---

### Post by ductiletoaster on 2009-09-01
Thank god for the internet... did some research and now i think i have an idea of what i want to do! Install Ubuntu, then get fluxbox. That way i can get used to it and still have the ability to select gnome in "sessions". So once agian here i go! ill post back here whith what happens maybe even a screen shot

---

### Post by blackened on 2009-09-01
> **ductiletoaster said:**
> Thank god for the internet... did some research and now i think i have an idea of what i want to do! Install Ubuntu, then get fluxbox. That way i can get used to it and still have the ability to select gnome in "sessions". So once agian here i go! ill post back here whith what happens maybe even a screen shot

Aye, that's what I meant earlier about installing them alongside each other. Good luck.

---

### Post by ductiletoaster on 2009-09-01
So i have read several things about this and im a little lost.... am i starting fluxbox at login through sessions... or am i running fluxbox with gnome and login into gnome? i guess im not to sure how to set up this theme

 O and when im in fluxbox and i open firefox, or any gnome app they have like a standard gnome theme.... so how do i unify the themes

---

### Post by blackened on 2009-09-01
> **ductiletoaster said:**
> So i have read several things about this and im a little lost.... am i starting fluxbox at login through sessions... or am i running fluxbox with gnome and login into gnome? i guess im not to sure how to set up this theme...

The first one.

> ... O and when im in fluxbox and i open firefox, or any gnome app they have like a standard gnome theme.... so how do i unify the themes

```
sudo apt-get install gtk-theme-switch
```

You may have to run it from the commandline if it doesn't appear in your menu.

---

### Post by steveneddy on 2009-09-01
> **ductiletoaster said:**
> Thank god for the internet... did some research and now i think i have an idea of what i want to do! Install Ubuntu, then get fluxbox. That way i can get used to it and still have the ability to select gnome in "sessions". So once agian here i go! ill post back here whith what happens maybe even a screen shot

By golly I think he got it!

Here's the Black theme installed on Gnome Intrepid.

Notice all of the RGBA transparency.

---

### Post by ductiletoaster on 2009-09-01
Well as i kinda anticipated fluxbox takes some getting used to! to say the least. So i opt once again to try something else. I am goin to test it out in virtualbox for a while. so that way i can safely mess with everything i want. Im also goin to try several things out... and like i said earlier was to install in along side gnome. The next is to install ubuntu server edition and then install fluxbox and all the necessary stuff. So ill will continue my quest for the best linux box. Thanks to those that gave me your suggestions.

---

### Post by ductiletoaster on 2009-09-08
For of those of u looking to use fluxbox i personally found it buggy when installed along side gnome. I had exelent results when i installed ubuntu server edition and then installed X server and fluxbox. I havent gotten it to look like the image but im working on it.

---

