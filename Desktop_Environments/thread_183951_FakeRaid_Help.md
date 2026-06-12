---
title: "FakeRaid Help"
date: 2006-05-29
forum: Desktop Environments
---

### Post by moffa on 2006-05-29
Hi,

I followed the [FakeRaidWiki]("https://wiki.ubuntu.com/FakeRaidHowto") except for the step with * base-config new * because the package no longer exists.  I used a LIve-cd - test flight 6.

My problem is that I can not boot properly because I keep getting *Error 15 - File not Found* when selecting the first item on the grub menu.
I **can** however boot using recovery mode and memtest.

My grub file is attached - I added a txt extension so I could upload it.  I would not be surprised if there is a typo in there causing all the problems.

My partitions are setup as:
boot - /dev/mapper/sil_agafdjccbcfe2
root - /dev/mapper/sil_agafdjccbcfe4
swap - /dev/mapper/sil_agafdjccbcfe3

Another issue is that my /etc/fstab file is empty.  I am not sure if that has anything to do with it.

I appreciate any help you may provide.

---

### Post by JoWilly on 2006-05-30
Sorry, I can't help you here. But why do you want to strugle with fake raid, it can be a real pain, sometimes works with some ditributions, sometimes not... ?

Linux software raid is much better (always works, more features with all raid modes, better support and flexibility,many benchmarks show better performance,...); I've been using it for years.

Linux is much better at doing what a fakeraid does.

---

### Post by psusi on 2006-05-30
[QUOTE=moffa]Hi,

I followed the [FakeRaidWiki]("https://wiki.ubuntu.com/FakeRaidHowto") except for the step with * base-config new * because the package no longer exists.  I used a LIve-cd - test flight 6.

My problem is that I can not boot properly because I keep getting *Error 15 - File not Found* when selecting the first item on the grub menu.
I **can** however boot using recovery mode and memtest.

My grub file is attached - I added a txt extension so I could upload it.  I would not be surprised if there is a typo in there causing all the problems.

My partitions are setup as:
boot - /dev/mapper/sil_agafdjccbcfe2
root - /dev/mapper/sil_agafdjccbcfe4
swap - /dev/mapper/sil_agafdjccbcfe3

Another issue is that my /etc/fstab file is empty.  I am not sure if that has anything to do with it.

I appreciate any help you may provide.[/QUOTE]

I'm confused because you say you can boot using the recovery option.  Neither option should work or both should work since they are the same, excepting the splash and single options.  

What file does it say is missing?  And yes, you will need to populate your /etc/fstab.

---

### Post by moffa on 2006-05-30
The reason why I do not want to use the linux software raid is because I have a Windows raid on it already.

I populated my fstab but I'm still not getting any luck.

It seems to recognize the files, but does not say what file can not be found.

I believe it has to do with the /dev/mapper/ path.  Is there a way to confirm that grub can actually see the /dev/mapper/ raid (from dmraid)?

When I select the ubuntu kernel the grub screen outputs:

root (hd0,1)
  Filesystem type is ext2fs, partition type ....
kernel		/vmlinuz-2.6.15-23-686 root=/dev/mapper/sil_agafdjccbcfe4 ro quiet splash
  [Linux-bzImage setup=0x... some numbers]
initrd		/initrd.img-2.6.15-23-686
  [Linux-initrd @ some more numbers]
savedefault

Error 15 : File not found ....

---

### Post by psusi on 2006-06-01
It appears that the savedefault command is the problem, which is why it works when you choose the recovery option, because that lacks the savedefault command.  

The error 15 is coming from grub when it tries to save the default choice, but I'm not sure where it saves that.  If you remove the savedefault command from your menu.lst, it should at least get you past that.

---

### Post by BoneKracker on 2006-06-02
psusi is right.  The rest of your file looks fine, and your dmraid is probably fine or it wouldn't have been able to get as far as it did.

Before you finalize your install, you should set a password and set lockalternative=true, and run update-grub.

Also, "base-config" has been deprecated in 6.06 (I don't know why).  So you'll have to manually overcome that.  That part of the howto is sketchy and assumes you can figure out how to configure the new system, but with base-config gone, that's a little tricky.  You may not need this advice, but here's a way to get started...

boot in single (recovery) mode
visudo              (set up %admin  to the same as root)
nano group      (add the group "admin" with yourself in it 
reboot and select the normal boot option
then you should be able to log in normally through gdm and use sudo as usual
if sudo gives you trouble you can su and fix it

---

