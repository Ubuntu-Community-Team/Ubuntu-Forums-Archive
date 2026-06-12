---
title: "Grub Loading Time (Slow)"
date: 2006-08-06
forum: Desktop Environments
---

### Post by nojobbob on 2006-08-06
Hello,
I've searched the forums, and ran into a couple of posts that mention the same problem as I am experiencing, but nothing as far as a resolution has been mentioned. (For example: [http://ubuntuforums.org/showthread.php?t=230056](http://ubuntuforums.org/showthread.php?t=230056))

Grub hangs for about 15 seconds, then says Grub is loading, which hangs for another 15 seconds, then everything works well after that. It's the initial waiting of 30 seconds that is upsetting. :mad:

Keep in mind this has nothing to do with the default timeout for selecting an option.

The HDD light on my system stays on constantly while Grub is "loading".

What is taking it so long? This seems to be specific to the new Ubuntu version (Drapper).

Anything I can do to troubleshoot or even eliminate this issue?

I was going to install LILO, but everything discourages it. That and a severe lack of support (and/or willingness to help) for LILO.

I waited for 6 weeks for my Ubuntu CD. I trashed my old install for this version, and now, I'm regretting it, since this 30 second load time for Grub is unexceptable, regardless of what OS I'm booting into. :sad:

TIA

---

### Post by Satch on 2006-08-06
I am having the same problem only mine takes about 1 to 1.5 mins to get to the Grub menu.  I posted the same question here [http://www.ubuntuforums.org/showthread.php?t=230056](http://www.ubuntuforums.org/showthread.php?t=230056) and have not gotten any reply.  From searching the forums it would seem that several people have had this problem since Breezy came out.  I love using Ubuntu, it is by far the best disto of linux that I have used and I am ready to make the full switch and just delete WinXP.  But not until I can get this to load correctly.  Anyone at all got any ideas?
Thanks
Satch

---

### Post by Rich99 on 2006-08-07
Is it your cdrom?  I know on my laptop, if I have a cdrom in the drive, or if the drive is ejected, grub loads instantly.  However if the drive is closed & empty, grub sits there polling the drive for a minute or two before it loads (and therefore the ide light is on).

I've seen it under debian etch & now dapper drake, I've posted to the grub & debian lists but no-ones been able to help.  The windows boot loader is instantaneous either way :)

---

### Post by nojobbob on 2006-08-13
Well, since I seem to have bad luck with people in forums, I fixed my own problem.

So for anybody who may be looking at this thread in the future because they too have found that GRUB sucks, here was how I fixed my own problem.

First, I downloaded the GAG boot loader. (Google for it, because that's how I found it.)
Don't worry. It's very simple and very straight forward as far as setup and operation goes.
Next, I had to re-install Ubuntu.
This is how I found out that Ubuntu hates LILO, as in my first attempt to fix this problem, I tried to install LILO and found out the hard way that it didn't properly install.
So on the 3RD installation of Ubuntu, I restarted my system. 
I waited the 2 minutes for GRUB to load and then loaded the Ubuntu install.
I then opened up a console and gave the command:
sudo grub-install /dev/hdb1

Shutdown Ubuntu, loaded my floppy disk with my GAG backup, and turned my machine back on. Re-instated the GAG loader and rebooted.

Now, when my machine boots up and I want to get into my XP install, I don't have to wait 5 minutes.

Instead, the GAG loader instantaniouly boots up.
When I choose Ubuntu, there is still a 30 second delay, as GRUB loads from the secondary disk, but it is STILL FASTER than if I had GRUB load from the primary disk.

Does any of this makes sense, because it still doesn't to me, but you know what, it works and now there is documentation on how to get around the slow load time of GRUB.

---

### Post by GTvulse on 2006-08-13
[quote=nojobbob]
This is how I found out that Ubuntu hates LILO, as in my first attempt to fix this problem, I tried to install LILO and found out the hard way that it didn't properly install.
[/quote]

That's incorrect. Rather, LILO can't write on top of an already existing GRUB bootloader stage.

---

