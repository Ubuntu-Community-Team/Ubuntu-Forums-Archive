---
title: "Display Settings Lost, Found, Lost ..."
date: 2009-10-26
forum: Desktop Environments
---

### Post by heykev on 2009-10-26
Display settings in 9.04 Jaunty are being mysteriously deconfigured occasionally on reboot, so that the monitor is seen as "unknown" and forced to run in 800x600 mode.

This has happened to me before, but before I could fix the problem it fixed itself, again mysteriously.  Now its happened again and I'm hoping to come up with a solution.

A relatively recent related post (link below) seemed to be dealing with the same problem, but the thread never identified the root cause or a solution even though it was marked solved.

[http://ubuntuforums.org/showthread.php?t=1261649](http://ubuntuforums.org/showthread.php?t=1261649)

Grateful for any/all help!

---

### Post by BitJunkie on 2009-10-27
Maybe this will be helpful. 
[http://ubuntuforums.org/showthread.php?t=1256607](http://ubuntuforums.org/showthread.php?t=1256607)

---

### Post by heykev on 2009-10-27
> **BitJunkie said:**
> Maybe this will be helpful. 
[http://ubuntuforums.org/showthread.php?t=1256607](http://ubuntuforums.org/showthread.php?t=1256607)

Thanks for your response.  There were a lot of ideas in that thread (and another it linked to).  The xorg.conf talk seemed inconclusive.  Someone claimed to solve the problem using xresprobe.

I installed xresprobe just now via synaptic.  No icon, so tried "xresprobe" from the command line.  Program complains that I need to specify the driver.  Any ideas about how I might do that?

---

### Post by BitJunkie on 2009-10-27
I never installed xresprobe, so I haven't used it. A quick search found this example: ```
xresprobe xserver-xorg-intel
```Obviously, this is for Intel graphics. 
You can also try:```
 xresprobe --help
or
man xresprobe
```That's about all the help I can give on xresprobe.

---

### Post by heykev on 2009-10-29
I think the problem may be solved, though it's a sporadic problem that may spring up again later.

I tried the xresprobe trick, but couldn't get very far.  Didn't know how to specify the my driver, even though I had done the lspci trick:

```
xxx@yyy:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS

```

All that fancy linux knowledge aside, what seems to fix the problem (at least temporarily) is to press the reset button on the computer case, forcing a reboot without giving Ubuntu the chance to shut itself down properly.  Then, on restart, the higher resolution becomes available again, though I have to go into Preferences > Display and select it manually.

The root cause is not solved, but hopefully I now have a workaround.

Thanks, BitJunkie, for your help in all this.

---

