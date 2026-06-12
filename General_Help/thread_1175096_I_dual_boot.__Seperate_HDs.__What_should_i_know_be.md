---
title: "I dual boot.  Seperate HDs.  What should i know before i reinstall Windows XP? and..."
date: 2009-05-31
forum: General Help
---

### Post by GirlofTime on 2009-05-31
Hello,

I dual boot ubuntu and XP on two HDs.  I only use windows for gaming and benchmarking my system.  I have to reinstall XP because of it slowing down.  I wanted to know if there's anything i have to do before i do this.  And also. Both Hard drives are western digital and have the  same amount of gigs.  Is there a command i can run to find out what hard drive belongs where?  I dont want to install XP over ubuntu by accident!  Thanks!

---

### Post by mb_webguy on 2009-06-01
If you're actually reinstalling XP, which would reformat the hard drive anyway, then to make it easier to identify the drive you can first reformat the Windows drive using gParted from Ubuntu.  Then, when you install XP, just pick the drive with the empty partition.

Also, after you install XP, you'll have to [restore GRUB]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

---

### Post by GirlofTime on 2009-06-18
> **mb_webguy said:**
> If you're actually reinstalling XP, which would reformat the hard drive anyway, then to make it easier to identify the drive you can first reformat the Windows drive using gParted from Ubuntu.  Then, when you install XP, just pick the drive with the empty partition.

Also, after you install XP, you'll have to [restore GRUB]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

Thank you very much.

---

### Post by mixmaster on 2009-06-18
I would physically unplug by ubuntu drive before installing windoze.

But then I'm paranoid about windows.  With good reason.

---

