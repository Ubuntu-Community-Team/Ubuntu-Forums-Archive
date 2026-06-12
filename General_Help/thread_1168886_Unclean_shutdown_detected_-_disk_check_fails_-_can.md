---
title: "Unclean shutdown detected - disk check fails - can't boot. Awesome!"
date: 2009-05-24
forum: General Help
---

### Post by Roasted on 2009-05-24
I was in Vista and rebooted as normal. The system boots up and does a disk check of my one partition. Okay fine, so I let it go. It failed. So I rebooted. Then it proceeds to say, unclean shutdown detected, unable to boot. The automatic file system check failed. It's telling me at a "bash: no job control in this shell" screen that I have to run a manual fsck. Okay fine. But what the hell happened? Why is Ubuntu giving me so much trouble? Every time I boot up I get a new grub error. I've seen error 13, 15, 18, 22. Then I reboot and most of the times it's fine. What the $#(@? How can I get this system running again? And most importantly, what happened in the first place? It's a new hard drive, only a month old.

---

### Post by Super TWiT on 2009-05-24
You could use gparted to check your partition from the livced.  To access it, go into the System, Administration menu and click on gparted.  Once a list of partitions load, right lick on the Linux partition and select check.  Then click apply and confirm your choice.  With any luck this should fix it.  As to why this happened, I am not sure. I have been running this Linux install of mine for months with no problems.

---

### Post by Roasted on 2009-05-24
Didn't work.

I'm still looking at a black screen with white text.

file system check failed
please repair the file system manually. 
A maintenance shell will now be started
CONTROL D will terminate this shell and resume system boot
bash: no job control in this shell.
root@Area51:


What the #$*( happened? This is ridiculous. Control D resumes normal boot but every time I reboot, BAM I have this. I did the fsck with ubuntu livecd as described above to all linux partitions on the drive (root and home) and it said completed and I rebooted.



EDIT - Okay. Now I have a headache. So I have 4 drives in my computer. One main one that dual boots Vista and Ubuntu and the other 3 are for backup purposes (1 for me and 2 for samba). I just connected all of them and booted up and bam, it worked out fine. Whenever I have trouble booting I always disconnect all drives except the main one and troubleshoot my PC from there. Then once it works I'll add the other 3.

I have the drives auto-mounting by their UUID in fstab. Why did I get that weird error as I described before?

---

### Post by Super TWiT on 2009-05-25
This is probably because disk check is performed on every drive.  It always checks to make sure every drive listed in fstab is checked occasionally (unless otherwise stated).  Also, it may not boot if one drive/partition listed isn't detected.  Usually, however, unless it's primary I didn't think this would happen...?

---

### Post by Roasted on 2009-05-25
I took a better look at the error screen. I just noticed the fail under the file system check and didn't look at anything else at first glance. One entry of the screen says it failed to resolve UUID - (insert UUID here) which sounds accurate since I had certain hard drives unplugged.

But I don't understand why my system is erroring out when I boot up without the other drives present. Is this something new with 9.04? I am 100% positive I've done this with 8.10 with no errors upon booting. Since I had 9.04 installed I can't remember any other time I disconnected the drives like I did now, but like I said, with 8.10 I know I did and booted up just fine without them - So I don't see what changed here with 9.04. Maybe the newer kernel?? Anybody know?

Also - I know device ID's aren't a big deal but 2 of my drives switched up the device ID and I can't understand why. Before I liked them being in order cause in system monitor it listed 500, 500, 250, 250, and now it's 500, 250, 500, 250.... ehh. Any way to re-align the device ID's to get them in order just from a personal preference standpoint?

---

### Post by Roasted on 2009-05-28
Bumping this till it gets answered. I had this happen to my Ubuntu machine at work today which has 2 drives in it. I upgraded my spare 80gb drive to a 160gb and it gave me the error since the 80gb drive's UUID wasn't present upon bootup.

Did 9.04 change something with booting while hard drive UUID's aren't present?

---

