---
title: "ubuntu resize partition after installing already"
date: 2009-07-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hello2007 on 2009-07-18
hi, i would like to resize the partition of my ubuntu drive how can i do that, is it possible since i already installed ubuntu on my computer already

---

### Post by wojox on 2009-07-18
With GParted you can accomplish the following tasks:

* Create a partition table on a disk device.
* Enable and disable partition flags such as boot and hidden.
* Perform actions with partitions such as:

    * create or delete
    * resize or move
    * check
    * label
    * copy and paste

---

### Post by kiridude on 2009-07-18
Yeah, just type 

```
gksudo gparted
```

this will open the partitioner and you can take it from there.

---

### Post by hello2007 on 2009-07-18
im really new to this so how can i get into gparted?

---

### Post by hello2007 on 2009-07-18
> **kiridude said:**
> Yeah, just type 

```
gksudo gparted
```this will open the partitioner and you can take it from there.

where would i type that?

---

### Post by kiridude on 2009-07-20
In a terminal. It is under "accessories" in one of your menu options at the top left. I do not remember which one because I removed mine a long time ago and use a dock. Once the terminal opens, just type what I sent before.

---

### Post by SecretCode on 2009-07-20
Just note, you can't resize a partition that's mounted - and it's not a good plan to unmount your system partition! (I don't think it will even let you but I'm not about to mess up mine by testing.)

The normal practice is to boot from a live CD.

---

### Post by raymondh on 2009-07-21
As mentioned above ... use the liveCD and access gparted from a live session (try ubuntu without changing...).  In live session, go to system > administration > partition editor (which is gparted).

In gparted, double-check that your HD is indeed unmounted.  If you see your HD in the desktop (not the gparted window), right click on it and unmount.  Another tip is to (in the gparted window) rt. click on the partitions and if you are given the option to unmount, do so.  For swap, select swapoff.

Once ready, click to highlight the partition you want to resize.

If unsure, post back a screenshot of your gparted to give us a visual guide.

Remember to backup first.  No guarantees are given.

---

### Post by RussellEngland on 2009-08-27
I'm trying to do the same. I'm very new to ubuntu and installed a dual boot alongside Vista earlier this year. I had already split Vista with 2 drives, c and d. Ubuntu is fab and I use it all the time now. So I've moved everything off my drive d, deleted the partition and wanted to resize the main ubuntu partition to use the unallocated space.

I booted up from a usb stick with the ubuntu install, then went into gparted. But I can't resize sda5. I've tried it with the drive d (sda4) space unallocated and also partitioned as ext3 but still cant resize sda5.

Or... thinking about it... is there a way to use sda4 for my documents/pictures/videos/etc?

Many thanks

Russ

---

### Post by raymondh on 2009-08-27
> **RussellEngland said:**
> I'm trying to do the same. I'm very new to ubuntu and installed a dual boot alongside Vista earlier this year. I had already split Vista with 2 drives, c and d. Ubuntu is fab and I use it all the time now. So I've moved everything off my drive d, deleted the partition and wanted to resize the main ubuntu partition to use the unallocated space.

I booted up from a usb stick with the ubuntu install, then went into gparted. But I can't resize sda5. I've tried it with the drive d (sda4) space unallocated and also partitioned as ext3 but still cant resize sda5.

Or... thinking about it... is there a way to use sda4 for my documents/pictures/videos/etc?

Many thanks

Russ

Russ,

Those keys mean that it (the partition) is mounted (or better yet ... LOCKED). If you right click on them and are given a greyed-out option to resize, try swap-off on the swap file.

For sda4 .... and this is only a suggestion .... I would convert that partition to NTFS and use it to store personal data / media.  Ubuntu will read and write in/to NTFS ... and of course, your windows install will as well.  That way, both OS can access the/your personal data/media.  For Ubuntu to read/write into NTFS, you can use (look for in add/remove) NTFS-3G.

Another advice ... try to leave 10-20% space free in your partitions.  More critical in windows.

Start backing up. And then see about moving files out of Ubuntu.  If you wish to take space away from windows, defrag Vista forst and then use its' disk management tool to shrink.  You can then expand sda4 to take up the bigger, unallocated space.

Good luck.

---

### Post by RussellEngland on 2009-08-28
Thank you for the reply :)

