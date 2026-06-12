---
title: "Boot Freezes at &quot;Mail Transfer Agent&quot;"
date: 2009-02-19
forum: General Help
---

### Post by mockdeep on 2009-02-19
I installed tiger a little while back and it looks like it pulled in sendmail with it, or did some sort of modification to it.  Ever since then when I boot my computer I will see the bar moving up with the logo and then about three quarters of the way through the boot sequence it will show the terminal output and it will be stuck at "Starting Mail Transfer Agent".  It stays that way for a few minutes and then finally it continues to boot normally.  Any guesses as to what might be wrong?

I've got a Dell XPS M1710 running Ubuntu 8.10.

Thanks!

---

### Post by dcstar on 2009-02-19
> **mockdeep said:**
> I installed tiger a little while back and it looks like it pulled in sendmail with it, or did some sort of modification to it.  Ever since then when I boot my computer I will see the bar moving up with the logo and then about three quarters of the way through the boot sequence it will show the terminal output and it will be stuck at "Starting Mail Transfer Agent".  It stays that way for a few minutes and then finally it continues to boot normally.  Any guesses as to what might be wrong?

I've got a Dell XPS M1710 running Ubuntu 8.10.

Thanks!

If it did install a MTA then you probably need to configure the MTA as it may be timing out because of a misconfiguration.

Personally I would remove sendmail and install postfix, it is easy to set up and does the job just as well.

---

### Post by mockdeep on 2009-02-21
Ok, an update.  I don't really think I need the Mail Transport Agent, so I tried uninstalling everything that referenced it, including tripwire, which I think I installed at the same time as tiger.  This time when I rebooted it froze indefinitely at "Setting Advanced Power Management level to 0xfe (254) ... done".  It still was frozen ten minutes later.

So I used Ctrl+Alt+F1 to log into a terminal and reinstall sendmail, which got me back where I started, with a two minute freeze at MTA before finally booting up.  I tried installing postfix, which uninstalls sendmail, but that just gets me the same permafreeze after the Power Management bit.

I would be really grateful for any ideas to help me get to a normal boot.

---

### Post by mockdeep on 2009-02-24
chicken teriyaki?

---

