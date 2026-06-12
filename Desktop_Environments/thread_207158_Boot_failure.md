---
title: "Boot failure"
date: 2006-07-01
forum: Desktop Environments
---

### Post by kelcey_s on 2006-07-01
Ok, so I think that I have scoured the forums and not missed this problem. So, here goes.

I turned my computer on this morning and it wouldn't go past the loading root file system bit on the splash screen startup. So I tried starting in the command line and it said a load of things that went passed too fast to read and ended by saying "kernel panic". So I put in the cd and tried starting that up. Same problem. This leads me to think that there is some form of hardware or RAID (I don't know what this is, just read it somewhere) problem.

I am mostly a noob, using ubuntu for a month or so now, so any help would be massively appreciated.

Cheers in advance.

---

### Post by vigleik on 2006-07-01
Well, if you don't know what RAID is then you probably aren't using that. It's a way to use several hard drives together either to increase size/speed or for redundancy in case one of the drives break. It shouldn't affect the live CD anyway, so this is not your problem.

A couple of control questions. Did you change any settings in your BIOS? Or did you add any hardware, such as a PCI card?

Try checking your memory. There should be an option for doing that in GRUB. A bad memory stick could lead to problems like what you're describing, I think. 

Vigleik

---

### Post by kelcey_s on 2006-07-01
Cheers, I will check GRUB. I haven't changed anything in the BIOS and I don't think it was a bad memory stick because I haven't used it in a few days but might it be a bad dvd. I put one in yesterday and then eveything stalled until I managed to get the dvd out. Could this be the culprit?

Edit: Also I haven't install any new PCI cards or anything.

---

### Post by kelcey_s on 2006-07-02
Right, so I tried the memtest86+ thing and everything appeared to be fine. Rebooted and still wont work. I am really annoyed at this problem because I can't just reinstall because the live disc has the same problem. 
I would really like to have my Ubuntu back.

---

