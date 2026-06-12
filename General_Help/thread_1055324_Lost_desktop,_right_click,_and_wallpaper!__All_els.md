---
title: "Lost desktop, right click, and wallpaper!  All else works"
date: 2009-01-30
forum: General Help
---

### Post by ellison_northwest on 2009-01-30
Hi all - this is my first post here.  I've gotten a lot of help as a lurker but now I'm in a real mess.

I'm running Intrepid 8.10 on a dual-screen quad-core (dual boot with Vista).  My setup was all running fine until I edited trash_icon_name in Configuration Editor (Alt+F2, run gconf-editor).  I inadvertently changed the value from <no value> to zero, and the precise instant I made this change my desktop went black, all my desktop icons vanished, and right-click on the desktop has no effect at all!  What in the world could I have done by such a small change to an icon name?  The only other things I did was turn on the other items (apps/nautilus/desktop - made the icons visible for computer, trash, volumes, and network).  I've tried rebooting to no avail.  I turned the trash_icon_name value back to 0 - tried other values, tried strings, but cannot return in to <no value> - I don't see that as an option.  Outside of the black desktop, all else works - programs, synaptic, panels, launchers (in panels).  But zero content on the desktop except for the AWN dock launcher, which runs fine.

Help!!!

---

### Post by drs305 on 2009-01-30
> **ellison_northwest said:**
> I turned the trash_icon_name value back to 0 - tried other values, tried strings, but cannot return in to <no value> - I don't see that as an option.  

You can set it back to the default value by right clicking on the trash_icon_name and selecting "Unset Key".

You might also check to make sure the show_desktop option is still enabled.

---

### Post by ellison_northwest on 2009-01-30
Well, it all went south on me now.  I did a reboot and 'repair x-org' option, so now I'm totally busted.  I got my wallpaper back, but no desktop icons, no right-click function, lost my 'visual effects' ("could not be enabled"), and lost my extended dual monitors.  I haven't a clue where to go at this point... guess it's time to boot into Vista :( :( :(  I don't even know where to begin at this point.

---

### Post by drs305 on 2009-01-30
> **ellison_northwest said:**
> Well, it all went south on me now.  I did a reboot and 'repair x-org' option, so now I'm totally busted.  I got my wallpaper back, but no desktop icons, no right-click function, lost my 'visual effects' ("could not be enabled"), and lost my extended dual monitors.  I haven't a clue where to go at this point... guess it's time to boot into Vista :( :( :(  I don't even know where to begin at this point.

Did you update the kernel today? Make sure any hardware drivers you had are still enabled (System, Admin, Hardware Drivers).

---

### Post by ellison_northwest on 2009-01-30
Yes, I updated the Kernel.  I just rebooted back into the older version, and was able to restore my dual monitors and Compiz effects.

But I still don't have ANY desktop items, and right click on the screen does nothing!!!

This is too weird.  Thanks for the help - so far so good.  Now to just get my desktop icons and right click functions back....

Dave

---

### Post by drs305 on 2009-01-30
> **ellison_northwest said:**
> Yes, I updated the Kernel.  I just rebooted back into the older version, and was able to restore my dual monitors and Compiz effects.

But I still don't have ANY desktop items, and right click on the screen does nothing!!!

This is too weird.  Thanks for the help - so far so good.  Now to just get my desktop icons and right click functions back....

Dave

That is exactly what happens when the show_desktop feature is turned off. I imagine you have already checked that in gconf-editor, but running this command will ensure it is set to on.
```

gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop 'true'

```
Perhaps you could run the command with *sudo* as well although that should not be necessary.

Compiz also has a "Show Desktop" setting in it's Desktop section. I use compiz, have my desktop and yet have the compiz setting unchecked. (If I want to have separate wallpapers for each workspace, I either have to use wallpapoz or turn the gconf desktop setting off.)

---

### Post by ellison_northwest on 2009-01-30
SOLVED - (thanks to my 14-year-old son Jeremy who is a Linux geek but lives 2700 miles away - helped me with Remote Desktop!).

Here's what the fix was.  It crashed under the NEW (xxx.11) Kernel upgrade that happened this morning.  I then rebooted into the OLD Kernel (xxx.9).  When I reenabled the ATI hardware drivers under .9, apparently Nautilus refused to recognize any change of state in show_desktop.  I then rebooted back into .11 and after rechecking show_desktop and rebooting, all my icons were back, as was my right click.

So I'm all whole again!

Thanks for all the help....

---

