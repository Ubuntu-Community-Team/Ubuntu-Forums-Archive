---
title: "sshfs causing kernel panic."
date: 2009-04-05
forum: General Help
---

### Post by paradigm2 on 2009-04-05
I'm going to try this here as it is a problem more so with sshfs than jaunty it appears.

I'm getting kernel panics (Num lock and caps lock alternating, system completely freezes needing reboot)when transferring over a 100 MB or so of files over sshfs.

The problem does not seem to occur otherwise besides with sshfs.

Is anyone else having issues with sshfs?

How can I get more info about the cause of this.  I checked /var/log/messages and only found three entires named *** MARK *** with nothing else right before the freeze.  The num lock and caps lock key light in alternating order off and on.  It has happened twice now and I've isolated it not being a temperature issue.

I'm using a ~4,000 bit key....should I try to take it down to 1024 to take load off the CPU (Its only a 750 Mhz cpu) ?  It is transferring at 1 MB/s to the other computer on my internal LAN.  Is there some way to take the speed down to say 300 KB/s to see if this helps with the problem?

Im not using fstab at all.  I am just mounting the sshfs shares via script on startup in gnome.  It works fine much of the time, but consistently does this.

Id rather not have to go back to Samba. :(  I'm willing to try anything.

---

### Post by Peter09 on 2009-04-05
If you are running Jaunty then you should goto the Jaunty Forum to raise this issue

[http://ubuntuforums.org/forumdisplay.php?f=352](http://ubuntuforums.org/forumdisplay.php?f=352)


I believe there has been some problems with SSH on a particular upgrade.

---

### Post by paradigm2 on 2009-04-05
> **Peter09 said:**
> If you are running Jaunty then you should goto the Jaunty Forum to raise this issue

[http://ubuntuforums.org/forumdisplay.php?f=352](http://ubuntuforums.org/forumdisplay.php?f=352)


I believe there has been some problems with SSH on a particular upgrade.

Thanks. I did that but did not get any response so I figured I would try here.  Google revealed some bug reports on it over the years, but no real fixes.  More than likely I should go file a bug report with the sshfs maintainers. 

Though if anyone else, no matter what their distro, is having this issue, Id like to know.  Also if anyone has a workaround.  I know how to change key size and will try that but I am not familiar with how to change the rate sshfs transfers unless I do something esoteric with Iptables and I would like to avoid that.

Or if anyone knows how to get more info on this.  I dont believe I can do a backtrace with a kernel panic like this...can I?

---

### Post by paradigm2 on 2009-04-05
> **Peter09 said:**
> If you are running Jaunty then you should goto the Jaunty Forum to raise this issue

[http://ubuntuforums.org/forumdisplay.php?f=352](http://ubuntuforums.org/forumdisplay.php?f=352)


I believe there has been some problems with SSH on a particular upgrade.

I found this noting a problem with a ssh tunnel:

[http://ubuntuforums.org/showthread.php?t=1108175&highlight=ssh](http://ubuntuforums.org/showthread.php?t=1108175&highlight=ssh)

But then he claims it worked after the next update.

They are having issues with nomachine (which does use ssh) but that seems different, more of a display issue.  Is there something else I am missing?

I will try the updates and see...

---

