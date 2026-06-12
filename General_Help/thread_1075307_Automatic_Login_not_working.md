---
title: "Automatic Login not working"
date: 2009-02-20
forum: General Help
---

### Post by Kissell on 2009-02-20
I usually setup Ubuntu to automatically login...  this isn't insecure, cause the user obviously has physical access to my machine anyway, so I just have it auto-login a limited access user without much rights, this way other people can use my computers and reboot and stuff, and they don't have to login.  I just switch and login with my user to better protect my stuff.

Anyway, I normally setup the computer to auto-login by going to SYSTEM / ADMINISTRATION / LOGIN WINDOW then going to the SECURITY tab and enabling automatic login.  However, I've done that on this computer, the box is checked and the username is typed into the box, but it never automatically logs in.  No error, it just never makes the attempt.  When the computer reboots it stops at the login window and I have to manually enter in the username and password, which does work when done manually, but this is undesirable, as then other people need a username and password to get on the internet and check their e-mail on my computer.  

I've unchecked the box and rebooted and set it up again, and still, no matter what I set this setting to, it never works or does anything.  It always stops on reboot at the login screen and I have to manually login.  Please help!

---

### Post by zika on 2009-02-20
do You by any chance have installed preload or used readahead for login? if You have they are the reason for no auto-login, if not, ... sorry.

---

### Post by Kissell on 2009-02-20
Wow...  actually I do have those loaded...  and I don't care about them.  I haven't noticed any difference in them making anything faster, so I'll just uninstall them.  I never would have thought they'd be causing the auto login to malfunction.

---

### Post by zika on 2009-02-20
> **Kissell said:**
> Wow...  actually I do have those loaded...  and I don't care about them.  I haven't noticed any difference in them making anything faster, so I'll just uninstall them.  I never would have thought they'd be causing the auto login to malfunction.
I'm glad I helped ... 
did it work?

---

### Post by Kissell on 2009-02-22
Yeah, finally got a chance to reboot, and autologin works just fine now.  

Awesome, I never would have thought to uninstall those programs.  

Eventually I would have just reinstalled the OS to fix it.

---

### Post by zika on 2009-02-23
> **Kissell said:**
> Yeah, finally got a chance to reboot, and autologin works just fine now.  
Awesome, I never would have thought to uninstall those programs.  
Eventually I would have just reinstalled the OS to fix it.
no, re-install is the last (if not an) option. I wonder why is it so popular. Windows legacy, I presume.

---

### Post by Kissell on 2009-02-23
Yeah, it's hard trying to wrap your head around not ever needing to reinstall or even reboot (outside of kernel updates).

But beyond the conditioning provided by windows, the fact remains that it often still works.  If I'd reinstalled Ubuntu from scratch, then those apps that were causing it to screw up would not have been loaded...  so if I couldn't find anyone that knew about this problem I would have just reinstalled and that would have fixed it, reinforcing the behavior.

---

