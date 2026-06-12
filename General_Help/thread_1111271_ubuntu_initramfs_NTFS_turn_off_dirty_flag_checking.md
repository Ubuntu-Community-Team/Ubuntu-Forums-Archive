---
title: "ubuntu initramfs NTFS turn off dirty flag checking?"
date: 2009-03-30
forum: General Help
---

### Post by whitenight639 on 2009-03-30
Hi,

I have a dual boot with hardy heron and XP pro, but whenever windows crashes (which is more often than ubuntu!!) I cant boot into ubuntu, makes having ubuntu abit pointless if I can't rely on it to help get me out the myer, 

Im dual booting on an NTFS filesystem so im using the ntfs-3g thingy. 

Its really irritating as I've got college assignements due in and I can boot into windows ive managed to clear the dirty flag after 10 mins wrestling with initframs or whatever it is but **how do I set it to permenently ignore the NTFS dirty flag, ?**

(i wish id made a separate ex2 /3 partition for ubuntu now  but too late.) 

Thanks in advance for any help.

---

### Post by ibuclaw on 2009-03-30
> **whitenight639 said:**
> Hi,

I have a dual boot with hardy heron and XP pro, but whenever windows crashes (which is more often than ubuntu!!) I cant boot into ubuntu, makes having ubuntu abit pointless if I can't rely on it to help get me out the myer, 

Im dual booting on an NTFS filesystem so im using the ntfs-3g thingy. 

Its really irritating as I've got college assignements due in and I can boot into windows ive managed to clear the dirty flag after 10 mins wrestling with initframs or whatever it is but **how do I set it to permenently ignore the NTFS dirty flag, ?**

(i wish id made a separate ex2 /3 partition for ubuntu now  but too late.) 

Thanks in advance for any help.

There is an application called **ntfsfix** which will try to fix/cover up any filesystem issues, but this is option is left rather redundant as you can only use it after Linux has booted properly.

As for ignoring the dirty journal flags, you may be able to force the mounting of the filesystem, but you will more than likely end up loosing data because of it, so use it at your own discretion.

In my opinion, it is a much better option to just boot back into Windows and let windows fix it, then shutdown cleanly and boot back into Ubuntu.

Yes, it can be an irritant, but that is probably the biggest downside to Wubi... You are always held back by the NTFS filesystem to which you reside.

Regards
Iain

---

### Post by whitenight639 on 2009-03-30
thanks tinivole,

I can't boot into windows thats the problem- i installed an anti keylogger program ( PSMAntikeylogger) last night and during the install it crashed windows and now it just cycles, the installer left no log file and as such it wont uninstall. 
anyway thats another issue which ill sort. 

how good would it be if when windows crashed like that ubuntu showed a joke about windows and offered some tools like winPE or some open source tools to fix it lol.

---

