---
title: "How to use liveCD productively in a Win-based lab?"
date: 2005-12-05
forum: Desktop Environments
---

### Post by simone.brunozzi on 2005-12-05
Hi,
I'm teaching basic Ubuntu things in a WinXP-only PC lab.
Computers are quite powerful, but having only liveCD is not really easy.
I was figuring out how to be able to, at least, save some configuration in a file in the local winXP file system, and recover and use it at the start of each lesson.
I searched in the forum, but I wasn't able to find anything about that.

Also, I'd need some help with hints on things to do with a liveCD, and things to avoid. For example: avoid updating your system, because at the next reboot every update will be lost, or avoid installing new software, because at the next reboot will be lost.
I need some help from people that used liveCD for something more than a pure demonstration.

I'm confident that showing Ubuntu's power will convince the lab admin to install Ubuntu in the computers at the lab.

Thanks everybody for any help!

Best,

---

### Post by jakev383 on 2005-12-05
[QUOTE=simone.brunozzi]Hi,
I'm teaching basic Ubuntu things in a WinXP-only PC lab.
Computers are quite powerful, but having only liveCD is not really easy.
I was figuring out how to be able to, at least, save some configuration in a file in the local winXP file system, and recover and use it at the start of each lesson.
I searched in the forum, but I wasn't able to find anything about that.

Also, I'd need some help with hints on things to do with a liveCD, and things to avoid. For example: avoid updating your system, because at the next reboot every update will be lost, or avoid installing new software, because at the next reboot will be lost.
I need some help from people that used liveCD for something more than a pure demonstration.

I'm confident that showing Ubuntu's power will convince the lab admin to install Ubuntu in the computers at the lab.
[/QUOTE]

To the best of my knowledge, you still can't write to a NTFS partition safely. WinXP wants to (by default) format the drive using NTFS, so Ubuntu would be able to READ the drive, but not safely save anything to it. There are ways around this, but it's not recommended. If the drives are FAT32, then it's different. I can't think of any way to save settings to the drive without re-authoring the Ubuntu LiveCD though.  And I assume dual-booting the machines is not an option.
I don't think there's an easy solution to what you want. Hopefully someone else will prove me wrong.

---

### Post by simone.brunozzi on 2005-12-05
Thanks Jakev,
I was already getting at the point that there is no way to have a liveCD with support to NTFS-writing; I'm pretty sure it needs to recompile the kernel...
I suppose that this feature would be a very useful derived-version of the basic liveCD.
In any case, any other suggestions, or comments, or simply chattings, are more than welcome!

Best,

---

### Post by Bachstelze on 2005-12-05
You can still save your files to an USB keydrive.

---

### Post by simone.brunozzi on 2005-12-05
Hi Hymntolife,
that's a good option (and I would be grateful to have a quick but complete explanation from you, if you can); what about saving files in a central server, and retriving them at the beginning of each lesson?
I still have to figure out how to save them... like software updates, or simply newly created files.

Thanks

---

