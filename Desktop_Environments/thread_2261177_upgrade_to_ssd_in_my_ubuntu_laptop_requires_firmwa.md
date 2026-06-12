---
title: "upgrade to ssd in my ubuntu laptop requires firmware upgrade?"
date: 2015-01-16
forum: Desktop Environments
---

### Post by varada75 on 2015-01-16
Dear Ubuntu experts,

I own a Asus U56E laptop and ubuntu is the only OS (no dual booting) and I am planning to upgrade my HDD to SSD but I am worried if it requires firmware upgrade. If firmware upgrade is required and with ubuntu will that be possible?

Please let me know your comments. Firmware upgrade required for this case? If so what are my options. 

Thanks and appreciate your comments.

---

### Post by mooreted on 2015-01-16
I suppose it depends on the drive manufacturer. My Sandisk Extreme can be updated with Linux tools; basically you just burn an ISO to a CD and reboot. You should update the firmware when you buy an SSD drive. There are often bug fixes needed.

---

### Post by varada75 on 2015-01-17
Thanks for your comment. If I understand you correctly, the firmware that comes with drive manufacturer should be checked and not the one that this laptop already has which we generally upgrade from vendor via preinstalled OS?

---

### Post by Bucky Ball on 2015-01-17
When I bought an Intel SSD, I simply cloned my HDD install, partitioned the SSD, plopped the cloned image onto a partition on the SSD, and that was that. No firmware upgrade required.

---

### Post by varada75 on 2015-01-17
Thanks. I will order SSD and will update the thread about my experience.

---

### Post by Bucky Ball on 2015-01-17
I cloned the install with [Clonezilla]("http://clonezilla.org/"), BTW. Yes, tell us how you go.

---

### Post by QIII on 2015-01-17
I needed no updates to my motherboard or the SDDs, except one case:

With the Samsung EVO 840 and there was a problem with the wear leveling algorithm in the drive firmware that had to be updated.  Unfortunately, I had problems with the Linux version of the updater and after several heated email exchanges about it not working and my providing images of the output in the terminal, I was finally told Samsung didn't support Linux.  (Samsung, by the way, is a member of the Linux Foundation and they darn well DO support Linux.)

Anyway, my solution was to put the drive in one of my Windows machines and use the Windows version of the updater.

So just be aware of that if you get a Samsung EVO 840.  The other SSDs in their lineup do not have this issue.

---

### Post by varada75 on 2015-01-17
Oh I am in fact planning for Samsung EVO 840 :( based on other threads in the forum ([http://ubuntuforums.org/showthread.php?t=2244465](http://ubuntuforums.org/showthread.php?t=2244465)) Thanks this is a valuable experience you had shared.

---

### Post by QIII on 2015-01-17
It's been great since that little hiccup.  Not a show stopper for me, but if you don't have access to a Windows machine it might be a bit of a pain.  If you update the firmware using a Windows machine before installing Ubuntu on it, you'll be fine.

---

