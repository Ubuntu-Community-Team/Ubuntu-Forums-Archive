---
title: "Dell Mini 9  freezed after hibernation..."
date: 2009-04-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vickoxy on 2009-04-19
Hi,
i noticed that sometimes my Dell Mini (with dell´s ubuntu) freezes after standby (when i leave the display lid opened). The screen remains black-no response-need to hold down Shut Down button to shut it off, and to restart it. Anyone has such experiences?

(i have posted this post also on mydellmini.com)

---

### Post by GsL9vBab on 2009-07-19
I found this bug submitted.  Do you have an SD card inserted? 

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-netbook-remix-default-settings/+bug/330671]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-netbook-remix-default-settings/+bug/330671")

---

### Post by vickoxy on 2009-07-20
> **GsL9vBab said:**
> I found this bug submitted.  Do you have an SD card inserted? 

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-netbook-remix-default-settings/+bug/330671]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-netbook-remix-default-settings/+bug/330671")

Hi, thanks for answer-no i didn´t have SD-Card. But, i installed full ubuntu 9.04-and so far i am very pleased-and since then have no freezing issues.

---

### Post by jwaclawsky on 2009-07-25
I had the exact same problem with 8.04 on my mini 9 and going to 9.04 has solved it.

---

### Post by vickoxy on 2009-07-26
> **jwaclawsky said:**
> I had the exact same problem with 8.04 on my mini 9 and going to 9.04 has solved it.

Yes,  same here! :D

---

### Post by ugm6hr on 2009-07-26
> **vickoxy said:**
> Hi, thanks for answer-no i didn´t have SD-Card. But, i installed full ubuntu 9.04-and so far i am very pleased-and since then have no freezing issues.

Suspend still fails with an SD inserted on 9.04.

Shame...  Seems like it should be easy enough for the suspend script to unmount all devices first, but if an open application is accessing it, it won't work.

---

### Post by vickoxy on 2009-07-26
> **ugm6hr said:**
> Suspend still fails with an SD inserted on 9.04.

Shame...  Seems like it should be easy enough for the suspend script to unmount all devices first, but if an open application is accessing it, it won't work.

So, i have inserted SD Card-and after standby i have this message:
> MMC: killing requests for dead queue

I have also conky installed, and it show in "up time" permanent working although the computer is in standby. Still, no freezing issues, and the led light blinks in standby just normal (as in standby should).

Is there any workround for this issues?

---

### Post by vickoxy on 2009-07-26
> MMC: killing requests for dead queue pops up only when there is sd card inserted. Still, no problems i have with system. Should i be concerned and look for some fix?

---

### Post by ugm6hr on 2009-07-26
> **vickoxy said:**
> pops up only when there is sd card inserted. Still, no problems i have with system. Should i be concerned and look for some fix?

I have no idea.

As I said, my unit will not actually suspend at all, and requires a Ctrl-Alt-PrntScrn-REISUB to reboot if my SD is inserted at the time of suspension.  The black screen stays with backlight on, with a single flashing cursor.

It appears we get completely different responses on the same hardware-software combo.  Hmmm...

---

### Post by vickoxy on 2009-07-27
> **ugm6hr said:**
> I have no idea.

As I said, my unit will not actually suspend at all, and requires a Ctrl-Alt-PrntScrn-REISUB to reboot if my SD is inserted at the time of suspension.  The black screen stays with backlight on, with a single flashing cursor.

It appears we get completely different responses on the same hardware-software combo.  Hmmm...

Well, did you try to format your SD Card in FAT32? I am using that format because i need to transfer data between different systems, and have no problems-didn´t try to use ext3/4.
 Or is maybe just your card?

---

### Post by ugm6hr on 2009-07-27
> **vickoxy said:**
> Well, did you try to format your SD Card in FAT32? I am using that format because i need to transfer data between different systems, and have no problems-didn´t try to use ext3/4.
 Or is maybe just your card?

Interesting thought.

I do use ext3 on SD.

There are a variety of different bugs reported relating to suspend / SD issues on the Mini.

To be honest, it isn't a problem since I gave up trying to use my SD as /home.

---

### Post by vickoxy on 2009-08-01
> **ugm6hr said:**
> Interesting thought.

I do use ext3 on SD.

There are a variety of different bugs reported relating to suspend / SD issues on the Mini.

To be honest, it isn't a problem since I gave up trying to use my SD as /home.

Well i have some little problems with new Adata 16 GB SD Card ([http://ubuntuforums.org/showthread.php?t=1224292](http://ubuntuforums.org/showthread.php?t=1224292)).

After tweaking everything is working normal (only i can not make shortcuts to SD Files, but instead i added on dektop some launchers), but after suspend i got this message:
> MMC: killing requests for dead queue ubuntu 9.04 sd card

Should i be concerned? And how do you mount your SD Card (FAT32) to different point (my card is mounted on /media/SD/), or it makes no difference on which point is mounted?

Thanks

---

### Post by vickoxy on 2009-08-01
Sorry for repeating the question

---

