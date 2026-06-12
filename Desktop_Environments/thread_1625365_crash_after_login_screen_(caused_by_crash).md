---
title: "crash after login screen (caused by crash)"
date: 2010-11-19
forum: Desktop Environments
---

### Post by pgagy on 2010-11-19
I was tooling around with my CPU speeds in my BIOS, and I booted into Kubuntu (10.04) no problem.  It worked for a bit and then froze.  I rebooted the computer, put my CPU speeds back to default levels, but I could no longer get past the kde login screen.  when I enter my user name / pword, it would start loading, then screen goes blank and that's it.  The system works OK, I can do command line no problem, its just that I can't get into the graphical interface.  I tried apt-get install --reinstall kubuntu-desktop and xserver, but nothing works.  Any ideas how to fix it?  I'm guessing when it froze, some kind of setup file got messed up and now it freezes during bootup.  Any way to diagnose this problem?

I think I'll just reinstall Kubuntu from scratch at this point, but I figure I'll ask you guys for some help before I do that.

---

### Post by deconstrained on 2010-11-19
> **pgagy said:**
> I think I'll just reinstall Kubuntu from scratch at this point, but I figure I'll ask you guys for some help before I do that.
Don't! For the love of god please don't! 

Aside from the fact that others including myself been having lockups lately (thus the possibility of it being a common problem), the fact that these crashes have been recent and after you tooled around with your CPU speed is quite telling. At least run Memtest86 to test the stability of your current Bios settings.

BTW I've re-installed 4 times this week. It's not fun having to re-install everything and certainly not worth the time/hassle just for a spontaneous crash or two, believe me. Halfway through this week's ordeal I got all butt-hurt because of the lock-ups and attempted ArchLinux (which I absolutely love using for my headless NFS/VPN server but is a colossal pain to set up as a desktop environment). I then went crawling back to Ubuntu, and here I am now. So far so good.

Forgive my rambling, I've lost a lot of sleep lately and have had a hard week.

---

### Post by pgagy on 2010-11-19
Thanks for the warning, but my system is OK.  Everything else runs OK, I can even use the kubuntu install CD to load up a live version of the system.  It's only when I try to log in to KDE it crashes.  So there is a screwed up file somewhere.  Where do I begin troubleshooting?

> **deconstrained said:**
> Don't! For the love of god please don't! 

Aside from the fact that others including myself been having lockups lately (thus the possibility of it being a common problem), the fact that these crashes have been recent and after you tooled around with your CPU speed is quite telling. At least run Memtest86 to test the stability of your current Bios settings.

BTW I've re-installed 4 times this week. It's not fun having to re-install everything and certainly not worth the time/hassle just for a spontaneous crash or two, believe me. Halfway through this week's ordeal I got all butt-hurt because of the lock-ups and attempted ArchLinux (which I absolutely love using for my headless NFS/VPN server but is a colossal pain to set up as a desktop environment). I then went crawling back to Ubuntu, and here I am now. So far so good.

Forgive my rambling, I've lost a lot of sleep lately and have had a hard week.

---

