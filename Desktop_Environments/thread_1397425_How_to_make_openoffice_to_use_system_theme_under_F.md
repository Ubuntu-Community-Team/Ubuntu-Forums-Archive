---
title: "How to make openoffice to use system theme under Fluxbox?"
date: 2010-02-03
forum: Desktop Environments
---

### Post by vickoxy on 2010-02-03
Hi,
i have fluxbox (linuxmint) 9.10 installed. But openoffice does not take default system theme. Is it possible to make fluxbox use default system theme?

---

### Post by m_duck on 2010-02-03
I think you need to set an OOo environment variable so it knows which DE to emulate. In your case, presumably you want it to take on the appearance of your GTK apps. There is a section about it in the [Arch Linux wiki - OOo]("http://wiki.archlinux.org/index.php/OpenOffice#Set_OOo_environment_variable"). From memory, I think I tend to just shove the following in ~/.bashrc or something:
```
export OOO_FORCE_DESKTOP=gnome
```

---

### Post by vickoxy on 2010-02-03
> **m_duck said:**
> I think you need to set an OOo environment variable so it knows which DE to emulate. In your case, presumably you want it to take on the appearance of your GTK apps. There is a section about it in the [Arch Linux wiki - OOo]("http://wiki.archlinux.org/index.php/OpenOffice#Set_OOo_environment_variable"). From memory, I think I tend to just shove the following in ~/.bashrc or something:
```
export OOO_FORCE_DESKTOP=gnome
```

I am newbie here in fluxbox, so i don´t know if i did it right-i added that line in .bashrc, but nothing there. Or should i do something else?

---

### Post by m_duck on 2010-02-03
As long as Ubuntu sources ~/.bashrc on login that *should* work. Have you tried logging out/in and/or rebooting your machine? I remember it being a bit temperamental sometimes.

