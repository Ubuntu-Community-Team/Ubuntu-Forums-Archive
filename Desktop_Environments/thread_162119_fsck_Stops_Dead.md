---
title: "fsck Stops Dead"
date: 2006-04-18
forum: Desktop Environments
---

### Post by wacole on 2006-04-18
Ubuntu start-up wanted me to do a manual fsck.  Something about the 30th reboot.  I started fsck without arguments and responded "yes" to "Ignore Error" and "yes" to "Force rewrite". 

The first time I did this a few months ago, after a tedious time pressing "y", "y" a bunch of times, Ubuntu came back up and ran just fine.

Today, this same procedure - running fsck manually and pressing "y", "y" works for awhile and then the machine stops responding and the cursor disappears.  If it power down and restart (as I've done twice), same problem, though it stops at a different block each time.

This is not giving me warm fuzzies.  [I did manage to back up all my data this morning before any of this happened.]  

I would be most greatful for any guidance on this problem.

Thanks very much,

Bill Cole

---

### Post by wacole on 2006-04-18
Update ...

After running it three times with fsck -y /dev/hda1, each time it is now stopping at the same block, 3047845.  

Thanks.

---

### Post by wacole on 2006-04-18
Update ....

Using information in Ubuntu Forum thread "fsck failed, Repair Manually, newbie help" ran 5.10 LiveCD and executed sudo fsck -y /dev/hda1 from a terminal.  Took about 2 hours, but it fixed the problem.

Thank you Ubuntu forum.   [Though I'd love to know what's causing this to crash ... second time.]

---

### Post by krazyman on 2007-08-12
I was having exactly the same problem, but running fsck from the live cd runs fine. Why does fsck fail when running it from the HDD? I was even in single user (recovery) mode, fsck'ing a disc which was not mounted, whilst my fsck would not work. I had been getting a tiny bit further each time till I read the above post.

---

### Post by CaptainInsaneO on 2007-09-06
I'm having this exact problem, been trying to find a solution for months. I'm at work right now but I'll try this when I get home!

(It's so simple, I'm kicking myself for not thinking of it before!:mad:)

---

### Post by CaptainInsaneO on 2007-09-07
Well that kind of worked. My filesystem is clean but now I'm getting erros about avgd, apt-get no longer works, my xserver won't start with sudo startx (something about libXext?!) and a bunch of folders magically got deleted. Luckily, I keep Winblows on my hdd for gaming, and I've got access to my ext3 fs from there so I can just copy over the files I need and my xorg.conf for use later.

I HAVE had my eye on that Ubuntu Ultimate. I guess now is a good time to make the jump. 8)

---

### Post by sdowney717 on 2007-09-07
if your HD is mounted then running fsck on it could leave you with a damaged system, I think anyway.I read this.
That is why you should do this with a live cd.
my system after 20 boots is running a fsck, why at 20 and yours at 30?
nothing i did to change anything.

---

