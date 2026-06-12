---
title: "Gnome related applications stops responding"
date: 2008-08-16
forum: Desktop Environments
---

### Post by Nimos on 2008-08-16
I've had this problem for a while now. I am using Ubuntu 8.04 with the latest updates.

It sometimes happen that after I have used the computer for a while I become unable to launch new gnome applications like gedit or gnome-terminal. I don't know why, but it might have something to do with GTK since applications like xterm and xmms can still be launched successfully. All GTK related apps just shows up and the instantly stops responding and I have to use Force quit to kill them.

Killing gdm with killall does not help because then gnome hangs after the login screen, but when I killed more processes like pulseaudio, metacity, compiz and others I thought would be GUI related I was able to get it all to work again.

Is this a known problem? I've read in another post that someone had a similar problem due to overheated processor. But I've installed a cpu temperature monitor and it was never above 44 degrees Celsius on my P4 HT.

If it's not a known problem, what can I do to track down the problem?

Is this the right subforum for this issue btw?

Best Regards
Nimos

---

### Post by ajgreeny on 2008-08-16
What graphic card do you have?  If you normally run with compiz enabled try booting with compiz disabled and see if that helps.  Sometimes compiz can freeze applications and do strange things to videos etc..

---

### Post by Nimos on 2008-08-16
Nvidia Geforce 6800XT 128 MB AGP

I'll try a week without Compiz then and see if it helps.

---

### Post by Nimos on 2008-08-16
Disabled Compiz through System->Preferences->Appearance selecting->Visual Effects->None

However I did not reboot the computer. After a few hours I got the same problem again.

This time I did some tests. It should have something to do with GTK I believe. For example OpenOffice, ScummVM, FileZilla, Thunderbird and vlc worked fine. But gedit, gnome-terminal, totem froze when I started them and Firefox refused to produce a window (I have gnome-support installed for Firefox, could be an explanation why it was affected).

I killed of a running Compiz process (one was running although Compiz were disabled), no change.
I then killed 2-3 gnome processes (unfortunately I didn't write them down) and the pulseaudio processes but left gdm untouched.
Then everything started to work again.

---

