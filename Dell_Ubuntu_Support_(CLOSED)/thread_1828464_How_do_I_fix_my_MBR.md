---
title: "How do I fix my MBR???"
date: 2011-08-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by emilward on 2011-08-19
I upgraded to Ubuntu 11.04 on my Dell D630 laptop. I have Virtual Box and I was relocating the .virtualbox folder to a partition I have on my HD that I use just for storage of pics, music, etc. Anyways, in the middle of the cut/pasting the folder my computer froze and crashed. So I powered down and when I turned it back on I got sent to what looks to be a grub rescue command line. From what I've read online I think my MBR got wiped and I just need to repair it??? I'm in over my head, obviously, and I'm hoping I get back into my OS. Can anyone help me?

---

### Post by An Sanct on 2011-08-19
For the relocation of files, using "move" (ctrl+x -> ctrl+v) never  deletes files until they are 100% moved, so no files can be lost even if  you reset the machine in the meanwhile.

Please be more specific as to where the problem lies. 

-Is the booting problem on your host or guest machine?
-*exactly* what text is displayed when you boot?

---

### Post by emilward on 2011-08-19
Well the problem is on my actual laptop itself. It basically won't load the OS. When I turn it on I see a black screen for about 2 mins and then I get:

error: unknown filesystem.
grub rescue>

And thats it. I don't know what to do from here.

---

### Post by An Sanct on 2011-08-19
okay :) have you got an Installation CD or maybe (far better) an Live USB? ([http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) step 2. of the guide)

If so, then you can run it and select "try without installing" and update grub with ```
sudo update-grub
``` (this fixes the boot sector for Ubuntu/Linux and dual boots)

Well, if you have the Live version, read through the guide here ([The thread where I messed up my booting]("http://ubuntuforums.org/archive/index.php/t-1684051.html") ...)

Edit: In the thread I fixed the stuff I messed up ...

---

### Post by emilward on 2011-08-19
I have the Live CD and USB and it still won't boot. I click to run off the Live disc and it just shows the Ubuntu logo. When I click "esc" it get the command line and it just shows a bunch of errors. Its been running for 2 hours now and its still going. I don't think its gonna boot.

---

### Post by mikewhatever on 2011-08-20
Your MBR? Are you a human hard drive? :p

Anyway, I very much doubt the MBR has anything to do with the problem. Not really sure how you got the idea. If the computer doesn't boot from a CD (that you know is good), it might be a hardware problem. If not, a file system check might help recovering.

---

### Post by emilward on 2011-08-20
Well it took 3 hours but the Live-USB finally loaded up. I was not able to update grub however. I tried "sudo update-grub" and about 45 mins later got the error: 

error: cannot read from '/dev/disk/by-id/ata-SAMSUNG_HM500JJ-S2HCJ1LZ800499'.
/usr/sbin/grub-probe: error: cannot stat 'aufs'.

SAMSUNG_HM500JJ-S2HCJ1LZ800499 is my hard drive, btw. 

Since I am able to boot from the live-USB I am going to try to just delete the partition and reinstall the OS with a clean HD. oh well. Thanks anyways, guys.

---

