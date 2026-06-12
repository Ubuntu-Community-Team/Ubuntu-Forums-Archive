---
title: "Ipod Sloooooowwwwww......"
date: 2006-09-14
forum: Desktop Environments
---

### Post by brucevangeorge on 2006-09-14
Whenever I try to sync my music with banshee or gtkpod, it takes forever to transfer to my nano. And eventually crashes after a couple of minutes.

In gtkpod, it takes 4.5 hours to transfer 3 gigs of music. When I did this in iTunes a few weeks ago (when I had XP), it took about 15min. What gives?

Is there some USB2.0 issue in Ubuntu?

Anyone else get this problem?

---

### Post by brucevangeorge on 2006-09-14
New Info:

My iPod crashes after transfering for a bit. Banshee says failed to synchronize. Is there some way to look at an error log?

---

### Post by brucevangeorge on 2006-09-14
I'm just going to keep bumping it until someone who figured it out posts.

Bump.

---

### Post by moore.bryan on 2006-09-14
*weren't we just having this discussion on another thread?*

---

### Post by brucevangeorge on 2006-09-14
Yeah. But I figure that doubles the chance that whomever figured it out, will post sometime.

---

### Post by moore.bryan on 2006-09-14
*i thought it was deja vu... if you get an answer, please let me know.*

---

### Post by brucevangeorge on 2006-09-14
Will do.



BUMP.

---

### Post by drummer4lifex on 2006-09-15
Why don't you just try using wine to install itunes. I thought I saw a guide for that around here. Also, I would write Apple a disgruntled email about linux support for itunes. I already have. The more people that do that, I'm sure the better the chances we get of a linux native itunes.

---

### Post by brucevangeorge on 2006-09-15
Yes,

But the problem seems to be that other people have working iPods. That use the normal transfer speeds... and I need to know how to get mine like that.

This is a problem that shouldn't even be.

---

### Post by moore.bryan on 2006-09-15
*and wine-ing itunes on a machine with little ram is impratical.*

---

### Post by brucevangeorge on 2006-09-15
> **moore.bryan said:**
> *and wine-ing itunes on a machine with little ram is impratical.*

That is true. iTunes sucked on my Windows... it is a memory hog. Not to mention that when I listen to music, i surf the internet.. or I'm doing work with an Office program or both. It's especially slow then.


Banshee is much better for processor and memory usage.

---

### Post by moore.bryan on 2006-09-15
*both amarok and banshee have the same lag-time with my nano as gtkpod, so i'll stick with that... any ideas why the slow speed?*

---

### Post by brucevangeorge on 2006-09-15
Plug in your ipod. And type dmesg ito the terminal, then paste the output.

I would like to compare it to mine.

---

### Post by brucevangeorge on 2006-09-15
And some more:

```

[17183037.708000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17183037.708000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17183037.716000] usb-storage: device scan complete
[17183037.752000] Driver 'sd' needs updating - please use bus_type methods
[17183037.756000] SCSI device sda: 7999487 512-byte hdwr sectors (4096 MB)
[17183037.756000] sda: Write Protect is off
[17183037.756000] sda: Mode Sense: 68 00 00 08
[17183037.756000] sda: assuming drive cache: write through
[17183037.760000] SCSI device sda: 7999487 512-byte hdwr sectors (4096 MB)
[17183037.760000] sda: Write Protect is off
[17183037.760000] sda: Mode Sense: 68 00 00 08
[17183037.760000] sda: assuming drive cache: write through
[17183037.760000]  sda: sda1 sda2
[17183037.764000] sd 2:0:0:0: Attached scsi removable disk sda
[17183037.780000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17183098.052000] usb 3-1: reset high speed USB device using ehci_hcd and address 3
[17183108.296000] usb 3-1: reset high speed USB device using ehci_hcd and address 3
[17183124.644000] usb 3-1: reset high speed USB device using ehci_hcd and address 3
[17183124.892000] usb 3-1: reset high speed USB device using ehci_hcd and address 3
[17183135.136000] usb 3-1: reset high speed USB device using ehci_hcd and address 3
[17183135.268000] sd 2:0:0:0: scsi: Device offlined - not ready after error recovery



```

---

### Post by moore.bryan on 2006-09-15
*attached is the ipod part of my lengthy dmesg...*

