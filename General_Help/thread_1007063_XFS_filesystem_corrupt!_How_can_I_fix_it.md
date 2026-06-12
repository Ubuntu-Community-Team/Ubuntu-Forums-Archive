---
title: "XFS filesystem corrupt! How can I fix it?"
date: 2008-12-10
forum: General Help
---

### Post by bibleman on 2008-12-10
I have been trying out XFS on my laptop using 8.10 Ibex. Everything was working fine until the other day when I was having some trouble just running regular programs. Even firefox would lock up on me and then the whole desktop options (Applications, System menus) would lose all of their text, which got replaced with little boxes as placeholders. I knew I had a problem, but I did not know what it was or how it started. Finally the computer locked up with a completely white screen and I had to hold the power button down to turn it off. No big deal right? Wrong! Next time I try to start up, it can't load the root file system. I have tried every kernel I have installed and no go with any of them. 

I tried using the Recovery mode on the 8.10 install CD but all that tells me is that I cannot mount the root file system. To further complicate the problem, this particular laptop will not run any bootable CDs unless that laptop was the one that burned them. It's nearly four years old so I can expect some problems due to its age. So trying another CD is out of the question because I can't burn it with that laptop. Is there any way that I could copy the data off the drive, say to a USB external drive or is the data pretty much lost?

I ran some diagnostics on the actual hard drive itself and they came back with 0 errors. I also ran tests on my memory to see if it was faulty and that also came back with 0 errors.

I have also read several web pages telling me to use xfs_repair. Unfortunately I cannot even get to a point where I can use that otherwise I would try it. Anybody have some ideas?

I guess my last resort would be to take the drive out and see if I can restore it using another computer? Anybody have an idea how to do that?

---

### Post by Ocxic on 2008-12-10
you could try a boot-able usb drive, w/ ubuntu or some other distro on it to attempt the repair/recovery

---

### Post by bibleman on 2008-12-13
I used some other diagnostics on the drive and everythin appears to be OK. So I believe xfs_repair might be able to fix it.

I can connect it to my Ubuntu Desktop system and I want to run xfs_repair but how can I figure which /dev/??? it is? I know my regular hard drive is /dev/sda3 but what is an external USB drive?

---

### Post by pseudonym on 2008-12-13
Download the [System Rescue CD]("http://www.sysresccd.org/Main_Page") to your desktop and install it to a USB flash drive/thumb drive/pen drive/whatever (instructions at the System Rescue CD website).

This is a great set of tools that you can use like the live CD. Boot the USB disk on your laptop and you get to a command line from where you can attempt your xfs recovery.

Be warned that the chances of a successful recovery are often slim. You may have to reinstall Ubuntu (after backing up whatever data you can using the rescue disk you made).

Tip for the future - don't use XFS on your laptop. It's good for working with very large files, but I doubt you'd be doing that on a laptop. There are probably more reports of corruption with xfs than with most file systems, and last I heard development of it had stalled.

---

### Post by bibleman on 2008-12-16
> **pseudonym said:**
> Download the [System Rescue CD]("http://www.sysresccd.org/Main_Page") to your desktop and install it to a USB flash drive/thumb drive/pen drive/whatever (instructions at the System Rescue CD website).

This is a great set of tools that you can use like the live CD. Boot the USB disk on your laptop and you get to a command line from where you can attempt your xfs recovery.

Be warned that the chances of a successful recovery are often slim. You may have to reinstall Ubuntu (after backing up whatever data you can using the rescue disk you made).

Tip for the future - don't use XFS on your laptop. It's good for working with very large files, but I doubt you'd be doing that on a laptop. There are probably more reports of corruption with xfs than with most file systems, and last I heard development of it had stalled.

Thanks for your suggestoin but it was not needed at least in my situation. My laptop is so old it won't boot off a USB drive, but for those that could boot that way it might be a viable solution. Here is what I did to recover my data.

1. Bought an USB to ATA-66 adapter. (Actually it was a hard drive enclosure)
2. Connected the hard drive up to my desktop computer.
3. Checked dmesg to find out which dev # it was. (Mine happened to be /dev/sdb3)
4. Ran xfs_repair /dev/sdb3
5. When that command finished I mounted the drive and copied over any files I needed.

Should someone else stumble upon this they should try to do something similar. From what I have read xfs_repair will usually fix a corrupted filesystem.

I will be re-installing the OS on that drive though. I believe there are still problems with it. At least I was able to recover the data.

---

