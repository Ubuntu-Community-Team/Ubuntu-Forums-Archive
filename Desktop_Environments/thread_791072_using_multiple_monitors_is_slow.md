---
title: "using multiple monitors is slow"
date: 2008-05-11
forum: Desktop Environments
---

### Post by rexxxlo on 2008-05-11
im upgraded to 8.04 a few weeks ago after i got a pair of new hdds to run raid it installed fine 

however when i installed envy and got my 2 identical monitors up and running things  were a little shaky 

vlc will not play a video across both monitors in full screen, it just closes the program 

when i scroll down in any screen the screen will continue to move after i stop scrolling 

some windows weather it be a nautilus window vlc or firefox when they  open the bottom 10% of that windows text video or whatever is all garbled up until i maximize or make a change to that particular window

im using a pci nvidia geforce fx5200 and 2 Westinghouse 20' monitors

---

### Post by rexxxlo on 2008-05-12
anyone else having a problem like this?

also when i watch a movie every 5 seconds or so the video stutters a few frames

---

### Post by jstgtpaid on 2008-05-12
Based on the subject, I thought your issue was the same that I experienced.  I have two identical monitors and was using dual screens.  One of the two monitors was very slow.  I found the following post and the solution worked fantastic for me.

You may want to give it a try to see if it works for you but YMMV.

[http://ubuntuforums.org/showpost.php?p=3426504&postcount=14]("http://ubuntuforums.org/showpost.php?p=3426504&postcount=14")

---

### Post by rexxxlo on 2008-05-15
i have the nvidia x server settings enabled and am using twinview but every time i restart the computer i have to re-enable it and when i do it will not save the file to xorg it gives me an error as follows

unable to create new x config backup file "/etc/X11/xorg.conf.backup'.

---

### Post by Surkow on 2008-05-16
> **rexxxlo said:**
> i have the nvidia x server settings enabled and am using twinview but every time i restart the computer i have to re-enable it and when i do it will not save the file to xorg it gives me an error as follows

unable to create new x config backup file "/etc/X11/xorg.conf.backup'.

You will need to run the program as a super user ("gksudo nvidia-settings").

---

### Post by rexxxlo on 2008-05-17
ok so it saved it but still no video in full screen as soon as  i maximize vlc closes

---

