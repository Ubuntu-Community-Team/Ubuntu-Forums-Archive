---
title: "Ubuntu is booting into my home folder"
date: 2009-04-20
forum: Desktop Environments
---

### Post by Hellstudios on 2009-04-20
> Last night I was using partition magic in my CD drive to make a new NTFS partition to install windows XP, I noticed it was going to take awhile so I left it on over night, the next day i wake up, noticed it was done, so I shut it down. took the CD out, then booted from ubuntu to check my email and such. and Ubuntu booted up fine until it got to the desktop, no taskbar would display and an error came up with something about .services and such (I already took a picture but it won't let me mount my flash drive to upload on my live cd!) so I shut down, reboot in recovery mode, and do 2 things, I first select "try to fix x server" because I heard somewhere where x server has to do with your GPU, I do that, done, then I choose "dpkg" or "attempt to fix packages" or something like that, I do, and it says I have to download one new package, I choose yes, and it says something like "can't reach server" or something... but i can't see it because it goes to fast, so I just reboot hoping "try to fix x server" will do it, it doesn't, the same exact thing happens and the same exact error comes up. and I'm like "WTF? what did that partitioning DO???" so I boot back up to partition magic and delete the partition and resize my ubuntu one to it's original size, reboot, still nada. and it seems to boot into my home folder.... this makes no sense! all I did was make a new partition! 



Any ideas?


That is my original thread, But I believe I posted it in the wrong section...


Ubuntu seems to be booting and showing my /home folder instead of /home/desktop, I click desktop and it just brings a folder up, and no taskbars, bottom OR top, will display.

any help will be welcome, PLEASE!

Thanks, Hellstudios.

---

### Post by Hellstudios on 2009-04-20
Bump,



I just noticed some of the windows have "[][][][][][][]" as theyre title. what does this mean?

---

### Post by Darael on 2009-04-20
This post makes it clearer to me what your problem is: please ignore my response in your original thread.

If your panels aren't opening, and assuming you're in GNOME, I suggest pressing alt+f2 and executing "gnome-panel &" (no quotes).  If you enabled desktop effects, you may (no promises) be able to get a working if less pretty system by executing "metacity --replace" in the run application dialog.

One thing from my other response that does apply is that for the broken package fix you'll need a wired network connection if you're doing it from the recovery console.  Alternatively, if you can get to a terminal in your graphical environment, in which your wireless (if you're using it) should work, you could try running "sudo dpkg --fix-broken".

---

### Post by Hellstudios on 2009-04-20
I am actually direct wired, and only one person replied to my other thread, purhaps your mixing me up with someone else?????

---

### Post by Hellstudios on 2009-04-20
I tried what you said Darael, But all the same things came up when I turned my computer on:

[IMG]http://i207.photobucket.com/albums/bb134/hellstudios/Img00014.jpg[/IMG]



Here is what i typed in when pressing ctrl alt esc, or f1 (i forgot) because pressing alt f2 didn't work.

[IMG]http://i207.photobucket.com/albums/bb134/hellstudios/Img00012.jpg[/IMG]

---