(I'm working from memory at the moment but will try to test it when I can. I tend to use Openbox rather than Fluxbox, but I think the principle is the same.)

---

### Post by vickoxy on 2010-02-03
> **m_duck said:**
> As long as Ubuntu sources ~/.bashrc on login that *should* work. Have you tried logging out/in and/or rebooting your machine? I remember it being a bit temperamental sometimes.

(I'm working from memory at the moment but will try to test it when I can. I tend to use Openbox rather than Fluxbox, but I think the principle is the same.)

Yes i tried, but nothing-as said-i just added one line in ~/.bashrc-do not know if that is enough.
 I tested also crunchbang-openbox and there was one easy fix for this issue-just needed to add some lines in auto autostart.sh. But this is not working in fluxbox.

I posted same question here:
[http://forums.linuxmint.com/viewtopic.php?f=142&t=41036](http://forums.linuxmint.com/viewtopic.php?f=142&t=41036)

And i tried to implement these solution here, but i just lost my openoffice and needed to reinstall it (i am newbie so i didn´t really know what to put in terminal):
[http://www.rebelzero.com/fixes/openofficeorg-dark-theme-workaround-with-ubuntu-804](http://www.rebelzero.com/fixes/openofficeorg-dark-theme-workaround-with-ubuntu-804)

---

### Post by m_duck on 2010-02-03
Sorry this is taking a while... I'm just trying it out - the Ubuntu/Fluxbox combo seems more difficult to make work than Arch/Openbox!

I tried my suggestions and a few others just to check that it wasn't any residual configurations on your computer that was stopping it working and they didn't work. On mine, Open Office follows my GTK theme if I launch it from the terminal with the following (using the word processor as an example:
```
OOO_FORCE_DESKTOP /usr/bin/soffice -writer
```Is this the same for you?

[B]EDIT:
[/B]Just been fiddling around and seem to have found the solution. It involves the first line I posted. Simply add the following to the bottom of the file, **/etc/openoffice/soffice.sh**
```
OOO_FORCE_DESKTOP=gnome
```After doing so, the whole of /etc/openoffice/soffice.sh looked like the following:
```
# configuration file to set up some environment variables for OOo

# File locking; possible values are:
# - yes:  enable file locking unconditionally
# - no:   disable file locking
# - auto: enable file locking, when the document is found on a nfs share
# If the environment variable SAL_ENABLE_FILE_LOCKING is set,
# the setting if ENABLE_FILE_LOCKING has no effect.

FILE_LOCKING=auto

# OpenGL support; may cause trouble with the restricted nvidia and fglrx
# drivers; possible values are:
# - yes:  enable OpenGL support unconditionally
# - no:   disable OpenGL support.
# - auto: only enable OpenGL support, if not running with the restricted
#   nvidia and fglrx drivers.
# If the environment variable SAL_NOOPENGL is set,
# the setting if OPENGL_SUPPORT has no effect.

OPENGL_SUPPORT=no

OOO_FORCE_DESKTOP=gnome
```

The only thing I changed was the last (OOO_...) line. The rest is all the default contents of that file.

---

### Post by vickoxy on 2010-02-03
So, this is what i get using your method (pict 2, and using help from this forum i get that (pict 1). Although there is difference in this two layouts, they are both not good integrated as gimp or acroread.
[http://forums.linuxmint.com/viewtopic.php?f=142&t=41036](http://forums.linuxmint.com/viewtopic.php?f=142&t=41036)

Can you post some pict of your oo3?
Thanks for help

---

### Post by m_duck on 2010-02-03
Strange. I suppose it must depend partially on the chosen GTK theme. I have only tried it with Ubuntu's clearlooks human theme (I'm using Ubuntu in a virtual machine) and it seems to work fine. As OOo isn't actually a GTK app (as far as I'm aware) it can only attempt to emulate a given theme, so won't always get it right like the GIMP for example. It's similar to Firefox in that respect though from my experience Firefox usually does a better job.

I've attached "before" and "after" screenshots to the bottom of this post for comparison. It does seem to be a bit inconsistent though and keeps reverting to its default style, but I've no idea why.

Additionally, OOo seems to have decided that it will now ignore any modifications to the soffice.sh file I mentioned in the last post, so will only work with the correct theme when launched via the following:
```
OOO_FORCE_DESKTOP=gnome soffice -writer
```

One final idea really is how are you setting your GTK theme? That is the last remaining difference I can think of could be that (except that you are using Mint, and I, Ubuntu as I wasn't paying attention when installing, but underneath they are effectively the same afaik). I am using an application called ***lxappearance*** which is available in the repos. It's just a simple app for setting GTK and icon themes as well as fonts when just using a window manager.

---

### Post by vickoxy on 2010-02-03
I am using the same app. And you have now right:
OOO_FORCE_DESKTOP=gnome soffice -writer gives me nice theme-i think we are close to solution. Now only to make it work always the same way.

---

### Post by vickoxy on 2010-02-03
SUCCESS!!!

i entered in ~/.mint.fm2/submenus/office

```
[exec] (Adobe Reader 9) {acroread } <> #/usr/share/applications/acroread.desktop
[exec] (OpenOffice.org 3.1) {openoffice.org } <> #/usr/share/applications/openoffice.org.desktop
**[exec] (OpenOffice.org Textverarbeitung) {OOO_FORCE_DESKTOP=gnome soffice -writer } <> #/usr/share/applications/oowriter.desktop**
[exec] (OpenOffice.org Präsentation) {ooimpress } <> #/usr/share/applications/ooimpress.desktop
```

Still, i should now figure out what is right input for main openoffice menu where i can choose other apps: ```
[exec] (OpenOffice.org 3.1) {openoffice.org } <> #/usr/share/applications/openoffice.org.desktop
```

Thanks for help! Please post solutions for main menu.

---

### Post by m_duck on 2010-02-03
Do you mean the selection screen for specific office apps - the one where there are buttons for writer, calc etc? If so you could just have a menu entry without the *-writer* part:
```
[exec] (OpenOffice.org 3.1) {OOO_FORCE_DESKTOP=gnome soffice } <>
```Does that work? I'm not entirely familiar with the Fluxbox menu file, but it seems to work for me! For the other apps, just create some new entries and change the bit within the curly braces so ***{OOO_FORCE_DESKTOP=gnome soffice -impress}*** to start OOo impress for example.

---

### Post by vickoxy on 2010-02-03
m_duck, thanks a lot-this is very good solution. Now all applications open with system theme.

:popcorn:

---

### Post by m_duck on 2010-02-03
Goodo, I'm glad I could help :D

---

### Post by iKonaK on 2010-04-18
I did like this:
```
sudo mousepad /usr/bin/oo-gtk
```I put this inside:
> #!/bin/sh
OOO_FORCE_DESKTOP=gnome soffice "$@"Then I made the file executable:
```
sudo chmod 755 /usr/bin/oo-gtk
```And finally I assigned oo-gtk to be default for documents .odt/.doc/etc from my file manager.

EDIT:
My example is for documents already written, so they would open with the gtk theme from the file manager.

---

