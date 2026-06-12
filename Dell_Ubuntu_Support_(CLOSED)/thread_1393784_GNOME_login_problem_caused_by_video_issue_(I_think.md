---
title: "GNOME login problem caused by video issue (I think)"
date: 2010-01-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RozNY on 2010-01-29
I am brand new to Ubuntu (and have not used a Unix environment since using AIX, SunOS, and Solaris 12+ years ago), so I may not use all the correct terminology...

I have just installed Ubuntu 9.10 on my Dell Precision 420. I am using a Dell UltraScan P1110 Monitor. I am logging into a GNOME session. 

By default, my display resolution got setup for 1600x1200 after the install. Once logged in, I changed this to 1400x1050 and everything was fine for the remainder of that session. However, upon a reboot, when I go to login, my credentials are accepted and then my monitor resets (I hear it click and the screen goes off and back on). Something then fails and I end up getting bumped back to the login screen. (I know it is not because of an invalid user/name password because when I enter a bad one, I just get an authentication failed message right away). This happens the majority of the time. If I try over and over again, eventually things will go through and I will have my gnome session up and running.

Once I am finally back in, if I change my resolution back to 1600x1200 and leave it there, the problem does not occur (my monitor also does not reset after I click the login button). I can reboot and relogin at will with no problems.  This leads me to believe that
1) the login window must be in 1600x1200 (since there is no monitor reset when I login to a 1600x1200 gnome session).
2) when the resolution has to change between the login screen and my session, something often goes wrong causing my session to abort.

Any ideas?  I looked through  the various system logs for errors, but nothing stood out (but I am a Ubuntu and Linux newbie).

My workaround right now is to change to my desired resolution for my session, and then change back to 1600x1200 prior to a logout or reboot. 

As another attempted workaround, I tried to get the resolution of the login screen to match my desired (and set) session resolution by updating /etc/usplash.conf and running sudo update-initramfs -u (I saw a posting on this somewhere), but this did not help. I don't think it actually changed anything since I still got the monitor reset after the login.

Thanks,

Bob

---

