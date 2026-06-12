---
title: "Gnome Ctrl-Alt-F2 produces blank screen"
date: 2012-10-23
forum: Desktop Environments
---

### Post by burgechris on 2012-10-23
I hope this is the appropriate forum.  This is actually 2 issues in one because the core issue had a work around for me which I was willing to put up with so I'll describe the whole thing.

1)  Ever since 10.04, gnome-sheel will freeze every so often for some reason that I have not been able to determine (happens at different times running different things).  After researching (and having very little time to deal with it), I found that if I pressed Ctrl-Alt-F2 (or some other F series to get me out of gnome) and did a killall -9 on gnome-shell that gnome-shell would autogenerate itself and I'm in happy land again.  I would then presss Ctrl-Alt-F7 and I'm back to programming.  I can deal with this (though annoying) because I don't have to reboot and it takes very little time.

2)  Since upgrading to 10.10, I can no longer do the Ctrl-Alt-F2 because I just get a blank screen (my monitor falls asleep).  I know that it is still there because if I log in (I just don't get the benefit of seeing anything on the screen), do the killall and then Ctrl-Alt-F7 I will get happy gnome again.  The problem is that I don't always type perfectly nor remember if I've already logged in and thus I get stuck in some dialog that I can't read.  I really need to get this at least figured out even if I can't get #1 done.  

In any case, I don't know what steps to take and I really need someone to help me figure out a aolution path.

Here is what I have:

AMD Phenom 9950 (yeah, I know old)

GEForce GTX560 Ti (I'm going to be upgrading my other hardware soon)

Dual monitors - HP 2511x

In additional drivers it says Using NVidia binary Xorg driver, kernel module and VDPAU library from nvidia-current-updates (propietray) - unfortunately I don't know the version nor how to find that

What should I do next before my monitor becomes another statistic in workplace violence.  LOL

---

### Post by Bobhuber on 2012-10-23
> **burgechris said:**
> I hope this is the appropriate forum.  This is actually 2 issues in one because the core issue had a work around for me which I was willing to put up with so I'll describe the whole thing.

1)  Ever since 10.04, gnome-sheel will freeze every so often for some reason that I have not been able to determine (happens at different times running different things).  After researching (and having very little time to deal with it), I found that if I pressed Ctrl-Alt-F2 (or some other F series to get me out of gnome) and did a killall -9 on gnome-shell that gnome-shell would autogenerate itself and I'm in happy land again.  I would then presss Ctrl-Alt-F7 and I'm back to programming.  I can deal with this (though annoying) because I don't have to reboot and it takes very little time.

2)  Since upgrading to 10.10, I can no longer do the Ctrl-Alt-F2 because I just get a blank screen (my monitor falls asleep).  I know that it is still there because if I log in (I just don't get the benefit of seeing anything on the screen), do the killall and then Ctrl-Alt-F7 I will get happy gnome again.  The problem is that I don't always type perfectly nor remember if I've already logged in and thus I get stuck in some dialog that I can't read.  I really need to get this at least figured out even if I can't get #1 done.  

In any case, I don't know what steps to take and I really need someone to help me figure out a aolution path.

Here is what I have:

AMD Phenom 9950 (yeah, I know old)

GEForce GTX560 Ti (I'm going to be upgrading my other hardware soon)

Dual monitors - HP 2511x

In additional drivers it says Using NVidia binary Xorg driver, kernel module and VDPAU library from nvidia-current-updates (propietray) - unfortunately I don't know the version nor how to find that

What should I do next before my monitor becomes another statistic in workplace violence.  LOL
add vga=normal to /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset vga=normal"

---

### Post by burgechris on 2012-10-23
Just tried that, rebooted and now Ctrl-Alt-F2 does not do anything.  :confused:

---

