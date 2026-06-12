---
title: "Big Problem, need help fast!!"
date: 2005-03-30
forum: Desktop Environments
---

### Post by Kimm on 2005-03-30
ok, yesterday I was installing a program on my computer, Kino for video editing. It needed some packages that where not in the apt-get lists. So I made a search for them on the internet (*packagename* +ubuntu) and I found them. I downloaded and installed them. Unfortunently this created some kind of dependency error and well I had to beasicly uninstall everything that had anything to do with GTK to be able to do anything. So... I did that, then I rebooted into the shell and apt-get:ed KDE so that I would have somewhere to move around. This worked. There didnt realy seem to be any trubble with my system at that time so I shut it off and went to bed. Now today when I went to continue fixing it I cant boot, or well, linux boots but it complains about errors in the file system of hda1 and starts trying to fix it, but it allways stops at 33%, when I cancel the process it tells me that I can do it manually somehow, but I have no idea how.

I am currently writing this from a Slax live CD and that works somewhat well, I got the network running so I can transfer my personal files to my dads windows box, but I cant seem to find my linux hdd anymore. If I run cfdisk it can find it, but Slax cant... can anyone help???

---

### Post by Kimm on 2005-03-30
ah, now this was not the right forum... feel free to move...

---

### Post by arctic on 2005-03-30
as you are experiencing some filesystem problems, could you give us a little information on yor harddrive? (name, vendor, partitions installed with used filesystem)

try to let it boot several times and rebuild the filesystem structure. i had this once in fedoracore and a triple reboot to fix the filesystem did the job. it might happen that you need to reboot several times in order to fix the filesystem but only if your harddrive is really plain dead, it won't function (=if there is a fatal error on your magnetic disk).

try to mount the drive as root with slax from a terminal:

mount -t ext3 /dev/hda1 /mnt/     &#8594;(replace ext3 with the filesystem you use on hda1)

are there any error messages when you try to do this? if yes, pleas post the contents.

good luck :)

---

### Post by Kimm on 2005-03-30
well, I got it running anyway, as in, I booted with knoppiox and move all the files in my homre directory to my dads windows computer... then reinstalled everything.
thats what I love about Ubuntu, just reinstall and do some apt-get:ing and your system is just liek it was before, without those apps you never use...

---

