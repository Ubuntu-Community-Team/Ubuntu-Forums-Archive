---
title: "Install Windows after Ubuntu?  What about GRUB?"
date: 2006-09-22
forum: Desktop Environments
---

### Post by Donshyoku on 2006-09-22
Right now my machine is entirely Ubuntu, but I want to put Windows XP back on for gaming.  For the last few weeks, I have been gaming with Cedega and it really isn't holding up with a few of my more wanted titles.

So I was going to use GParted to shorten my ext3 disc and put Windows XP on the remaining free space.  However, I think this would mess up GRUB and I wouldn't have the option to dual-boot like the menu prompt would normally give me after POST.

So will this screw it up? Is there a way to "refresh" GRUB so it will update itself with the Windows partition?  Or should I just bite the bullet and do it old-fashioned... installing Windows and Ubuntu following that?

---

### Post by moore.bryan on 2006-09-22
*i think most people would suggest using vmware, but check with a gamer...*

---

### Post by elettronicha on 2006-09-22
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Donshyoku on 2006-09-22
> **elettronicha said:**
> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Great link!  Thanks!

---

### Post by Roasted on 2006-09-22
Question about this. I'm in this rutt right now and I'm not sure what to do. 

In a nutshell, here's what I did:

I have 2 SATA hard drives. No, they're not in RAID format, however I do use the second drive for backup. I set up a script to mount the 2nd drive, rsync everything in my HOME folder to it, then unmount and sit idle. Works great! But anyway, I have Windows 98. I don't have XP. I'm not about to go buy XP either. My machine is a Linux only machine. What I thought I'd do is, I'd install Windows 98 onto my system.

Now, I have all of my information backed up on that 2nd drive, so if I have to reinstall Linux, I CAN do that, but I'd rather not. If I choose to use the link above and tack on Windows 98 AFTER Linux, would that be a wise decision? Or would it be better to format my main drive, install 98, then install Ubuntu?

---

