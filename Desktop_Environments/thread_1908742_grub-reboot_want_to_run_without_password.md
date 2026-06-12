---
title: "grub-reboot want to run without password"
date: 2012-01-14
forum: Desktop Environments
---

### Post by stephen brown on 2012-01-14
I have a dual boot system with Ubuntu 10.10 and Win XP.  I created an applet to reboot from Ubuntu to XP. 

Basically followed these notes from forum. 

[IMG]http://ubuntuforums.org/images/statusicon/post_old.gif[/IMG]             May 22nd, 2010                                                                       #[**1**]("http://ubuntuforums.org/showpost.php?p=9343382&postcount=1")                                                                                  [KIAaze]("http://ubuntuforums.org/member.php?u=240158")
_tep 1: Set up grub2_
Add the following to /etc/default/grub:
     Code:
     GRUB_DEFAULT=saved
# if you uncomment the following line, it will keep windows as default until you boot into ubuntu again.
# GRUB_SAVEDEFAULT=true 
Then run:
     Code:
     sudo update-grub2

It works fine but I want it to run without having to enter password.  Can I do this? Is it advisable?

---

### Post by hansdown on 2012-01-14
Hi, stephen brown.

Need to know.....

Which version of ubuntu are you dual booting?

---

### Post by Krytarik on 2012-01-14
> **stephen brown said:**
> It works fine but I want it to run without having to enter password.  Can I do this? Is it advisable?
Please see this thread reg. a similar target:

[http://ubuntuforums.org/showthread.php?t=1677548](http://ubuntuforums.org/showthread.php?t=1677548)

Notes:
[LIST]
[*]In your case, you need to add "/usr/sbin/grub-reboot" to the "Cmnd_Alias" line.
[*]If you have only a single user to "whitelist", you can spare the "User_Alias" part, and enter its username directly instead of "USERS" in the lower part.
[*]As mentioned there, you still need to use "sudo", but won't be asked for your password anymore.
[/LIST]
Here is a more comprehensive guide reg. that topic:

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

Advisable? Well, you neither have to enter your password when you initiate a usual shutdown or reboot via the GUI, so I guess it's fine. ;-)

Regards.

---

### Post by stephen brown on 2012-01-14
Thanks, Krytarik. That works great.  I had a little trouble till I Figured out, you have to run update-grub after you edit /etc/sudoers. But then it worked just like I wanted.  It was good to learn about the sudoers file.

---

### Post by Krytarik on 2012-01-14
> **stephen brown said:**
> I had a little trouble till I Figured out, you have to run update-grub after you edit /etc/sudoers.
This isn't exactly obvious, yeah, to me neither. :P

Cool that you figured it out, eventually! :D

---

