---
title: "Is it time for panic now?"
date: 2006-07-03
forum: Desktop Environments
---

### Post by vidak on 2006-07-03
Strange things are happening with my computer (a laptop, actually). I use kubuntu, and sometimes I get an error message that some kde files in my home directory aren't writable. After a reboot, a filesystem check follows, and there are plenty of errors on the hard drive - lost inodes, etc. It happens, that I get a prompt to run fsck manually. (in case when there are more errors, I think). This happend a few times. Meanwhile it looks that the computer is getting slower (I'm not sure whether there is any relation between these two things).
This laptop is only a few month old - can this be really serious (HDD error, whatever)?
Is it time to forget the classical "DON'T PANIC", and is it time to panic now?

---

### Post by pepolez on 2006-07-03
I think it is time to panic..right after you've read this reply ;)

I had the same problem in the past - supposedly broken permissions, weird fsck outcomes, random corrupted files, etc.

It turns out the hard drive itself had a mechanical fault (that started occuring JUST outside of it's warranty >:| ) which got progressively worse. Luckily by the time the drive became too dodgey to use, I'd gotten my hands on another drive and made the faulty one secondary. All I lost in the end was a few gb of music, scripting (ugh, wasn't happy there), some movies and some pictures.

Instead of jumping to conclusions, you may want to invest in an external USB laptop HDD enclosure - purely to test the drive in another computer. If it fails again while connected into the USB enclosure on another computer, it is most likely your hard drive. The USB latop HDD enclosures here cost about AU$20 while the laptop hard drives cost about $200.

If the hard drive is fine, I'm stumped for ideas right there. Hopefully it'll be fine, in which case a fresh install might knock some sense into it.

Any other suggestions from people?

---

### Post by vidak on 2006-07-03
[QUOTE=pepolez]I think it is time to panic..right after you've read this reply ;)

I had the same problem in the past - supposedly broken permissions, weird fsck outcomes, random corrupted files, etc.

It turns out the hard drive itself had a mechanical fault (that started occuring JUST outside of it's warranty >:| ) which got progressively worse. Luckily by the time the drive became too dodgey to use, I'd gotten my hands on another drive and made the faulty one secondary. All I lost in the end was a few gb of music, scripting (ugh, wasn't happy there), some movies and some pictures.

Instead of jumping to conclusions, you may want to invest in an external USB laptop HDD enclosure - purely to test the drive in another computer. If it fails again while connected into the USB enclosure on another computer, it is most likely your hard drive. The USB latop HDD enclosures here cost about AU$20 while the laptop hard drives cost about $200.

If the hard drive is fine, I'm stumped for ideas right there. Hopefully it'll be fine, in which case a fresh install might knock some sense into it.

Any other suggestions from people?[/QUOTE]


The most weird thing is that I haven't lost any data until now... :) Luckily I got a spare winchester, which I wanted to put in this machine as soon as my dapper cds arrive (since it's larger than this)
So the question is that you also think that this winchester is doomed and I'll have to go back to the shop (hope I'm still in time of the warranty...)

---

### Post by mlind on 2006-07-03
[QUOTE=vidak]Strange things are happening with my computer (a laptop, actually). I use kubuntu, and sometimes I get an error message that some kde files in my home directory aren't writable. After a reboot, a filesystem check follows, and there are plenty of errors on the hard drive - lost inodes, etc. It happens, that I get a prompt to run fsck manually. (in case when there are more errors, I think). This happend a few times. Meanwhile it looks that the computer is getting slower (I'm not sure whether there is any relation between these two things).
This laptop is only a few month old - can this be really serious (HDD error, whatever)?
Is it time to forget the classical "DON'T PANIC", and is it time to panic now?[/QUOTE]

I think it's a sign of problems.. Root (/) partition (which probably contains your
 /home too) is normally mounted on /etc/fstab with **errors=remount-ro** flag.
kernel will remount partition read-only if filesystem problems appear at run-time.

I think you should backup your data ASAP, and run some sort of diagnostics
software for your drive. HDD manufacturers usually provide this piece of software
on their website.

---

### Post by vidak on 2006-07-03
[QUOTE=mlind]I think it's a sign of problems.. Root (/) partition (which probably contains your
 /home too) is normally mounted on /etc/fstab with **errors=remount-ro** flag.
kernel will remount partition read-only if filesystem problems appear at run-time.

I think you should backup your data ASAP, and run some sort of diagnostics
software for your drive. HDD manufacturers usually provide this piece of software
on their website.[/QUOTE]

Maybe it's a lame question, but what is ASAP?

---

### Post by mlind on 2006-07-03
[QUOTE=vidak]Maybe it's a lame question, but what is ASAP?[/QUOTE]

**A**s **S**oon **A**s **P**ossible ;)

---

