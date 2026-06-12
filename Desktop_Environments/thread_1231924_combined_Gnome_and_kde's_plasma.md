---
title: "combined Gnome and kde's plasma"
date: 2009-08-05
forum: Desktop Environments
---

### Post by pmlxuser on 2009-08-05
after hearing a lot of hype about KDEs plasma i wanted to give it a short so i sudo apt-get installed kde-desktop.
Running KDE as a whole was not fun to me but i liked the plasma desktop.

So i decided to switch back to my gnome desktop (which i did) and then just out of crazy thought did ```
 $ plasma 
```

the result was outstanding a plasma in my gnome, next thing I found my self deleting the bottom panel changing icon theme in the palsma to match my gnome icons and I got the attached desktop shot.

i think its not that bad , its like killing two birds with 1 stone only not throwing the stone but the 2 birds hitting the stone.

---

### Post by tacantara on 2009-08-05
I like the KDE look.  Good job on brining KDE and Gnome together.  Do you find it more resource intensive than just running the standard Gnome DE?

---

### Post by pmlxuser on 2009-08-05
apart from the fact that the plasm loads i think five -10 second (emphasize "seconds") later than ubuntu, i have not noticed any differnce in the machine parfomance

---

### Post by windows-killer on 2009-08-05
will this make any changes on my gnome?
does it consume lots of ram?
does plasma start up when you log in to your pc?

---

### Post by GepettoBR on 2009-08-06
> **windows-killer said:**
> will this make any changes on my gnome?
does it consume lots of ram?
does plasma start up when you log in to your pc?

1. No.
2. Define "lots". If your computer is less than two or three years old, then no.
3. If you add it to Startup Applications, it'll run when you log on.

---

### Post by NCLI on 2009-08-06
I just did this... And it's really awesome, after a few modifications :)
[[IMG]http://xs942.xs.to/xs942/09324/screenshot-30821.jpg.xs.jpg[/IMG]]("http://xs942.xs.to/xs942/09324/screenshot-30821.jpg") [[IMG]http://xs942.xs.to/xs942/09324/screenshot-34awesomekdfexgnome327.jpg.xs.jpg[/IMG]]("http://xs942.xs.to/xs942/09324/screenshot-34awesomekdfexgnome327.jpg")

But for your own sake: Please delete the bottom panel first before attempting this. It's hell to remove it without stopping Plasma afterwards.

---

### Post by TheNosh on 2009-08-06
is there a way of installing KDE without all of kubuntu-desktop? i don't need the extra applications.

---

### Post by NCLI on 2009-08-06
Try "sudo apt-get install plasma" and see what happens.

Anyway, is there a way to force any request for Dolphin to open to launch Nautilus instead? Some of the widgets have a bad habit of launching it.

---

### Post by TheNosh on 2009-08-06
> **NCLI said:**
> Try "sudo apt-get install plasma" and see what happens.

it says theres no such package

---

### Post by NCLI on 2009-08-07
Try "aptitude search plasma"

Now if that doesn't list a useful package, I'm out of suggestions.

---

### Post by GepettoBR on 2009-08-07
> **NCLI said:**
> Try "sudo apt-get install plasma" and see what happens.

Anyway, is there a way to force any request for Dolphin to open to launch Nautilus instead? Some of the widgets have a bad habit of launching it.

Try adding an alias to your .bashrc file.

```
alias dolphin='nautilus'
```

If that doesn't work, you can always just replace the dolphin binary with a symlink to nautilus.

> **TheNosh said:**
> it says theres no such package
IIRC there was a metapackage called kde-base that only installed the essential packages for KDE. It's probably still more than you need, but it's smaller than kubuntu-desktop.

---

### Post by longtom on 2009-08-07
Should I try this and don't like it - how could I reverse the step again to get back exactly where I started?

---

### Post by GepettoBR on 2009-08-07
> **longtom said:**
> Should I try this and don't like it - how could I reverse the step again to get back exactly where I started?

You just need to disable Plasma's automatic startup by removing it from the list at System>Preferences>Startup Applications. Then, if you deleted the bottom gnome-panel, you'd have to make another one by right-clicking your top panel, selecting "New Panel" and populate it with the applets you want (like window list, trash bin, etc)

---

### Post by longtom on 2009-08-07
> **GepettoBR said:**
> You just need to disable Plasma's automatic startup by removing it from the list at System>Preferences>Startup Applications. Then, if you deleted the bottom gnome-panel, you'd have to make another one by right-clicking your top panel, selecting "New Panel" and populate it with the applets you want (like window list, trash bin, etc)

Thank you!

---

### Post by GepettoBR on 2009-08-07
> **longtom said:**
> Thank you!

You're welcome. :)

---

### Post by lykwydchykyn on 2009-08-07
> **TheNosh said:**
> is there a way of installing KDE without all of kubuntu-desktop? i don't need the extra applications.

apt-get install kde-core

---

### Post by Ms_Angel_D on 2009-08-07
I can't get this to work, I tried running it in the Alt-f2 window and also cli 

but cli just tells me

```
The program 'plasma' is currently not installed.  You can install it by typing:
sudo apt-get install kdebase-workspace-bin
```

But when I run the command I get this:

```
sudo apt-get install kdebase-workspace-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kdebase-workspace-bin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Running the command at Alt-F2 gives this error:

```
Could not open location 'file:///home/angel/plasma'
Error stating file '/home/angel/plasma': No such file or directory
```

Any Ideas?

Angel

---

### Post by CrusaderAD on 2009-08-07
How do you launch it if it is installed? What's the command?

---

### Post by lykwydchykyn on 2009-08-07
> **Ms_Angel_D said:**
> I can't get this to work, I tried running it in the Alt-f2 window and also cli 

but cli just tells me

```
The program 'plasma' is currently not installed.  You can install it by typing:
sudo apt-get install kdebase-workspace-bin
```

But when I run the command I get this:

```
sudo apt-get install kdebase-workspace-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kdebase-workspace-bin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Running the command at Alt-F2 gives this error:

```
Could not open location 'file:///home/angel/plasma'
Error stating file '/home/angel/plasma': No such file or directory
```

Any Ideas?

Angel

Did you install 4.2 or 4.3?  In 4.3 the command was changed to "plasma-desktop" for reasons I do not know.

In either case, the executable would be in /usr/bin/

---

### Post by solwic on 2009-08-07
This is brilliant.  I love KDE, but Kubuntu is so broken it's nearly crippled, and I miss certain programs that always have issues with KDE (i.e. Gnome-Do, OpenOffice, and Firefox looks like *** in KDE, etc.).

This is the best of both worlds.  I've got a KDE taskbar at the bottom of the screen and a Gnome panel at the top.  

Anybody found any glitches/bugs/issues with this method so far?  Also, would ```
sudo apt-get remove kde-core
``` undo these changes, or would I have to manually remove every package?

Thanks for finding this!  I love it!

EDIT:  Also, I hate those silly KDE programs.  I use ktorrent, but beyond that...don't need koffice, konqueror, kbathroom, kocakola, or any other lame program the KDE devs can stick a k on and make it so sickeningly cute and clever that I can barely stand it....  This method avoids all that.

Anyway.... :)

