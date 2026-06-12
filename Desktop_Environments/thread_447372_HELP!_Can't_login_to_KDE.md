---
title: "HELP! Can't login to KDE"
date: 2007-05-17
forum: Desktop Environments
---

### Post by innernaut on 2007-05-17
I have spent about 12 hours searching for a solution to this problem and get nothing but dead ends.  I just installed Kubuntu Feisty.  I upgraded my video card to an Nvidia GeForce 7600 GS, and KDE was running great.  I installed Beryl, and it was working great.  After installing and configuring the majority of the packages I use (they worked) I tweaked environment settings (themes, transparency) etc, in both beryl and in KDE and rebooted.  Now I cannot login to kde under my user account, or any other user account but root.  I have tried reconfiguring x settings in xorg.conf but nothing helps and I have reverted back to my original working configuration.  For a while my .Xauthority permissions were bad, but giving them the appropriate permissions, user, and group do not fix it. The only error I get upon running startx from tty1 is:

waiting for X server to shut down FreeFontPath: FPE "/usr/share/X11/fonts/misc/" refcount is 2, should be 1: fixing.

Any help would be greatly appreciated.  Everything was set up perfectly before I rebooted and I really do not want to reinstall.  Here is some standard info:


cat /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER

I see no errors, which leads me to believe it isn't with my Xorg.conf configuration.

It seems like something with permissions, but I don't know what exactly I don't have permission to...  for example

cat /home/innernaut/.xsession-errors
Xsession: X session started for innernaut at Thu May 17 22:07:22 EDT 2007
open: Permission denied
Xsession: X session started for innernaut at Fri May 18 00:03:53 EDT 2007
open: Permission denied
Xsession: X session started for innernaut at Fri May 18 00:05:34 EDT 2007
open: Permission denied
Xsession: X session started for innernaut at Fri May 18 00:07:06 EDT 2007
open: Permission denied
Xsession: X session started for innernaut at Fri May 18 00:08:12 EDT 2007
open: Permission denied

Any Ideas?

---

### Post by itazuki on 2007-05-31
Holy freakin' cow! I had this same problem today(the refcount error) and I still can't wrap my head around what happened. To make a long story short, a few days ago I created file /home/greg/.xinitrc and in it I typed one line:

xscreensaver &

That's it! and when i deleted this file X started working again! Hope this helps...

---

