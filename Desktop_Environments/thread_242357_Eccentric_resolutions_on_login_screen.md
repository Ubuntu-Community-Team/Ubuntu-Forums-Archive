---
title: "Eccentric resolutions on login screen"
date: 2006-08-23
forum: Desktop Environments
---

### Post by mycelo on 2006-08-23
I am getting all kind of wacky resolutions on the login screen (the brownish one that asks for the username in the center). 

When I boot, I get something like 640x480 but it scrolls when I move the mouse to the bottom, so I can see the menu to change sessions.

If I logout from Gnome, the login screen goes to an even worse resolution, something line 320x200 with a huge pixelated mouse cursor and I can see only what would be the corner of the screen. In this "mode" I can't scroll the screen anymore and I can't even see the login box.

Inside Gnome I have several resolutions and refresh rates to choose, and all seem to work fine. But that won't change the login resolution.

So, how can I change the default resolution of this screen?

mycelo

---

### Post by steefjeqv on 2006-08-31
Hello,

I'm quite new here and just started learning to use Ubuntu.

Anyway, maybe this thread can help you.

Greetings,
Steven



[www.ubuntuforums.org/showthread.php?t=240259&highlight=resolution+login](www.ubuntuforums.org/showthread.php?t=240259&highlight=resolution+login)

---

### Post by hraposo on 2006-08-31
go to terminal and execute

sudo dpkg-reconfigure xserver-xorg

you can choose the resolutions
then go to 
system and change the resolution

---

### Post by mycelo on 2006-08-31
Hi,

Thank you guys. I tried to reconfigure the xorg, but it asked for a lot of things that I couldn't answer. Then I restored a very old backup of my xorg.conf, which fixed my login screen.

However, I lost some resolutions/refresh-rates. I did a lot of research about this file, understood most of its structure and managed to insert all of my desired resolutions.

Even though my login screen is ok now, I still didn't find where exactly I can change its very resolution, since it seems independent of the gnome/kde settings. :confused::confused::confused: 

mycelo

---

### Post by steefjeqv on 2006-09-02
Hi Mycelo,

Did you check out the link in my previous post ?
This solution worked fine for me and I now have a full screen upon login.
Basically, you have to remove all the resolution modes that you don't use in your xorg.conf file (under the section screen). 

Hope you have a full screen login soon !

Greetings,
Steven

---

### Post by willz06jw on 2006-09-02
I wonder why we can't change this display information in a menu somewhere.  This seems like something that would screw up a Linux first-timer

---

### Post by SpikeyMike on 2006-09-03
> **hraposo said:**
> go to terminal and execute

sudo dpkg-reconfigure xserver-xorg

you can choose the resolutions
then go to 
system and change the resolution


Hi 

I ran sudo dpkg-reconfigure xserver-org which started a dialogue where I had to select the video card I am using and other questions which I didn't really understand, later on it started asking me questions about my keyboard, I quit this and now the colours look strange, how can I change whatever I have done to restore it?

Thanks in advance

Mikey

---

### Post by SpikeyMike on 2006-09-03
help, i'm not sure whats happened but the colours even look strange when I boot windows, it looks like it did something to my video card :( :(

---

### Post by mycelo on 2006-09-04
> **steefjeqv said:**
> 
Did you check out the link in my previous post ?
This solution worked fine for me and I now have a full screen upon login.
Basically, you have to remove all the resolution modes that you don't use in your xorg.conf file (under the section screen). 


Thank you a lot Steven, my login screen is fixed now (after recovering an old *xorg.conf* backup and some tweaking). I was wondering how can I change the resolution of that screen (directly and independently), but it doesn't seem possible.

GDM developers should take a look at this.

mycelo

---

