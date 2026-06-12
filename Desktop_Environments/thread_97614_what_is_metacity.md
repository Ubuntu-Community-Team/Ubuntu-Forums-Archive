---
title: "what is metacity?"
date: 2005-12-01
forum: Desktop Environments
---

### Post by tagg3rx on 2005-12-01
This is a line from my TOP - its using 14% of my RAM
I would like that ram free for me to abuse as i see fit
With a name like metacity i cant help but think "SPYWARE"

6897 helpdesk  15   0 80012  53m 5128 S  1.0 14.3  54:22.37 metacity

What is this and is it safe to sudo killall metacity?

Thanks

---

### Post by EviL_Me on 2005-12-01
metacity is no spyware! it's something from gnome, but I've forgot what it was. But the other's can tell you, I think.




sorry for my bad english, it's not my native language.

---

### Post by frodon on 2005-12-01
Metacity is the default window manager for GNOME, that's why it's running all the time.

---

### Post by magnusbb on 2005-12-01
Metacity is the window manager of GNOME - it's taking control of the windows in your desktop environment. 

If Metacity is using a lot of resources, that is no secrect. To change that, you can use a less memory intensive theme (Clearlooks, Mist or Simple), or, more complex you could change the Window Manager to something like Openbox or Enlightenment. 

If you're new to Linux and GNOME, I would stick to Metacity, though. But, yes, it consumes a lot of memory, and that's a problem with GNOME in general. For the next version, this is supposed to change - so stay tuned.

---

### Post by frodon on 2005-12-01
[QUOTE=magnusbb]For the next version, this is supposed to change.[/QUOTE]I don't think so.

Saying that metacity is "the problem with GNOME" is a point of view.

---

### Post by tagg3rx on 2005-12-01
Ok I switched to mist - that seemed to help a minisqule bit.

I am a noob but getting a little better every day 

If i switch to enlightment can i come back to me current gnome desktop if i cant figure it out or will gnome be lost and i need to start from scratch configuring it?

And what about KDE? or do i need a diffrent distro to use kde?  breezy or wheezy or whatever.

thanks

---

### Post by mostwanted on 2005-12-01
go into the terminal and write

> sudo apt-get install kubuntu-desktop

Then, after you're done with downloading and installing it, log out and select another session type (specifically, KDE), then log in again.

Voila le KDE!

---

### Post by mostwanted on 2005-12-01
[QUOTE=frodon]I don't think so.

Saying that metacity is "the problem with GNOME" is a point of view.[/QUOTE]

Actually, I don't think he meant that they're replacing Metacity in Gnome 2.14. If you read the Gnome developer blogs, you'll notice that the big theme of the next Gnome release is optimising everywhere possible.

---

### Post by dbott67 on 2005-12-01
You can download & install virtually any desktop environment or window manager that you like in Ubuntu (and any other distro, for that matter).  Just open Synaptic and search for KDE, XFCE, fluxbox, IceWM, blackbox, etc.  Download and install whatever packages you want and at the login screen you can select which DE/WM you want to use.  I've tried most of them and find that Gnome is my personal favourite.

Window managers generally do not include a file manager, they only control the way the windows are displayed and customized (which makes them fairly fast & light-weight).  Desktop environments are complete graphical interfaces that include a window manager and file manager and a few other things (which is what makes them a little more resource intensive).

You can change the default window manager in Gnome from Metacity to Enlightenment (and a few others)  --- search the forums here to get the details, someone has written a great howto.

XFCE is the middle-ground between a full-blown desktop environment (like KDE and Gnome) and only a window manager (blackbox/fluxbox, IceWM, etc.) --- not too resource intensive, but a complete DE none-the-less.

Try them all, but keep in mind that some apps are designed using different tool-kits (Gnome apps generally use GTK, while KDE using QT) meaning that some application windows do not match your theme.  The other issue is that all of the default apps that get installed tend to clutter up your menus in the other DE/WMs.

-Dave

---

### Post by magnusbb on 2005-12-01
I'm really fond of GNOME, it works the way I want. And it performs very well on my computer. But that is a fast computer, and I understand that for some, it can be a hog. 

But what exactly is it in Metacity that makes it so slow, compared to other WMs? Is it poorly written?

---

### Post by pek on 2005-12-01
one question, maybe it's a bit ot... is it possibile to have gnome on top of another window-manager?

---

### Post by tagg3rx on 2005-12-01
OK help

I changed my default login to KDE and i dont like it

How do i switch it back to gnome?

I dont see that option in the login setup

Thanks

---

### Post by dbott67 on 2005-12-01
[QUOTE=pek]one question, maybe it's a bit ot... is it possibile to have gnome on top of another window-manager?[/QUOTE]

It is possible to have Gnome use a different WM.  There is a detailed HOWTO in these forums on how to use Enlightenment, and someone else told me they use 'sawfish'.

I tried 'enlightening Gnome' and found that I preferred Metacity. Enlightenment is very customizable --- it allows you to move the window controls around, the title bar can be along the side, as opposed to across the top, etc.  You can certainly make your computer look pretty wild, but in the end, I found that I just prefer a 'standardized' location of things.

-Dave

---

