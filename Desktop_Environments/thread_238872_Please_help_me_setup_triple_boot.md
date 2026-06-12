---
title: "Please help me setup triple boot"
date: 2006-08-18
forum: Desktop Environments
---

### Post by harisund on 2006-08-18
Here's my need. Windows XP, Ubuntu i386, Ubuntu AMD64.

My partitions are

hda1- primary - 30 GB Windows XP (currently)
hda4 - extended, under which there are
hda5 - logical - 15 GB
hda6 - logical 15Gb
hda7 - bits and pieces, or swap

Originally I installed i386 on hda5, it identified my Windows XP and created a grub entry for i386 and Ubuntu. All fine. 

I then installed AMD64 on hda6, it identified my XP and i386, and created a new grub entry. Now, grub sees all three. Sweeet. 

I upgraded my kernel in i386. However, the grub, naturally, doesn't see the new kernel, since the grub belongs to AMD64. I could technically edit the grub from my AMD64's menu.lst, or access hda6 from my i386 (on hda5) and change. 

But I want something cleaner than that. 

I am thinking of the following 2 ideas. Any help/suggestions are most welcome.
 
(1)--> Have /boot common to both operating systems. Will this work? If so, what other folders can I have mounted common across both OS? What about suggested space occupations? I was thinking I will also have stuff like /var and /tmp common. /home too. And perhaps, taking it to an extreme, /lib of i386 and /lib32 of AMD64 shared. Not worth it right? 

(2)--> Chainload the grub. Have one grub that belongs to AMD64 on the primary MBR, where the options would be 
  (a) Ubuntu AMD64
  (b) Ubuntu AMD64 recovery
  (c) Other 32 bit OS

And clicking on option (c) would take me (chainload, if that's the right term?) to a new grub, on a different partition that goes
  (a) Ubuntu i386
  (b) Ubuntu i386 recovery
  (c) Windows XP Pro

Any ideas?

---

### Post by latebeat on 2006-08-18
You don't need to chainload. A common /boot partition will definatelly work. That's what I've always done. Usually with gentoo/suse and now ubuntu. /tmp also definatelly shared and swap also. I don't know about /var I prefer them separate.

---

