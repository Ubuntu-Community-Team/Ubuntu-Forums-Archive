---
title: "My home/user file is wiped out!!"
date: 2009-05-05
forum: General Help
---

### Post by joeray on 2009-05-05
Hello, 
I just did a fresh reinstall with ubuntu 9.04 because of xserver problems with my intel 945 chipset. The install went fine with a separate home and separate root partition setup (vista dual-boot).
I saved and pasted my home/user folder into the new installation and all configs were ok. I received the 644 .dmrc nonsense warning and installed nautilus scripts to run nautilus as root to reset the home folder permissions. The next time I logged in the warning message said my home/user folder did not exist. I am writing this using the live cd and have done all that I know to do. My home folder shows empty. I installed with ext4 file config. Can the files be recovered? Are they hiding because of my use of Nautilus scripts? Any help would be appreciated as I can't copy and save my home folder because it is gone. I deleted the previous backup because all went well and I was going to make a fresh one. Any hints would be appreciated.

---

### Post by lloyd_b on 2009-05-05
One possibility - it may be that it simply isn't *mounting* the partition for "/home", in which case all your files are still there, just inaccessible.

Can you post the contents of the file "/etc/fstab" (from the root partition on your hard drive) so we can see whether or not it's even attempting to mount /home?

Lloyd B.

---

### Post by Michael.Godawski on 2009-05-05
If you had previously ext3 on your drive and changed to ext4 than you have probably formatted the drive and the files are gone.

Changing ext3 to ext4 without formatting requires some additional steps during the installation or upgrade process.

[LIST]
[*][http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21](http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21)
[/LIST]

---

### Post by joeray on 2009-05-05
As for formatting the drive, I just followed the steps in gparted and did the installation. As for mounting /home I can with the livecd and it shows the /home/user directory empty. I cannot mount /root-tried changing permissions through chown command line. When I installed, I completely deleted all partitions and created new ones with ext4. How do I establish permissions to /root to post the contents of /etc/fstab?

---

### Post by joeray on 2009-05-05
Ok, guys, here's the gist of it. You were trying to help an idiot. After the new installation I was confused and was trying to find my /home/user directory on the /root partition. No good, of course it is on thE /home partition. Lloyd_B you were right, it wasn't being mounted. Somehow, I'm not sure how, I mounted it and I'm in to my new installation. Though, I still get that annoying message concerning 644 and .dmrc about permissions to the home folder. That I should be able to figure out with the great help available in the forums here. Thanks for your quick replies and I hope I can be of help to someone in the future, Joeray saying FREEDOM ISN'T FREE.

---

