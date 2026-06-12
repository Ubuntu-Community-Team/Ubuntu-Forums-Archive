---
title: "Fullscreen problem.."
date: 2005-07-29
forum: Desktop Environments
---

### Post by galo on 2005-07-29
I'm having problems with the fullscreen in applications Vmware and Dosbox.
When I switch to fullscreen mode, it doesn't expand the picture to the entire screen, it stays with the same size, but placed in the center and with the rest of screen black.

Does anyone know how to make it expand ? :)

---

### Post by mcmuffy on 2005-07-29
It sounds like it is displaying the screen as requested but keeping your native desktop resolution (eg : an 800x600 screen would be in the middle of the screen with the rest black as you discribe).
I don't know the software you are using but is there an option to activly change the desctop resolution to match the emulated resolution?

---

### Post by kjempe on 2006-01-25
I have exactly the same problem with DOSBox. Even though I`ve been messing around pretty much with the created dosbox.conf, I`m not able to make DOSBox resize the screen to fullscreen. The pictures stays the same and in the middle of the screen. Ideas anybody?

---

### Post by fallingcow on 2006-04-27
Found the problem:

You'll need a dosbox conf file, and you'll need to have it in the directory from which you run Dosbox (I just keep it in my home folder).

If you don't already have one, just open dosbox and type "config -writeconf" followed by the path and file that you want written (it'll create the file), i.e. "/home/[your user name here]/dosbox.conf".  The man page for Dosbox gives more info on this command if you want it.

Anyway, once you've got the config file, edit it and change "fullfixed=false" to "fullfixed=true".  It's in the first bunch of options near the top of the file.

Reading the description of this option, this seems like the exact *opposite* of the correct setting to make it work right...  but this makes it work, so whatever.

I've only had to do this one one machine, all the others work fine without tweaking.  I don't know what the difference is, but this certainly fixed it.

---

