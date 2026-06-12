---
title: "Best DE for a 500MHz/128MB RAM computer + usability?"
date: 2007-01-12
forum: Desktop Environments
---

### Post by userundefine on 2007-01-12
Greetings all,

I'm wondering what people think would be the best DE/WM for a desktop with 500MHz and 128MB of RAM.  Fluxbox, XFCE, IceWM?  The twist here is that the computer will be going to an older woman and her family who have a non-working Win98 and have not experienced Linux before.  However, her needs on a computer are basic and simple, and Linux will be perfect for her.  So, from a user-friendly standpoint and keeping in mind the specs, what do you think will be best?  I'll be setting up everything so there would be little question of her needing to "tweak" something.

Thanks !

---

### Post by jem7v on 2007-01-12
Personally, I would recommend XFCE.  I've used both it and Fluxbox and I really prefer the luxury of not having to make your own menus and the likes.  Sure, Fluxbox is NIFTY and I like its minimalism, but I'm also a sucker for being able to find the program or settings manager I want with ease.

It will probably run fine on those system specs, but you won't be able to INSTALL from the LiveCD with only 128 megs ram - you'd need either need 192 to install it from the LiveCD, or you could just use the Alternate Install disk.  (You can Run the LiveCD with only 128MB, but you can't install from it.)

---

### Post by RedSquirrel on 2007-01-16
I would go with Fluxbox. From everything I've read on these forums, XFCE is more of a "middle weight" window manager, whereas Fluxbox is really light weight and perfect for older systems. I have it on a 600 MHz PC and it works very well.

It's also fairly user-friendly once you setup the menu (which is not hard).

There's a lot of customization you can do, but other than the menu setup, everything works fine when you install it.

---

### Post by userundefine on 2007-01-17
Hmm.  I tried Openbox on my laptop since I'd never tried it, and it's probably too minimalist for the person I'm installing it for.  However, it may very well be nice for me. :)  I'll check out Fluxbox too.  The computer belongs to a Grandma that I'm setting it up for, so that's why user-friendliness is important.

---

### Post by happy-and-lost on 2007-01-17
I like Openbox, as you can just plug all your favourite bits from all the DEs into it. 

OB + Pypanel + feh + Thunar + a bit of work compiling it and configing it = Yummy :)

---

### Post by Lord Illidan on 2007-01-17
I wouldn't use any Ubuntu on that box. Why not try Zenwalk Linux? Ubuntu is still a bit bloated, and Xubuntu is getting fatter.

---

### Post by andrew.46 on 2007-01-17
Hi,

 Can I cordially differ from your post:

> **jem7v said:**
> Personally, I would recommend XFCE.  

