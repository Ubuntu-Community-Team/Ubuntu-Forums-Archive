---
title: "/dev/hda1 not found - root file system missing - update trigged it - help!"
date: 2006-08-09
forum: Desktop Environments
---

### Post by Yoshimitsu8 on 2006-08-09
Hello Everyone,
Well I was using my computer normally tonight and I did a normal update. It gave the signal to restart because a new linux kernal (I'm pretty sure) was installed so I restarted. 

After that when it got to the Ubuntu screen, that goes through and loads all the different things. It hung up on "loading root file system". After that it dropped me into busybox (I think that is what it is called) shell and said that it couldn't find /dev/hda1 (which is where my root file system lies).

I restarted a few times, only to find the same error each time :(
I used my live CD to boot in, which is where I'm typing from.
I checked out my Hard Drive with Gparted and it looks fine. It shows /dev/hda1-4 (1 has the file system on it, 2 has my /home, 4 is open partition, 3 is my swap). 

I tried to sudo mount /dev/hda1 and /dev/hda2 to see if I could access my stuff, but I get 
mount: can't find /dev/hda2 in /etc/fstab or /etc/mtab

I looked around the internet a bit and someone was saying somewhere that a specific linux kernal changed HD recognition from /dev/hda1 to /dev/hde1.
I don't have a clue, and the person who posted that could be on crack; I'm just trying to get as much information out there, so I can get help!

This is my main family computer and it is not operation at the moment please help! I know a little bit of linux, but I love it so please help me!
Thanks

---

### Post by computergroove on 2006-08-09
during bootup hit esc at the grub prompt and select a previous version of kernel and boot to see if you can read your main drive. If so revert back to your old kernel or be able to use your drive while you research why it is happening.

---

### Post by Yoshimitsu8 on 2006-08-09
Wow, thanks for the advice. I booted in normally, so I can at least boot up until I get some more help.

I have used Ubuntu for almost 2 years now and I've never had a linux kernel pull a stunt like this. Anyone have any thought on why and how to fix it?

---