---

### Post by brucevangeorge on 2006-09-15
Ummmm....

Whad do I do with a .gz file? Could you just post it instead?


Also, could you try installing Banshee and synching? 

Mine Says:

"Failed to synchronize iPod

Invalid handle to path /media/ipod/iPodControl/iTunes/iTunesDb or /media/ipod/iPOdControl/iTunes/iTunesDB.bak"

This is AFTER the incredibly slow speeds.

---

### Post by moore.bryan on 2006-09-15
> Whad do I do with a .gz file? 
[I]```
gunzip file_name.gz
```
[/I]Linux version 2.6.17.11 (root@ubuntu) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5) ) #1 Thu Aug 31 21:13:50 EDT 2006
usb 4-5: new high speed USB device using ehci_hcd and address 4
usb 4-5: configuration #1 chosen from 2 choices
scsi1 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 4
usb-storage: waiting for device to settle before scanning
  Vendor: Apple     Model: iPod              Rev: 1.62
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sdb: 7999487 512-byte hdwr sectors (4096 MB)
sdb: Write Protect is off
sdb: Mode Sense: 68 00 00 08
sdb: assuming drive cache: write through
SCSI device sdb: 7999487 512-byte hdwr sectors (4096 MB)
sdb: Write Protect is off
sdb: Mode Sense: 68 00 00 08
sdb: assuming drive cache: write through
 sdb: sdb1 sdb2
sd 1:0:0:0: Attached scsi removable disk sdb
sd 1:0:0:0: Attached scsi generic sg1 type 0
usb-storage: device scan complete
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will b e case sensitive!

*i don't have banshee installed... i'll get it, run it, and let us all know.*

---

### Post by moore.bryan on 2006-09-15
*so much for banshee... it won't even run for me; it simply aborts.*

---

### Post by brucevangeorge on 2006-09-15
I tried iTunes with crossover.

Complete waste of time. Ipod not detected through wine, I don't think that there's anything that can be done there.

---

### Post by brucevangeorge on 2006-09-15
Bryan,

Use yamipod and see if you get the following error in the terminal:

"Ipod segmentation fault."

Maybe you have the exact same problem with yours that I do.

---

### Post by moore.bryan on 2006-09-16
*i tried yamipod and it sucked.  i scoured the net/forums for answers, applied "special" tweaks and patches; it still sucked.  last night i tried amarok vs. gtkpod, with comparable speeds.  looks like us linux nano users are sol.*

---

### Post by brucevangeorge on 2006-09-17
Nah. I'm not giving up. I'll find a solution.

Just keep looking and trying.

---

### Post by brucevangeorge on 2006-09-17
BTW, have you installed a package called ipodslave form the repos?

---

### Post by brucevangeorge on 2006-09-17
[SIZE="7"]YEAAAAAAA!!!!!!!!!!!!!!!!!!!!!!!!!!!![/SIZE]

I got it. It works!!

Here is what I did:

1. I installed Ubuntu from the alternate CD in text mode. I had the ipod connected the entire time. The partition manager picked it up and recognized it... (maybe it wrote an entry somewhere about it??)

2. After it installed I ran terminal and did "dmesg". I got no errors this time. Except a warning about not writing certain characters on fat.

3. Took the pod and formatted it on a XP computer that had no itunes. Just right click format... then set up your ipod when it asks for what language you would like.. and etc.