It will probably run fine on those system specs, but you won't be able to INSTALL from the LiveCD with only 128 megs ram - you'd need either need 192 to install it from the LiveCD, or you could just use the Alternate Install disk.  (You can Run the LiveCD with only 128MB, but you can't install from it.)

 I quite successfully installed Xubuntu 6.06 from the LiveCD just a month ago on a 128MB system. I do note however that you are certainly quoting the official specs:

[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

 Perhaps I was lucky :-)

           Andrew

---

### Post by Tazix on 2007-01-17
I run Xubuntu Dapper (6.06) on my celeron 500 laptop with 128MB and it runs fine.  Haven't tried installing Edgy (6.10) on it yet, though.

Desktop Environment isn't the only thing to trim the fat on.

Running TinyX or KDrive with the Xvesa driver, instead of Xorg will take less RAM and speed things up too.

Unfortunately, I don't have a link to a "How-to" on replacing Xorg with TinyX.

---

### Post by RedSquirrel on 2007-01-17
> **userundefine said:**
> Hmm.  I tried Openbox on my laptop since I'd never tried it, and it's probably too minimalist for the person I'm installing it for.  However, it may very well be nice for me. :)  I'll check out Fluxbox too.  The computer belongs to a Grandma that I'm setting it up for, so that's why user-friendliness is important.


In my opinion, Fluxbox is quite user-friendly once you setup the menu.

For a windoze user, getting used to Fluxbox shouldn't be too hard. Instead of clicking 'Start', you just right-click anywhere on the desktop and voila, there's your menu with all of your favorite apps.

Fluxbox can be made even more user-friendly by adding all sorts of eye candy:

- fbpanel (gives you a more "GNOME-like" toolbar to replace the standard Fluxbox one)
- dockapps in "the slit"
- rox file manager can be used to manage the look & feel of the desktop

... and so on.

I won't get into the gory details of these things, but here are some Fluxbox links for you:

Fluxbox 
[http://fluxbox.sourceforge.net/](http://fluxbox.sourceforge.net/)

Fluxbox Wiki
[http://fluxbox-wiki.org/](http://fluxbox-wiki.org/)

Fluxbuntu (their community page has some neat ideas)
[http://community.fluxbuntu.org/](http://community.fluxbuntu.org/)

Here is a link to a HOWTO for using rox:

[http://community.fluxbuntu.org/index.php?topic=78.0](http://community.fluxbuntu.org/index.php?topic=78.0)

(haven't tried rox yet myself... one of these days...)

---

### Post by igknighted on 2007-01-17
> **userundefine said:**
> Greetings all,

I'm wondering what people think would be the best DE/WM for a desktop with 500MHz and 128MB of RAM.  Fluxbox, XFCE, IceWM?  The twist here is that the computer will be going to an older woman and her family who have a non-working Win98 and have not experienced Linux before.  However, her needs on a computer are basic and simple, and Linux will be perfect for her.  So, from a user-friendly standpoint and keeping in mind the specs, what do you think will be best?  I'll be setting up everything so there would be little question of her needing to "tweak" something.

Thanks !

I have a laptop with these specs and I use KDE.  If you use all KDE native apps it will perform better than Xfce even (once you turn down some of the fancy GUI effects like fading menus, etc.).  Plus, KDE looks better and is easier to use than its more barren counterparts.

---

### Post by aysiu on 2007-01-17
If she wants performance and doesn't need to change the wallpaper, then I'd go with IceWM or Fluxbox.

---

### Post by RedSquirrel on 2007-01-17
> **aysiu said:**
> If she wants performance and doesn't need to change the wallpaper, then I'd go with IceWM or Fluxbox.


Changing the wallpaper is straighforward in Fluxbox:

In ~/.fluxbox/init, find the line that has:

```

session.screen0.rootCommand: 

```and change it to:

```

session.screen0.rootCommand:    fbsetbg -l

```Then put this in the ~/.fluxbox/menu:

```

[wallpapers] (/path/to/background/images)

```Another option is to put the command to change the background (fbsetbg) in the menu file. An example is here:

[http://fluxbox.sourceforge.net/docbook/en/html/x750.html](http://fluxbox.sourceforge.net/docbook/en/html/x750.html)


In either case, the result is a menu item that lists all of the wallpapers found in '/path/to/background/images'.

---

### Post by viper on 2007-01-17
Maybe Damn Small Linux or even Puppy Linux....
[http://www.frozentech.com/content/livecd.php](http://www.frozentech.com/content/livecd.php)
Try this link out, might give you a few more alternatives...

---

### Post by aysiu on 2007-01-17
For the record, Damn Small uses Fluxbox, and Puppy uses IceWM.

---

### Post by viper on 2007-01-18
> **aysiu said:**
> For the record, Damn Small uses Fluxbox, and Puppy uses IceWM.

Probably should have mentioned that, thanks aysiu.......

---

### Post by Littleweseth on 2007-01-18
I have a Celeron 566 desktop that runs Openbox with gnome-panel for convenience, It's very fast and snappy, though gnome-panel is a bit of a memory hog - but gnome-panel is the easiest way for a non-computer using person to find their programs, et al. I'd also suggest Abiword, Gnumeric, etc. instead of Openoffice (using OOo tends to be painful on slow hardware.)

For reference, I installed the base system from the Dapper Server CD (I think they call the the 'alternate install' CD nowadays), then did something like 'aptitude install x-window-system-core openbox gnome-panel synaptic'. That's enough to get you up and running in a graphical environment, and from there I used synaptic to add everything else I wanted. The resulting system has exactly what prgrams you want, nothing more and nothing less - though i'm not sure how suitable it'd be for a laptop (ACPI power management, etc.)

There's a wiki page about low memory systems, which makes good reading;
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

EDIT : and this page too;
[https://help.ubuntu.com/community/LowEndSystemSupport](https://help.ubuntu.com/community/LowEndSystemSupport)

Hope this helps :)
-lws

---

