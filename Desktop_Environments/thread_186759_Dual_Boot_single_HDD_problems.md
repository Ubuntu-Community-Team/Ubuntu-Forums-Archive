---
title: "Dual Boot single HDD problems"
date: 2006-06-02
forum: Desktop Environments
---

### Post by i++ on 2006-06-02
I have a 160 GB HDD partitioned into 50 GB for windows, and the rest is one linux install (with 1536MB swap), i installed windows first, using the windows setup to partition the 160 into 50 and 110, leaving the 110 unformatted, and installing windows on the 50. I've read in lots of places that this should be done first, as windows overwrites the GRUB with its crappy mbr. now that all went well, so i booted from the 6.06 desktop install cd, and formatted and installed dapper on the 110 gb partition. Now i cannot boot windows, i get the loading screen for a few seconds, then get the bluescreen of death :( the error is "UNMOUNTABLE_BOOT_VOUME". doesnt sound good! however, i can still boot linux. 

Can someone help me as to how to get the setup i want, but being able to boot both :) I can easily reformat the whole hdd if needs be, because it has nothing i need to keep on there, and feel this may be the easiest thing to do...

thanks :) 

i++

---

### Post by edwina on 2006-06-02
Somebody more expert than me will doubtless have some better ideas, but I in the meantime you could ...

1) Check your /boot/grub/menu.lst file and tell us what it has under the Windows section

2) To clarify - you get to the Grub loader, then choose Windows, then it hangs after a few seconds, yes?

3) Maybe try booting with your windows CD and use fixmbr and fixboot in the recovery console (do a bit of research to explain how these work first) - sometimes sorts things out, although I think you might then need to reinstall Grub (never done this myself, just reinstalled Ubuntu when something similar happened, seeing as it only takes a little while). Alternatively, see if the CD can fix the Windows installation automatically with the "recover" option (or whatever it's called).

That's the best I've got, I'm afraid. The way you've gone about things seems reasonable to me. Something to do with Windows needing to be installed on the first partition could be the problem though. I'm sure I've read about that somewhere around these forums and elsewhere.

Good luck!

---

### Post by i++ on 2006-06-02
thanks for the quick reply!
1) boot menu.lst is...
...
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title               Microsoft Windows XP Professional
root               (hd0,0)
savedefault
makeactive
chainloader     +1
...
2) after grub loads i choose Windows XP Professional, and then it shows the windows loading screen for a few seconds, then that dissapears, as if its going to load, then i get the blue screen. it just sits on the blue screen, doesnt reboot or anything.

3) booting from the windows cd, it claims that my hda (160gb) is unformatted, completely, and doesnt show any of the partitions. Though when i boot linux all seems well, 50gb is ntfs, and the rest is my linux install. very odd! 

I think i'll just have to play around, and see what i can get working!

UPDATE -- found this [http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html) -- so am going to give that a shot, and see what happens!

thanks again 

i++

---

