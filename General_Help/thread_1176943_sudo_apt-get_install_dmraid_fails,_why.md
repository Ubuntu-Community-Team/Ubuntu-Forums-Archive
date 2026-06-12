---
title: "sudo apt-get install dmraid fails, why?"
date: 2009-06-02
forum: General Help
---

### Post by ladasky on 2009-06-02
Hi folks,
 
I'm going through a major upgrade here.  A new motherboard, and two new SATA hard drives which I would like to use as a RAID 1.  My old PATA hard drive is also in the system for now and runs Heron nicely.  The plan is to get Ubuntu to boot from the RAID, and then to retire the PATA drive.

I have done everything that my motherboard manual recommends to configure the BIOS for RAID.  Now it's time for me to deal with Ubuntu.  I am trying to follow the guidelines [here]("https://help.ubuntu.com/community/FakeRaidHowto"), but I can't get past the first step.  I've booted from the Live CD as recommended, opened a terminal, and tried to install dmraid.  Here's the result:

```

ubuntu@ubuntu:~$ sudo apt-get install -y dmraid 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package dmraid
```

I've never tried to install packages while running from the live CD before.  Honestly, I don't know where the OS would put them if it doesn't have privileges on any of my hard disks.  Can anyone explain to me why the package is not found?  The answer may be in the apt-get docs.  If so, I read through it without recognizing it...

Thanks for your help!

---

### Post by michy99 on 2009-06-02
Does dmraid show up in Synaptic Package Manager?

---

### Post by ladasky on 2009-06-02
> **michy99 said:**
> Does dmraid show up in Synaptic Package Manager?

No it did not.  I actually tried Synaptic first, even though the instructions said to open a terminal and type in apt-get... probably because after you install dmraid, there are more commands you can only launch from the terminal.

And, ah-HA, you made the light bulb go on over my head. 
 
:!:
:shock:
 
The dmraid package is NOT in the default repositories... I added the "universe" repository to Synaptic, and this time I could find dmraid in the search.
 
Thank you, first problem solved!  I'm sure there will be more later.  ;)

---

### Post by ronparent on 2009-06-03
All local install processes from the live cd are in memory. That is why it is tempoary and lasts only as long as the session.  (it would have to be done with each subsequent boot). You can chroot once the raid is up and mounted to make a persistent install to your root drive for the new install.

---

### Post by ladasky on 2009-06-05
Thanks, ronparent, for the information about where installed packages reside when you boot from the Live CD.  I wondered!
 
As it turns out, I did not need dmraid, because I don't need Windows compatibility.  I went with the Alternate Install CD, which allows you to implement Linux native RAID on setup (using mdadm, I believe).

---

