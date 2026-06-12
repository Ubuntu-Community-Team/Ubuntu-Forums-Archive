---
title: "Synaptic Manager Showing ERROR !!!"
date: 2009-06-06
forum: General Help
---

### Post by Be_frank on 2009-06-06
Hi,

When I go for Synaptic Manager, it shows me following error.

  
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Solution please......

Thank You.

---

### Post by Jaded Misanthrope on 2009-06-06
Have you tried following the instructions given by the error and running the command? It could help; the command wouldn't be offered for no reason.

---

### Post by pastalavista on 2009-06-06
Open a terminal (Applications > Accessories > Terminal) and enter this ```
sudo dpkg --configure -a
``` It will ask for your password but won't show any sign that you typed anything. Don't worry, just type it and press enter. That should be all it takes.

---

### Post by user_not_expert on 2009-06-08
Hello,

is this thread still running? because I've got the same problem. I've tried running 'sudo dpkg --configure -a', it runs a couple of setup lines about mailmerge in open office, something py... then the machine freezes and I have to use the long press on the power button. I did try leaving it all night to see if it would resolve but no luck. There is zero activity from the disk activity light whatever I do.

I don't think it's anything to do with that setup because the same thing happened in my last install when setting up java. That time I just assumed it was a glich and did a clean re-install. This time i've put more work in and the setup has gone a lot further so I'm looking for a solution.

Once this has occured, I can't use add/remove, synaptic or 'apt-get install' to add or remove anything without going back to the same message; 'dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.' and if I follow it's advice, the subsequent freeze so I'm caught in a loop.

Other than that, the set-up is fine (I'm sending this from it), but pretty useless if I can't install, uninstall, update or upgrade!

As this has happened to two sucessive installs, I don't know if I'm dealing with a bug, a glich or a user error but if no-one can find me a workround I'm going to have to abandon this operating system on this machine which would be a shame because it's the main reason for this pc.

The pc is a eeepc 1000HD multibooting (so far) winXP as bundled but now on a much smaller partition, pc-bsd, this install of ubuntu studio (I think jaunty though it doesn't seem to want to tell me anywhere), toutou linux off a 1 gig partition at the end of the drive, and eventually I hope, os X leopard. Everything is working fine other than minor hardware and config issues, but this is potentially a major headache.

Thank you in advance for any help or advice anyone can give .-)

---

### Post by cdude on 2009-06-08
user_not_expert: seems to me that your filesystem could be corrupted. run *fsck* on the filesystem from single user mode, and see if it helps.

---

### Post by user_not_expert on 2009-06-08
err.... sorry, but what is 'single user mode' please, I've found the term before but never had occasion to follow it up.

I have tried booting the rescue choice from grub which took me to a dos-like box and i checked the file system from that, with no error messages.

---

### Post by user_not_expert on 2009-06-08
oops!

---

### Post by pastalavista on 2009-06-08
forget what was here...

---

### Post by Yellow Pasque on 2009-06-08
> I've tried running 'sudo dpkg --configure -a', it runs a couple of setup lines about mailmerge in open office,
It might be helpful to post the exact error output. You'll probably find this information towards the end of /var/log/apt/term.log

---

### Post by Yellow Pasque on 2009-06-08
Disregard above post if this is the problem. Follow the workaround in that bug report: [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/370233](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/370233)

---

### Post by FlyOutlaw on 2009-06-08
I have a similar problem only it is with Add/Remove programs.  but it will not run if Synaptic is running.  This is the Error I get when I run Add/Remove 

E: Problem executing scripts APT::Update::Post-Invoke '/usr/bin/daptup --post'

E: Sub-process returned an error code



W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>



W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/Release](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/Release)  



W: Some index files failed to download, they have been ignored, or old ones used instead.
.


Can some one please HELP 
Thanks

---

### Post by Yellow Pasque on 2009-06-08
Fly: You can only have one package manager process running at a time.

---

### Post by user_not_expert on 2009-06-08
Ok, i havn't checked the log yet (thanks, I never know which log to look in - or what most of it means), because I went to rescue mode, droped to a console and typed in the line from pastalavista. It warned me I was about to overwrite a custom config file and then went to a prompt, so I assumed it had done it. I typed 'exit' which took me back to the menu box. This doesn't have a shutdown option so I let it 'continue normal boot' The desktop was fine so I went sreight to reboot as requested.

Normal shutdown, normal start through grub, then it went into one of those scary black screens with lots of stuff. In the middle right it says

'irq 19, nobody cared (try booting with the "irqpoll" option)
Pid: 49, comm:  IRQ-19 Not tainted 2.6.28-3-rt #12-Ubuntu
Call trace:

above and below, lots of odd words and symbols

on the left is a column of numbers which flash and change about every 3 seconds. Its been doing that ever since and looks set to continue all night (its up to 3633. with 6 nos after the dot)

Is it meant to be doing this and how long should I leave it?

---

### Post by user_not_expert on 2009-06-08
Thanks Temüjin, I went to launchpad and yes its exactly that problem, so i'll follow it there and report back here when there is a solution.

