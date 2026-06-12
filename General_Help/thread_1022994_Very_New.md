---
title: "Very New"
date: 2008-12-27
forum: General Help
---

### Post by unnounn on 2008-12-27
Hello, I just freshly installed Ubuntu and I am having a wonderful time with it, but as for what I've seen, this system has infinite capabilities, and I have absolutely no clue on how to enable/disable them. e.g: I have installed compiz, but therefore it doesn't work, I have enable things such as the 'cube' feature, and yet it doesn't work, I have read tutorials but none of them seem to work, oh yeah, and how and where do I enter codes such as these:
```
\#become root (as you don't currently have permissions to modify your own files)
sudo -i
#go to parent folder
cd /home/tim
#reset ownership & group to yourself
chown -R tim:tim targer-folder
#give yourself the default read-write permissions, set group and other to read only
chmod -R 644 targer-folder
#re-apply excecute permissions on all the directories
find targer-folder -type d -print0 | xargs -0 -II chmod 755 'I'
# don't leave your private keys showing:
chmod 700 .ssh
```

Thanks for your time, and have a nice day.

---

### Post by dragos_iliescu_2005 on 2008-12-27
Code is to be input using terminal:
Applications>Accesories>Terminal

---

### Post by oldos2er on 2008-12-27
Be very careful with the commands chown and chmod, as they have the potential to do a lot of damage. 

 Have you installed the package compizconfig-settings-manager ? It makes modifying compiz-fusion settings easy.

---

### Post by unnounn on 2008-12-27
Also, why doesn't Ubuntu recognise any of my drivers? I click on System > Administration > Hardware Drivers and nothing is there, and how do I install a theme?

---

### Post by unnounn on 2008-12-27
> **oldos2er said:**
> Be very careful with the commands chown and chmod, as they have the potential to do a lot of damage. 

 Have you installed the package compizconfig-settings-manager ? It makes modifying compiz-fusion settings easy.

No, I have no clue on what do with what, I am very new, to install Compiz I went to add/remove, then searched compiz fusion. I installed enabled some things and none of them seem to work, and yes the weird thing is that it doesn't show I have any hardware drivers installed.

---

### Post by kokkus on 2008-12-27
> **unnounn said:**
> Also, why doesn't Ubuntu recognise any of my drivers? I click on System > Administration > Hardware Drivers and nothing is there, and how do I install a theme?
The driver for your gfx card should be listed there.
If not, there isn't any linux drivers for your card, or your card have been blacklisted for security reasons.
You can take the compiz check program to see were the error is and how to solve the problem.
This script will also tell you how you can white list your graphic card if it's whitelisted. But I do not recommand it.
Here's the script btw.
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

Good luck:)

---

### Post by unnounn on 2008-12-27
> **kokkus said:**
> The driver for your gfx card should be listed there.
If not, there isn't any linux drivers for your card, or your card have been blacklisted for security reasons.
You can take the compiz check program to see were the error is and how to solve the problem.
This script will also tell you how you can white list your graphic card if it's whitelisted. But I do not recommand it.
Here's the script btw.
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

Good luck:)

Thanks, here is what I get

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)
 Driver in use:         openchrome
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: openchrome driver in use 

No clue on what it means what so ever.

OT: How do I install a theme such as [http://mariuxv.deviantart.com/art/Hardy-Theme-75628261](http://mariuxv.deviantart.com/art/Hardy-Theme-75628261) ?

---

### Post by kokkus on 2008-12-27
You'll find themese and how to install them guides on gnome-look.org
It's really easy to explain. On your desktop, right-click and click change background or whatever it says, click on themes and drag-and-drop it there, also with cursers, icons and backgrounds you use this method.
GTK 1 is simple 2D coloured themes, GTK 2 is 3D, Metacity themes is  building on GTK +1 or 2 themes with extra effects and stuff.

---

### Post by unnounn on 2008-12-27
> **kokkus said:**
> You'll find themese and how to install them guides on gnome-look.org
It's really easy to explain. On your desktop, right-click and click change background or whatever it says, click on themes and drag-and-drop it there, also with cursers, icons and backgrounds you use this method.
GTK 1 is simple 2D coloured themes, GTK 2 is 3D, Metacity themes is  building on GTK +1 or 2 themes with extra effects and stuff.

Nice thanks it worked, but what about the compiz problem? 

p.s. do you have MSN or AIM? I won't bother you at all, I just have some basic questions...

---

### Post by kokkus on 2008-12-27
Looks like the compiz check worked out fine, so have you enabled the visual effects? if not, click the right mouse on your desktop, and on change background you click on visual effects, then choose normal.

---

### Post by unnounn on 2008-12-27
> **kokkus said:**
> Looks like the compiz check worked out fine, so have you enabled the visual effects? if not, click the right mouse on your desktop, and on change background you click on visual effects, then choose normal.

It says "Desktop effects could not be enabled"

---

### Post by ugm6hr on 2008-12-27
> **unnounn said:**
>  Graphics chip:         VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)

You may be out of luck with Compiz: [http://ubuntuforums.org/showthread.php?t=184512&page=9](http://ubuntuforums.org/showthread.php?t=184512&page=9)

---

### Post by kokkus on 2008-12-27
see if this will help you
[http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875)

---

### Post by unnounn on 2008-12-27
I give up, I'll try to buy a motherboard-compatible nVidia card in 2 weeks, it will run there, besides that, how can I change cursors, install Songbird (I am having problems with that), oh yeah, what is KDE? and how can I install the 'emerald' theme?

---

### Post by ugm6hr on 2008-12-27
I would suggest you start one thread per question, otherwise things get confusing.

But the easy question: [http://www.kde.org/](http://www.kde.org/)

---

### Post by jmszr on 2008-12-27
unnounn,
          For Songbird 1.0 go here: [http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird) . Download the applicable Intrepid Ibex (8.10) file [32-bit or 64-bit]. Double click on the downloaded file and it will install. You can then find it by clicking Applications > Sound & Video > Songbird.

---

### Post by linux_tech on 2008-12-27
> **unnounn said:**
> how can I change cursors, 
 what is KDE? 
and how can I install the 'emerald' theme?

How to install Emerald Theme Manager?
```
sudo aptitude install beryl emerald-themes
```
see here-http://ubuntuforums.org/showthread.php?t=539886&page=4

how can I change cursors
you can try to install gcursors
```
sudo apt-get install gcursor
```
 

what is KDE?
[http://en.wikipedia.org/wiki/KDE](http://en.wikipedia.org/wiki/KDE)

---

### Post by unnounn on 2008-12-28
> **linux_tech said:**
> How to install Emerald Theme Manager?
```
sudo aptitude install beryl emerald-themes
```
see here-http://ubuntuforums.org/showthread.php?t=539886&page=4

how can I change cursors
you can try to install gcursors
```
sudo apt-get install gcursor
```
 

what is KDE?
[http://en.wikipedia.org/wiki/KDE](http://en.wikipedia.org/wiki/KDE)

OK I have Installed both files, now how do I run them, where do I find them?

---

### Post by hyper_ch on 2008-12-28
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by unnounn on 2008-12-28
> **hyper_ch said:**
> It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

Thanks, I'll make sure I'll start doing that, but I though they were simple questions and I might as well pack 'em up in one thread, sorry for the inconvenience.

---

