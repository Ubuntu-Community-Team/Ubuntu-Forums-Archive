---
title: "Compiz fusion in 9.04"
date: 2009-06-15
forum: Desktop Environments
---

### Post by mgbowe1 on 2009-06-15
Hi,
can anybody help me? I turned on blur windows in compiz fusion and now all I have is a black screen and the mouse :mad:
Anybody that helps thank you :)

---

### Post by Jekshadow on 2009-06-15
Press Ctrl-Alt-F2. That should show you a shell instead of X Server. Remove Compiz/Beryl/Emerald:
```
sudo apt-get remove compiz compizconfig-settings-manager emerald beryl
sudo apt-get autoremove
```

The autoremove is just to get rid of plugins and similar stuff that is no longer needed.

---

### Post by cmost on 2009-06-15
I'm not sure why you would direct someone to uninstall Beryl in Ubuntu 9.04.  That compositing window manager hasn't existed since Compiz and Beryl merged nearly two years ago to create Compiz-Fusion.  Which is a real shame in my opinion....

---

### Post by izizzle on 2009-06-15
DO NOT UNINSTALL IT. There has got to be a fix which somebody knows of, but do not uninstall. 

BTW, +1 for above post.

---

### Post by mgbowe1 on 2009-06-15
thanks everybody but i think the first response I got will work best because I know how to re-install it.:D

---

### Post by izizzle on 2009-06-16
alright then. Good Luck!

---

### Post by mgbowe1 on 2009-06-16
It didn't work.
compiz fusion is still on the computer for no real reason.
I removed it. :mad:

---

### Post by UbuntuNerd on 2009-06-16
you can always fold back to metacity by typing this command in terminal:
```
metacity --replace
```
which is the ubuntu default window and theme manger, if you want to remove compiz you can try "synaptic package manager" search for compiz and remove any relate files

---

### Post by londonali1010 on 2009-06-16
Argh! The same exact thing happened to me. Evidently you can't use blur with Intel video (sorry, I don't remember where I got that infom and I don't know if that's your video), but the rest of Compiz is fine, so it may not be all of Compiz, just blur.  I use Compiz, complete with transparency, cube, etc, but I just can't use blur :(

Have you managed to fix the black screen problem so that you can at least turn off blur? I ended up booting into the shell and changing the compiz filename to prevent it from loading when my DE started, then went into CCSM and unchecked blur. Then I changed the filename back, rebooted, and all's fine.

HTH.

---

### Post by UbuntuNerd on 2009-06-16
you can also try this command to reset compiz to default:
```
gconftool-2 --recursive-unset /apps/compiz
```

---

### Post by mgbowe1 on 2009-06-16
thanks for the new responses i think i'll try changing the filename. can I get the code for that though because i'm still pretty new to ubuntu and haven't use the shell much.:D

---

### Post by ~sHyLoCk~ on 2009-06-16
> **mgbowe1 said:**
> It didn't work.
compiz fusion is still on the computer for no real reason.
I removed it. :mad:

Can you Alt-F2 and type "gnome-terminal" and then type "ccsm" and deselect blur from there and reboot?

---

### Post by londonali1010 on 2009-06-17
> **mgbowe1 said:**
> thanks for the new responses i think i'll try changing the filename. can I get the code for that though because i'm still pretty new to ubuntu and haven't use the shell much.:D

Well, here's what I did, it worked for me, but as with all things that involve messing around in the root shell, please be cautious, and if you're not sure, don't do it!

1. Restart, and when it says GRUB loading, press <ESC> to enter the boot menu.
2. Select whatever kernel you're currently using, but be sure to select the one that says "(recovery mode)" at the end.
3. When the recovery mode menu comes up, select the option "root (Drop to root shell prompt)".  This will give you a shell prompt, and you will be using root, so be very careful what you do!
4. Type the following:
```
mv /usr/X11R6/bin/compiz /usr/X11R6/bin/compiz1
```
This simply renames the compiz file so that when your DE loads, it can't find that file and doesn't start Compiz.  *NOTE*: prior to doing this, it would be wise to check that that file exists by running:
```
ls /usr/X11R6/bin/ | more
```
And pressing <space> to go down...if the file compiz isn't listed, don't go any further...At any point here if you type "exit" at the command prompt, it will just take you back to the recovery mode menu.
5. Once you have renamed the compiz file, type "exit" to back to the recovery mode menu.
6. Select "resume".  This will continue the normal boot process.
7. When your desktop comes up, you shouldn't have any Compiz effects, and you may not have window decorations, either...That's okay. Go into Compiz Config Settings Manager (via System>Preferences>Compiz Config Settings Manager) and deselect the blur option.
8. Alt-F2 and type "terminal" to bring up a command prompt.  Type:
```
sudo mv /usr/X11R6/bin/compiz1 /usr/X11R6/bin/compiz
```
This renames the compiz file back to its original name.
9. Restart your system.  It should come up as normal, and you should have your effects back, bar (obviously) blur.

I hope this helps.

---

### Post by mgbowe1 on 2009-06-17
> **~sHyLoCk~ said:**
> Can you Alt-F2 and type "gnome-terminal" and then type "ccsm" and deselect blur from there and reboot?
I can't actually I had attempted to uninstall. the files no longer show but the effects still work. I don't know what to do now. I think I need to reinstall ubuntu at this point. p.s. my computer can't boot now because it is a laptop that won't consistently charge due to a bad ac adapter.

---

### Post by londonali1010 on 2009-06-18
> **mgbowe1 said:**
> I can't actually I had attempted to uninstall. the files no longer show but the effects still work. I don't know what to do now. I think I need to reinstall ubuntu at this point. p.s. my computer can't boot now because it is a laptop that won't consistently charge due to a bad ac adapter.

So you uninstalled CCSM? You should still be able to go into System>Preferences>Appearance>Visual Effects and select "No Visual Effects" to turn everything off. Or am I correct in thinking that you can't get your DE up at all?

Maybe someone else knows how you can disable that option via command line?

---

### Post by UbuntuNerd on 2009-06-18
if you want to kill compiz or just turn the effects off just type this command in a terminal:
```
metacity --replace
```

---

### Post by Hetor on 2009-06-18
Or delete your ~/.compiz dir.

---

### Post by n3e on 2009-09-02
> **UbuntuNerd said:**
> you can also try this command to reset compiz to default:
```
gconftool-2 --recursive-unset /apps/compiz
```

This seemed the simplest option to me. Thankfully, it worked just fine after a restart. Rockin'. Thanks!

I'd say that if this happens again, try this first if you're able to, even as you may not be able to see the terminal you're typing in. For one thing, you know that the session is still active and what the cause is, so if you can reset it that's probably the best first option. 
It isn't deleting anything or uninstalling anything, which I'm wary of doing if I'm new at whatever it is I'm doing.

---

### Post by viduthalairr on 2009-10-22
hi all, i had the same problem with blur enabled compiz.. black screen with mouse... after i tried a few of the recommendations, finally renaming the file worked for me... thanks to londonali1010...

---