Yes, the screen capture was after I had rebooted, I should of mentioned that. I had the option to resize but not beyond 38gb when there was an additional 105gb free.

Funnily enough, the NTFS set up is what I had before with all my data on there.  Hence the reason the other partitions are full. But I want to move completely to ubuntu.

Cheers

Russ

---

### Post by Gausian on 2009-08-28
Russ,

Have you tried using a live-cd to adjust your partitions?  this will leave all hdd partitions unmounted/un-locked.

another recommendation (although not necessary) is, if you're going to go all Ubuntu, then do a clean re-install of the OS.  This will optimize your hdd by putting you boot sectors in the beginning and will also allow you to make a separate /home partition for your media and doc files.

---

### Post by thehaloguy13 on 2009-09-02
i have installed Ubuntu and only partitioned enough space for Ubuntu to install... i went on and installed some updates and it took up all the space and now when i try to boot Ubuntu from the HDD it sends me into this DOS like mode... like a terminal or something... and i tryed to resize the partition using GParted (in live cd) and everything is unmounted and there is around 6 gb of unalloted space just stitting on my HDD but when i try to resize the Ubuntu partition it will only let me go either way by about 8mb... can anyone help?

---

### Post by drs305 on 2009-09-02
Here is a guide I wrote about resizing the system / partition. It is geared toward taking space from a Windows partition but the principles apply no matter how you plan to do it:

[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by admiralspark on 2009-09-03
That guide is excellent, but for others experiencing the same problems I am updating his situation (Thehaloguy13 and I know each other personally).

When loading the computer, grub boots up and offers three Ubuntu partitions (could be an installation problem?). When choosing the "right" partition, instead of loading GNOME it boots into a fullscreen version of the terminal, prompting for username/password. When we entered the usr/pwd correctly it gives us an error code saying that it 'cannot save the login attempt' or some such prompt, then returns to asking for username/password. He used the same install Cd I have, which I had no problems with; I used wubi and I've never had a problem. He also only used the lowest 2.3gb for the install (partition), not the recommended 10 or 15.

---

### Post by raymondh on 2009-09-03
> **admiralspark said:**
> That guide is excellent, but for others experiencing the same problems I am updating his situation (Thehaloguy13 and I know each other personally).

When loading the computer, grub boots up and offers three Ubuntu partitions (could be an installation problem?). When choosing the "right" partition, instead of loading GNOME it boots into a fullscreen version of the terminal, prompting for username/password. When we entered the usr/pwd correctly it gives us an error code saying that it 'cannot save the login attempt' or some such prompt, then returns to asking for username/password. He used the same install Cd I have, which I had no problems with; I used wubi and I've never had a problem. He also only used the lowest 2.3gb for the install (partition), not the recommended 10 or 15.

Thanks admiralspark ....

@ thehaloguy, boot into the liveCD and in live session.  Access gparted and post back a screenshot.  It'll help the forum visualize where the 6GB is.

When admiralspark mentioned "3 ubuntu partitions", are you guys referring to the kernel or otherwise (memtest, recovery, etc)?  Kindly, while in liveCD/live session, access a terminal and post back (as well) output of

sudo fdisk -l

small L, not 1 nor I.

In the meantime, back-up your files.  If you have windows, defrag it as we may have to take space from it.

---

### Post by drs305 on 2009-09-03
> **admiralspark said:**
> When loading the computer, grub boots up and offers three Ubuntu partitions (could be an installation problem?).
For a brand new install, these could be the normal kernel, recovery mode, and a memory test option. There could also be several kernel versions available if a newer kernel was released and he has already updated his machine.

> 
He used the same install Cd I have, which I had no problems with; I used wubi and I've never had a problem. He also only used the lowest 2.3gb for the install (partition), not the recommended 10 or 15.

The 2.3GB installation isn't enough to run Ubuntu normally. There is a bug in the current Jaunty/Karmic installation CDs which incorrectly defaults to 2.3-2.5GB for a "side by side" install with Windows. Users who fall victim to this must either expand their / system after installation or reinstall without repeating the same partitioning scheme. 

[SIZE="3"]Here is a link to how a user can end up with the 2.3GB partition and what to do to avoid it in Step 4. (Note the devs are in the process of fixing the bug).[/SIZE]
[HOWTO: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271")

---

### Post by raymondh on 2009-09-03
And here is a picture of that slider (thanks to presence1960) in case you decide to re-do the installation.

[http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874](http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874)

---

### Post by drs305 on 2009-09-03
LOL - That's the graphic I made for the post I linked!  ;-)

But thank you Raymond for putting it in this link - it will help people who don't stray from this thread.

---

### Post by raymondh on 2009-09-03
> **drs305 said:**
> LOL - That's the graphic I made for the post I linked!  ;-)

But thank you Raymond for putting it in this link - it will help people who don't stray from this thread.

My apologies ... presence showed me that png not knowing it came from you.  In that case ..... thanks to Drs305 :)

---

### Post by admiralspark on 2009-09-04
Well, it's 5:36 AM on Friday and therefore I haven't seen him today. Hopefully he'll bring his laptop with him so that we can gather the information, post back here, and run through the guide. 
Minor correction of my previous post: the three "installs" that were showing up in grub are in fact the main, 'recovery' etc. I don't have them on my machine as a result of Wubi and so misinterpreted them. I believe either today or tomorrow he's going to attempt to fix the partition sizes, will post back here when results are had.

Thanks for all the responses!

UPDATE: He didn't bring the laptop today, but I think one of the problems was that he wasn't shrinking the windows partition first (hence the 8mb limit on adjustment). Tonight/tomorrow if possible he'll attempt to fix it, if that doesn't work then fresh install Monday!

Also, sort of a random question: if the HD is split into three partitions (Windows/Ubuntu/Shared) can Ubuntu applications be installed in the shared partition but be accessed like normal? Neither of us have ever used a shared partition, but it sounded like a good idea. I'm assuming it should be NTFS?

---

### Post by raymondh on 2009-09-06
> **admiralspark said:**
> 

Also, sort of a random question: if the HD is split into three partitions (Windows/Ubuntu/Shared) can Ubuntu applications be installed in the shared partition but be accessed like normal? Neither of us have ever used a shared partition, but it sounded like a good idea. I'm assuming it should be NTFS?

Admiralspark,

Ubuntu (linux) apps are better installed in an ubuntu partition.  What you can do is store your personal data, media, pics, songs, etc. in that shared partition which can be accessed by both.  Applications may only weigh so little .... yet it's our personal files that can take up so much space.  I have a bunch of media editing apps (among others as I tend to try out any free app) yet my Ubuntu root is only about 18GB.  However, my media/video is already about 360GB.

Ubuntu can read/write into NTFS.  It uses a program called NTFS3g.  Once you have set up the partitions and, ubuntu installed, go to your add/remove (or synaptic) and search for NTFS.  It's usually the first app presented.

Post back should you need assistance in partitioning. Back-up your files and defrag.

---

### Post by admiralspark on 2009-09-11
Thanks for the in-depth response! It makes sense now...I've kept my Ubuntu install under Wubi, still in the experimentation stage. Both he and I have had no time to get together and work this out, but we'll keep the forum updated. Thanks again!
-Admiralspark

---

### Post by raymondh on 2009-09-11
> **admiralspark said:**
> Thanks for the in-depth response! It makes sense now...I've kept my Ubuntu install under Wubi, still in the experimentation stage. Both he and I have had no time to get together and work this out, but we'll keep the forum updated. Thanks again!
-Admiralspark

Excellent.  Keep your windows happy and clean and you should have no/little problems with Ubuntu (it being WUBI installed).  Also, be careful to do a clean shut-down of windows at all times .... that as well as a clean "eject" (safely remove...) of any USB drives.

Happy Ubuntu-ing.

---

### Post by admiralspark on 2009-09-24
Yep, I've always been a stickler for shutting down the proper way, and using the "Safely Remove Hardware" for the USB's. But back to the subject!
News update: We got it to work. Classic lack of thinking ahead....late nights do that. He had unmounted all of his partitions, we were even adjusting in the right order, and then I got to thinking.......he has this habit of never shutting down windows (*slaps the forehead*), using sleep mode instead (which, on crappy Vista, makes no sense....it's still going to take a decade or so to boot up even with Turion X2's!). Whatever, he shut it down completely and it worked great after that. 
Thanks to everyone who helped get this going! I'm really impressed with the instant and thorough feedback that is found here on the forums, and I hope to be able to give back to the community as much as I can :-)

---

