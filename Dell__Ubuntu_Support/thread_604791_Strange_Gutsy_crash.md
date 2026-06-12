---
title: "Strange Gutsy crash"
date: 2007-11-06
forum: Dell  Ubuntu Support
---

### Post by mushroomcloudwarrior on 2007-11-06
I have a Dual-Boot with windows and xp, and i've not been booting into linux for some time (a week or so) because of some touchpad and headphone issues (i've made a thread about here; [http://ubuntuforums.org/showthread.php?p=3622333#post3622333](http://ubuntuforums.org/showthread.php?p=3622333#post3622333))

Right, now i booted into my Linux, and got strange messages ending up with a command line kind or something. Here's a grainy picture i took with my cellphone..although i think you can read most of what's being displayed on the screen. 
[IMG]http://i36.photobucket.com/albums/e37/mushroomcloudwarrior/DSC00101.jpg[/IMG]
[IMG]http://i36.photobucket.com/albums/e37/mushroomcloudwarrior/DSC00102.jpg[/IMG]

Right, i then typed ctrl+alt+del because i though that would reboot it and i would boot into XP, so then it actually went into the KDE log in page, and when i did log in, this is what i got.
[IMG]http://i36.photobucket.com/albums/e37/mushroomcloudwarrior/DSC00104.jpg[/IMG]

I hope someone helps me out, because i'm not liking logging into XP all the time :(

---

### Post by mushroomcloudwarrior on 2007-11-07
Has nobody ever faced anything like this before?

---

### Post by Linicks on 2007-11-07
Looks bad - the hard drive (partitions) seem corrupted from the screen shots you posted.  And if fsck fails to drop back to a linux-single shell  (like it seems to there), it seems pretty terminal.

Nick

---

### Post by mushroomcloudwarrior on 2007-11-07
Do you know what i can do to fix it?

---

### Post by Linicks on 2007-11-07
The short answer is nope.

The long answer is it is possible, but no way can I advise or even guess what route to take without sitting at the computer.

Nick

---

### Post by sprung on 2008-01-12
I had the same problem on an older pc, and while I didn't dig deep enough to find out the reason or fix it, there was a simple workaround:

As odd as it sounds, all i did when this messages showed up was pressing ctrl+alt+del, and seconds later gnome started and everything worked!

EDIT: whoops, sorry i completely missed the last part because of the textonly-view.. but still, maybe the kstartupconfig problem can be easily fixed? i also got gnome config error messeages, but only from time to time, and it only messed up my theme

EDIT2: what i also sometimes had to do in this case was switching to ctrl+alt+f8 and then back to gnome with ctrl+alt+f7 to make gnome work.. but maybe that was another (display?) problem..

---

### Post by natehall on 2008-01-12
Can you run a cd live disk to access the hard drive? If so run sudo fdisk -l (to see how your partitions are set up) and open up /var/log/fsck/checkroot and post the results here.

---

