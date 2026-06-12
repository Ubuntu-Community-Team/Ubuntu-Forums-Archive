---
title: "Problems logging in with KDM"
date: 2007-04-25
forum: Desktop Environments
---

### Post by cpetzol2 on 2007-04-25
I just installed a fresh copy of Kubuntu Feisty, things were going just fine.


I have a program called Kooldock installed, and it wasnt working quite right. I thought a quick reboot might make something better. When I restarted, everything went wonderfully, and I was left at the KDM login screen. I log in.....the screen goes black.....flashes one time.....and I am back at the KDM log in screen again, like nothing had happened. No error messages, no anything.
I try again, this time setting the session type as 'failsafe'. Exact same thing.

I restarted the computer again, and booted in recovery mode, things went well, and I was left at the prompt as root. I typed "/etc/init.d/kdm", got to the KDM login screen, and everything started happening all over again.

I really dont want to reinstall everything again, but I dont know what else to do at this point. Does anybody have any ideas as to what might be causing this. Also, its not like Kooldock was crashing, it just wasnt displaying icons correctly. I cannot say with any certainty that Kooldock is the cause of the problem, and to top that off, I dont have it to start automatically. 

Thanks.

---

### Post by anator on 2007-05-28
I faced pretty much the same problem. While I don't have an answer for fixing it, you can login to your system using gdm. Go to console prompt from the kdm login screen and then type in "gdm" (requires root privileges). I then decided to live with gdm and got rid of kdm. This should prevent a show-stopper - at least you can login;).

---

