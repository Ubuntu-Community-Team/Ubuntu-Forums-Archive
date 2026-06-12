---
title: "Gnome menus sparse"
date: 2004-12-07
forum: Desktop Environments
---

### Post by darren on 2004-12-07
So, I just swapped Gentoo out for Ubuntu and I've been pretty happy with all this so far. But i've run into the first snag - my Gnome menus are messed up. Instead of Applications and Computer I have Applications and Actions like a normal Gnome system. And even the menus I do have are rather sparse - I can't find Desktop Preferences, for example, or Synaptic, or many things I'd find rather useful. Re-adding the 'Menu Bar' applet just copies the same sparse menu bar I already have on the panel.

This all happened after a merry old Synaptic add/remove session, including upgrading to Hoary. I'd be hard pressed to say just what was added or removed in between, but I know I got rid of cups, foomatic, lvm, evms, lots and lots of python junk, and a few other things like that.

Any ideas?

---

### Post by Marauder1 on 2004-12-07
I have read through all the forums that you simply dont mix
Hoary and Warty, since Hoary can have unstable packages.
You should re-install and do only updates to Warty.
Thats what i did and, ok i dont have the latest software but
my system is smooth and clean .

---

### Post by TravisNewman on 2004-12-07
That's not exactly true. If you upgraded everything to Hoary, then you aren't mixing packages. You upgraded to Hoary in the same fashion that everyone had to before there were array cds. If you haven't put a lot of work into this installation, I'd suggest grabbing an array cd and reinstalling. It saves a lot of time.

---

### Post by darren on 2004-12-07
there was a new ubuntu menus package in synaptic when i checked this morning, and I now have all the things available that were missing before. Now it's just that the menu is a bit of a mess but I think thats more a long-term problem being sorted out, I just wanted to be able to get to things without running up a terminal.
Thanks for your suggestions anyway.

---

### Post by Ineluki on 2004-12-07
[QUOTE=darren]... I just wanted to be able to get to things without running up a terminal..[/QUOTE]

You could always hit ALT+F2.

---

### Post by Marauder1 on 2004-12-07
[QUOTE=panickedthumb]That's not exactly true. If you upgraded everything to Hoary, then you aren't mixing packages. .[/QUOTE]

Do you agree that you are subjet to an unstable system panickedthumb !
I dont say not to try any Hoary packages but at least try them one at a time
and not a full upgrade, so you can see if they are without bugs.
Also its easy to go back if it does not work.

---

### Post by TravisNewman on 2004-12-07
I agree that there's a POSSIBILITY of an unstable system, though most don't seem to have that happen. From my previous experience before I completely upgraded to Hoary, it's more unstable to mix packages because of some dependency issues. Say for example you install bumbledoo version 1.2 from Warty that depends on plopidy version 4.7 or higher. Then you install blamblam from Hoary that depends on plopidy version 5.0 or higher. bumbledoo version 1.2 may not have been tested with plopidy higher than 4.9, but Synaptic doesn't know that. Bumbledoo may get broken. That's perhaps a confusing thought, since bumbledoo, plopidy, and blamblam do not exist. But that happened a couple times with me. That's the point of the backports project that's coming up soon.

---

### Post by Marauder1 on 2004-12-07
Do you know if the Synaptic devloppers are working on
a history type command that will enable you to go back
to your original system at any date you want ? (as long 
that you dont apt-get clean).
That would be a fantastic feature that would put linux
even more on the desktop market.
Imagine you install that software with some dependencies
and that you like it, just click one button coresponding
to the time you installed it and your system is back to
what it was.

Just dreaming or it could be done ?

---

### Post by talkingwires on 2004-12-08
This is a [known problem](http://www.ubuntuforums.org/showthread.php?t=7443) with Hoary right now. The Gnome developers are upgrading their menus system, and the Ubuntu developers haven't ported their patches over it it. Give it a couple days, and the menus should be back.

---

### Post by kamstrup on 2004-12-09
Panickedthumb: You shouldn't go about installing packages that don't exist :)

Back to the original problem: Darren, are you sure you cleared all you old Gnome-configuration files after changing to Ubuntu? If you have some remians of ye olde Gentoo Gnome configs lying in you home dir, things will look weird ;P

Try adding a fresh user and see what the menus look like with this login.

Cheers

---

