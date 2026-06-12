---
title: "Editing processes (and changing runlevel that is booted to)"
date: 2009-05-24
forum: General Help
---

### Post by PhoHammer on 2009-05-24
Hi, I was messing around (I know, I shouldn't change things that I don't understand haha) with system processes
 in !# CrunchBang and I saw the graphical login manager option. I said to myself "Hey, I don't need no pretty login" and disabled the option then restarted.

Now when I went back to play some more in these settings, I can no longer "unlock" them. Previously, I could just select the unlock button, but now it's not an active button. What's up with that? I'm logged in as the same user and everything...There's a screenshot below of the window I used to edit the
option.

And on a side note, my non-graphical login romp reminded me of something I tried to figure out how
 to do, but couldn't: I want to boot up to runlevel 3 instead of 5, every time I boot. My train of thought is I can login at 3 and issue the 
"startx" command. And will this have any ill-effects that I haven't thought of (I've heard of people doing it to
make a perceived drop in boot time, which is what I want)?

---

### Post by PhoHammer on 2009-05-24
Now I am getting this error when opening synaptic:

"Failed to run synaptic as user root.

Unable to copy the user's Xauthorization file"

And I can't even upload a png file (another screnshot) to the forums...

Edit: okay i fixed this error by chowning .Xauthority, but I still would like to 
be able to edit the services/daemons section...

---

### Post by balloooza on 2009-05-24
>  I want to boot up to runlevel 3 instead of 5, every time I boot. My train of thought is I can login at 3 and issue the 
"startx" command. 
Clever thought, you have some good knoledge of linux, but unfortunatly, debian (and therfor ubuntu) runs in runlevel 2, what for most distros is multiuser, without networking, is one out of three runlevels ubuntu uses N, 2, and 6 (powerdown)

This is possible, but I do not know how to do it,
BTW, are you using #! on old hardware, or just for speed, I like openbox, and use it os some computers, but Truthfully, if you do not know what some settings are (please take no offense I am not implying that you are a noob **you know about runlevels!)
I recomend the gnome desktop, but not for low end hardware, end to end, it is still verry fast.

---

### Post by PhoHammer on 2009-05-24
> **balloooza said:**
> Clever thought, you have some good knoledge of linux, but unfortunatly, debian (and therfor ubuntu) runs in runlevel 2, what for most distros is multiuser, without networking, is one out of three runlevels ubuntu uses N, 2, and 6 (powerdown)

This is possible, but I do not know how to do it,
BTW, are you using #! on old hardware, or just for speed, I like openbox, and use it os some computers, but Truthfully, if you do not know what some settings are (please take no offense I am not implying that you are a noob **you know about runlevels!)
I recomend the gnome desktop, but not for low end hardware, end to end, it is still verry fast.

Oh, I see. I wasn't aware of ubuntu's runlevel differences. And I do consider myself a 
noob in GNU/Linux land hahaha! I'm using openbox for speed, and I don't like gnome
 so I rather stick with what I have now and just learn. I am just confused about why I cannot edit these options that I had access to before turning off the gdm...

---

### Post by Brandon Williams on 2009-05-24
Some of the authority-related systems will only work correctly if you log in using a session manager (i.e. from a graphical login). Event though you have gdm disabled at startup, you can still launch it. From your console login, run 'sudo invoke-rc.d gdm start' and login. Now you will be able to unlock that dialog and various others that won't work if you use startx.

As noted before, Ubuntu (and all Debian derivatives) use only a limited range of the standard runlevels. In particular, although runlevels 2 through 5 all exist, they are also all identical, and only runlevel 2 is really used. [Here](http://www.marzocca.net/linux/bumdocs.html#order) is a more detailed discussion of the topic.

That page also describes a utility call bum (Boot Up Manager), which many people prefer to the Services capplet that is part of the standard Ubuntu install. If you think you're going to do a lot of tweaking of the runlevels, you might want to switch to bum, because it gives greater control over things.

And finally, although the way you did it works just fine, the typical way to disable graphical logins in a Debian-based system is to empty out /etc/X11/default-display-manager. If that file is empty, then no display manager will be started.

---

### Post by PhoHammer on 2009-05-24
> **Brandon Williams said:**
> Some of the authority-related systems will only work correctly if you log in using a session manager (i.e. from a graphical login). Event though you have gdm disabled at startup, you can still launch it. From your console login, run 'sudo invoke-rc.d gdm start' and login. Now you will be able to unlock that dialog and various others that won't work if you use startx.

Mr. Brandon Williams, the GDM master! Thank you that worked like a charm! I had
installed the BUM, but I need to read up on the options before disabling anymore haha!

---

