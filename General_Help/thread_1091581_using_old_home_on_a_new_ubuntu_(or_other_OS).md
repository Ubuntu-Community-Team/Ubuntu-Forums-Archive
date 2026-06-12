---
title: "using old /home on a new ubuntu (or other OS)"
date: 2009-03-09
forum: General Help
---

### Post by Schok on 2009-03-09
how do i reinstall ubuntu and keep my old /home? will it overwrite the old one?

what if i install opensuse or mint over ubuntu, can it still use the old /home?

---

### Post by LowSky on 2009-03-09
/home has to be on its own partition for you to be able to use it on a new install. Otherwise you cannot reuse it.

and yes other OS can use the Same /home, but be carefl doing so, as some other distros use different versions of software and they might  create issues with your file settings

---

### Post by Schok on 2009-03-09
yes it is on its own partition. should i delete any software settings so it wont have any conflicts?

btw, will it detect the seperate home automatically? or do i need to do the partition editor thingy **manually** during the initial installation?

---

### Post by mike555 on 2009-03-09
In my experience using an older versions home will mess things up ...... better to back up and do a clean install , then configure you settings ......

---

### Post by Schok on 2009-03-09
so you're saying its pointless to do a seperate /home? i thought it was recommended..

---

### Post by mike555 on 2009-03-09
Yes , it's recommended , but as a backup as much as anything ...... your older home folder has settings that pertain to the version of Linux your using , and are not necessarily good for the new version , it has hidden folders with settings , etc. that might not agree with the new version ..... things like Firefox user settings , etc. are probably ok , but some might not be..... just a warning .....

---

### Post by Schok on 2009-03-10
so ill just delete the settings folder and it should be fine rite?

---

### Post by jlochhead on 2009-03-10
> **Schok said:**
> so ill just delete the settings folder and it should be fine rite?

In your home folder press ctrl.h. All the settings folders are the hidden ones, the ones beginning with a dot. If you delete these then it should be fine to use that partition without formatting it.

I would recommend doing this from the Live CD though.

---

### Post by Schok on 2009-03-10
ubuntu is not working for me anymore, it boots up into a read-only filesystem without any gui. so im stuck with windows for now.

btw, i'm planning on waiting for 9.04 but while waiting, i prefer NOT to use windows so the only CD's i got now are the latest of opensuse and mint. still trying to decide which one to install..and hopefully both can use my old /home

---

### Post by Yellow Pasque on 2009-03-10
Why isn't Ubuntu working for you? Did you actually delete all of the hidden files in /home/<user> as suggested? (That was bad advice IMHO)

If so, try booting Ubuntu to recovery mode and adding a new user (with the adduser command).

For future reference, if you want to re-use /home partition, you need to manually partition and tell it to use that partition as /home (and NOT to format it). I actually had 3 different distros (Ubuntu, Sidux, Arch) sharing the same /home user. There were a few annoying issues, but nothing show-stopping.

---

### Post by Schok on 2009-03-10
well if u read earlier as i posted, my ubuntu boots up as read-only..i dont think adding a new user is possible in read-only..btw im reformatting the partition to mint while waiting for 9.04

---

