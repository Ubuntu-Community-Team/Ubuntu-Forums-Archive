---
title: "dual boot ubuntu and xp with ubuntu loaded first"
date: 2009-03-14
forum: General Help
---

### Post by mkapadia13 on 2009-03-14
Can anyone provide a basic how-to of how to install xp when you already have ubuntu loaded?

First time user, so any details explained thoroughly would be appreciated.

---

### Post by lisati on 2009-03-14
I'm sure I've seen something about this in the forums. As far as I know (I'd have to do some searching) it can be done, but it's often easier to start with Windows being installed first....... don't forget to backup your data....

---

### Post by mikewhatever on 2009-03-14
There is nothing special about installing XP before or after Ubuntu. All you need is some unallocated space (don't think the installer can handle resizing) and the installation media. After you're done, reinstall Grub to boot both OS's.
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by nml on 2009-03-14
> **mkapadia13 said:**
> Can anyone provide a basic how-to of how to install xp when you already have ubuntu loaded?

First time user, so any details explained thoroughly would be appreciated.

I'm as new or newer to Ubuntu as your....but here's a link somebody pointed to a couple of days ago.....looks pretty easy

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Mick

---

### Post by mkapadia13 on 2009-03-15
Thanks I picked up on both those links.

I have a 160gig HD, and I partitioned 17gigs for XP.  When I went to install XP, I clicked on the 17gig partition space and it didn't let me install on it - I was only able to install on the remaining 130gigs.

Does that mean that I now have XP and Ubuntu on one partition?

Also, how can I make it so it always loads Ubuntu, and how would I switch to XP?

---

### Post by mkapadia13 on 2009-03-15
Looks like I ran into the problem I posted about above.

I've ran the following lines of code 'sudo grub / root (hd0,0) / setup (hd0)' 

After the last line, I get this:  'Error 17:  Cannot mount selected partition'

Does this mean that there is only Windows on my HD now?

---