In the meantime I see that pastalavista has told me to forget what he had posted, but, too late, the machine seems to be running it

'sudo dpkg-reconfigure -phigh xserver-xorg'

was how I typed it in. What now? can I turn the pc off or do I have to let it run for however long it takes? (see my last post above)
__

---

### Post by user_not_expert on 2009-06-08
Got tired and went for a second reboot anyway. everything working fine. Following the links from Temüjin it seems to be a problem between Open Ofice and the rt-kernel in studio. I'll work through the fixes tomorrow and when I find one that works for me I'll post it here,

Thanks people

---

### Post by Eredeath on 2009-06-08
I'm finding myself to have the same error, but i also can't start gnome-terminal. I don't know if that is related or not, but i'm working out of and xterm window. Keep us posted on if something works. I will be working on this in the next couple days.

---

### Post by user_not_expert on 2009-06-09
Been using Gnome terminal 2.26.0 all the way, no problems so far accept the lock up, but that's what everybody reports.

---

### Post by user_not_expert on 2009-06-09
right, 1st stage; I found this post by praseodym on launchpad at this adress:

  [https://.launchpad.net/ubuntu/+source/openoffice.org/+bug/368570](https://.launchpad.net/ubuntu/+source/openoffice.org/+bug/368570)

  "dkpg --configure -a in recovery mode causes a kernel bug (.../buffer.c:1282). The trace output ends with "fixing recursive fault but reboot is needed"

  You can fix your system by"

rm /var/lib/dpkg/info/openoffice.org-emailmerge.prerm
dpkg -r --force-all openoffice.org-emailmerge

These two lines free up all the installers, but don't run the current updates without unmarking the Open Office writer2latex package at the end, because it does exactly the same but is harder to solve as there is no .prerm file (I know, I just did it .-)  )

incidentally, this subject is also running on the 'Ubuntu studio 9.04 crashes while installing openoffice.org mailmerge' thread, do they get merged?

---

### Post by user_not_expert on 2009-06-09
ok I've found three solutions (or at least work arounds) for the Open office bug on Jaunty Studio:

**Simple.** Don't use it, use Gnome Office or something else instead but remember to un-check all Open Office updates when offered.

**Clunky.** Install the generic kernel through synaptic, boot the generic to install or use Open Office, boot the rt kernel to use studio applications. How-to by poloking, post #19 here:

[http://ubuntuforums.org/showthread.php?t=1146127&highlight=openoffice&page=2](http://ubuntuforums.org/showthread.php?t=1146127&highlight=openoffice&page=2)

**Clean.** Remove all relevant references to Open Office 3.0, install Open office 3.1. _and_ add the repository for update compatibility. How-to by praseodym on post dated 2009-05-22 here:

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/368570](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/368570)

I'm going to try the third method, I'll post the results later or tomorrow.

---

### Post by user_not_expert on 2009-06-10
Installed Open Office 3.1, same problem, same bug, same place.

there is some ambiguity on the posts on launchpad. Its possible that 3.1 can be installed under generic but will work under rt. I'll let you know tomorrow.

---

### Post by user_not_expert on 2009-06-12
> **user_not_expert said:**
> ok I've found three solutions (or at least work arounds) for the Open office bug on Jaunty Studio:

**Simple.** Don't use it, use Gnome Office or something else instead but remember to un-check all Open Office updates when offered.

**Clunky.** Install the generic kernel through synaptic, boot the generic to install or use Open Office, boot the rt kernel to use studio applications. How-to by poloking, post #19 here:

[http://ubuntuforums.org/showthread.php?t=1146127&highlight=openoffice&page=2](http://ubuntuforums.org/showthread.php?t=1146127&highlight=openoffice&page=2)

**Clean.** Remove all relevant references to Open Office 3.0, install Open office 3.1. _and_ add the repository for update compatibility. How-to by praseodym on post dated 2009-05-22 here:

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/368570](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/368570)

I'm going to try the third method, I'll post the results later or tomorrow.

Nope, Just trying to open Open Office modules under the rt kernel locks up, at least on my system, so its down to **simple** or **clunky** for me. I have now found three ways to lock up my system with OOo - I hope someone resolves this conflict/bug soon. I'm going for **clunky** at the moment.

As this is now down to the developers and there are three reported work-arounds, does this thread get marked as solved?

---

### Post by Eredeath on 2009-06-13
I'm not using studios, and openoffice seems to be working great for me. I don't understand how OO is related to the dpkg manager failing...

---

### Post by user_not_expert on 2009-06-13
Beats me, I'm not an expert. It just seems that the process of trying to install certain OOo packages freezes the system to a degree that necessitates a hard reboot. The folks over at launchpad seem to think (from an error report in a log) that there is some sort of conflict between OOo and the realtime kernel.

[https://bugs.launchpad.net/ubuntu/+bug/375394](https://bugs.launchpad.net/ubuntu/+bug/375394)

and

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/368570](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/368570)

are the links, but how it affects dpkg is beyond my level of comprehension .-(

---