---

### Post by GepettoBR on 2009-08-08
> **iRun said:**
> This is brilliant.  I love KDE, but Kubuntu is so broken it's nearly crippled, and I miss certain programs that always have issues with KDE (i.e. Gnome-Do, OpenOffice, and Firefox looks like *** in KDE, etc.).

This is the best of both worlds.  I've got a KDE taskbar at the bottom of the screen and a Gnome panel at the top.  

Anybody found any glitches/bugs/issues with this method so far?  Also, would ```
sudo apt-get remove kde-core
``` undo these changes, or would I have to manually remove every package?

Thanks for finding this!  I love it!

EDIT:  Also, I hate those silly KDE programs.  I use ktorrent, but beyond that...don't need koffice, konqueror, kbathroom, kocakola, or any other lame program the KDE devs can stick a k on and make it so sickeningly cute and clever that I can barely stand it....  This method avoids all that.

Anyway.... :)

kde-core is a metapackage so removing it won't really do anything, unfortuately.

---

### Post by Ms_Angel_D on 2009-08-08
> **lykwydchykyn said:**
> Did you install 4.2 or 4.3?  In 4.3 the command was changed to "plasma-desktop" for reasons I do not know.

In either case, the executable would be in /usr/bin/

Awww thanks very much, I was wondering why it wouldn't work for me :D, Now I have the KDE desktop!

---

### Post by NCLI on 2009-08-08
> **gepettobr said:**
> try adding an alias to your .bashrc file.

```
alias dolphin='nautilus'
```if that doesn't work, you can always just replace the dolphin binary with a symlink to nautilus.

:guitar:

---

### Post by lykwydchykyn on 2009-08-08
> **GepettoBR said:**
> kde-core is a metapackage so removing it won't really do anything, unfortuately.

If you use aptitude it should; I thought apt-get kept track of whether things were installed automatically or deliberately?

---

### Post by GepettoBR on 2009-08-09
> **lykwydchykyn said:**
> If you use aptitude it should; I thought apt-get kept track of whether things were installed automatically or deliberately?

It does, but IIRC apt-get autoremove only removes packages on which nothing depends. That won't get rid of KDE, at least not in one iteration. Hopefully, though, I'm completely wrong.

---

### Post by Ms_Angel_D on 2009-12-13
> **GepettoBR said:**
> Try adding an alias to your .bashrc file.

```
alias dolphin='nautilus'
```

If that doesn't work, you can always just replace the dolphin binary with a symlink to nautilus.


IIRC there was a metapackage called kde-base that only installed the essential packages for KDE. It's probably still more than you need, but it's smaller than kubuntu-desktop.

> **NCLI said:**
> :guitar:

Which part of that worked for you?

---