4. Installed banshee from the repositories (if that version doesn't work for you, do the same steps from the beginning except with the one from the banshee repositories, version 10.12)

5. Add music, and sync.




I hope this works. Please follow the instructions to the letter (I want to see if it works for you the way I did it.)

I tried it many other ways, and this is the only thing that worked. I think the most important step is keeping it connected while installing through text mode. But I could be wrong. I am now going to start testing this to see if it makes any difference.

---

### Post by Lord Illidan on 2006-09-17
> **brucevangeorge said:**
> [SIZE=7]YEAAAAAAA!!!!!!!!!!!!!!!!!!!!!!!!!!!![/SIZE]

I got it. It works!!

Here is what I did:

1. I installed Ubuntu from the alternate CD in text mode. I had the ipod connected the entire time. The partition manager picked it up and recognized it... (maybe it wrote an entry somewhere about it??)

2. After it installed I ran terminal and did "dmesg". I got no errors this time. Except a warning about not writing certain characters on fat.

3. Took the pod and formatted it on a XP computer that had no itunes. Just right click format... then set up your ipod when it asks for what language you would like.. and etc.

4. Installed banshee from the repositories (if that version doesn't work for you, do the same steps from the beginning except with the one from the banshee repositories, version 10.12)

5. Add music, and sync.




I hope this works. Please follow the instructions to the letter (I want to see if it works for you the way I did it.)

I tried it many other ways, and this is the only thing that worked. I think the most important step is keeping it connected while installing through text mode. But I could be wrong. I am now going to start testing this to see if it makes any difference.

Nooo... I don't think it would have made any difference whatsoever.. I am guessing the main difference is the format.

---

### Post by moore.bryan on 2006-09-17
> YEAH!
*i don't get it... was your ipod not working at all?  or are you saying the reinstall method made it fast?*

---

### Post by moore.bryan on 2006-09-17
*could simply formatting the nano to ext3 solve our problem?  would that screw anything up?*

---

### Post by SirKillalot on 2006-09-17
ipods can't read ext3 paritions, they only manage fat and hfs+

---

### Post by brucevangeorge on 2006-09-17
No. It was not formatted to ext3. Its fat. I just installed Ubuntu with the pod connected to it.

I don't know why it works.

Maybe its because its a fresh install with the original kernel?


I'm going to try to see what I can do to break it.

---

### Post by brucevangeorge on 2006-09-17
> **moore.bryan said:**
> *could simply formatting the nano to ext3 solve our problem?  would that screw anything up?*

The nano cannot read and write ext3... can it?

---

### Post by brucevangeorge on 2006-09-17
New info: It was not the Kernel. I installed linux-K7 and no problems.

Smurfdude, as soon as you try my method.. post and tell me if it works or not.

---

### Post by moore.bryan on 2006-09-18
*so, are you saying your nano is zippy-fast now?*

---

### Post by moore.bryan on 2006-09-18
*i don't have the time to fresh install today, perhaps tomorrow... stupid job.*

---

### Post by brucevangeorge on 2006-09-18
Zippidy Zip. Just like in windows.

I also noticded that "Sync with iPOd" doesn't work too well in banshee. If you say sync the library automatically (it puts all the songs it can)... it loads them and then tries to "flus the disk cache" or something like that. Then becomes unresponsive.

I found that if you do it manually.. selecting and delteing songs from the ipod and synching that works.

No idea why.

Could be a banshee bug with the nano.


Oh well. Works good now.

---

### Post by moore.bryan on 2006-09-18
*another issue i have is with banshee... no matter what i do or from where i install it, it won't run... but i digress... i'm going to format the nano here at work (xp, sp2, no itunes) and see what just hooking it up on ubuntu does.  then i'll try the install; maybe we can get to the "why" of this, compadre.*

---

### Post by moore.bryan on 2006-09-19
*alright, new issue.  formatted the nano at work (xp), went home, booted ubuntu with nano attached.  launched gtkpod with no issues.  moved a bunch of music (~3.7gb) to the nano, hit sync, asked if i wanted to make the nano's folder's (yes!), and it started... slow, again.  but then a funny thing happened... it just locked-up; stalled at copying song 43.  closed gtkpod, ejected the nano, rebooted.  this time when i sync-d, it took all of 10 seconds.  i thought "that's !@#$%-ing GREAT!"  too good to be true.  not one of the songs transfered.  for lack of a better term, all of their "headers" transfered (e.g. title, album name, artist, track), but the songs themselves wouldn't.  tried it for about 45-minutes with no luck.  gtkpod's "check ipod's files" said the songs were not on the pc... WHAT!?  so i checked through xmms... they're there.  weird !@#$ here...*

---

### Post by brucevangeorge on 2006-09-20
> **moore.bryan said:**
> *alright, new issue.  formatted the nano at work (xp), went home, booted ubuntu with nano attached.  launched gtkpod with no issues.  moved a bunch of music (~3.7gb) to the nano, hit sync, asked if i wanted to make the nano's folder's (yes!), and it started... slow, again.  but then a funny thing happened... it just locked-up; stalled at copying song 43.  closed gtkpod, ejected the nano, rebooted.  this time when i sync-d, it took all of 10 seconds.  i thought "that's !@#$%-ing GREAT!"  too good to be true.  not one of the songs transfered.  for lack of a better term, all of their "headers" transfered (e.g. title, album name, artist, track), but the songs themselves wouldn't.  tried it for about 45-minutes with no luck.  gtkpod's "check ipod's files" said the songs were not on the pc... WHAT!?  so i checked through xmms... they're there.  weird !@#$ here...*

Hmmm. I got that for a bit too. It is a default Ubuntu instalation. right? No  extra packages like ipodslave and other crap that works with the hardware.

Also. A bit of a workaround for me (I am using banshee) is to transfer about 20 or so songs at a time. If I transfer too many it freezes up right in the middle.


Also, I found that this is not just an iPod issue. I was having similar problems with certain USB sticks (locking up). And they just popped up randomly. I think its something with Ubuntu.

---

### Post by brucevangeorge on 2006-09-20
> **moore.bryan said:**
> *another issue i have is with banshee... no matter what i do or from where i install it, it won't run... but i digress... i'm going to format the nano here at work (xp, sp2, no itunes) and see what just hooking it up on ubuntu does.  then i'll try the install; maybe we can get to the "why" of this, compadre.*

What do you mean banshee won't run? What about the latest one? 10.12? Or is it the one from the repos? (10.10)

---

### Post by moore.bryan on 2006-09-20
*i'll double-check to make sure ipod slave isn't installed... banshee won't load at all; as it is loading it simply "aborts" as the terminal puts it.  it's not a huge loss, since i can't stand banshee... back to the drawing board.*

---

### Post by moore.bryan on 2006-09-21
*i finally had it, flipped out, and tried to put rockbox on the nano instead, so as to direct-copy.  no matter what i did in ubuntu, it wouldn't work, so i broke down, went back to the xp herioin pipe, and did it on there.  not as "pretty" as nano's natural theme, but a helluva lot easy to transfer... i'm going to check times when i get outta this prison we call work.*

---

### Post by brucevangeorge on 2006-09-25
> **moore.bryan said:**
> *i finally had it, flipped out, and tried to put rockbox on the nano instead, so as to direct-copy.  no matter what i did in ubuntu, it wouldn't work, so i broke down, went back to the xp herioin pipe, and did it on there.  not as "pretty" as nano's natural theme, but a helluva lot easy to transfer... i'm going to check times when i get outta this prison we call work.*

Ouch. That sucks dude. I hope they fix this problem in Edgy. It's very annoying. Apparently it wasn't present in 5.10 from what I read.

---

### Post by moore.bryan on 2006-09-25
*i'm not holding my breath for anything in edgy; i tried to upgrade this weekend and spent the whole time reinstalling the hd.  as for the nano, rockbox isn't as pretty, but it tranfers a whole lot faster (~1/3 of the time).*

---

### Post by brucevangeorge on 2006-09-25
> **moore.bryan said:**
> *i'm not holding my breath for anything in edgy; i tried to upgrade this weekend and spent the whole time reinstalling the hd.  as for the nano, rockbox isn't as pretty, but it tranfers a whole lot faster (~1/3 of the time).*

There's skins for that.

---

### Post by moore.bryan on 2006-09-26
*to be entirely truthful, none of the skins are very pretty either.  ;-)*

---

### Post by brucevangeorge on 2006-09-29
> **moore.bryan said:**
> *to be entirely truthful, none of the skins are very pretty either.  ;-)*


Ouch.

Well, if it makes you feel any better. I GOT MY NANO WORKING!

WHOPEE!

All I had to do was install Amarok instead of banshee and do that weird thing with the pod connected during OS reinstall. Now it works NO PROBLEMO!

---

### Post by moore.bryan on 2006-09-30
*i'm glad to hear it's working for you... i'm actually starting to get used to rockbox.  i wasn't a big fan of the apple firmware anyway, so this is probably a good thing.  i ran across a guy in the forums who was having a similar problem as us, but he balked at reinstalling ubuntu just to get his pod working... i hope he does it too, so we can see if that's a fix.*

---

### Post by moore.bryan on 2006-10-03
*the other guy broke down and reinstalled with ipod connected... it magically worked.  how silly can linux be sometimes?  :-)*

---

