---
title: "Wubi  9.04 Trouble"
date: 2009-04-23
forum: General Help
---

### Post by kmand on 2009-04-23
I had no trouble with wubi 8.10, but when I run the wubi 9.04 install, nothing happens. The Icon shows busy for a few seconds, then nothing. If I run it from the command line, same thing no error messages.

Any idea?

---

### Post by zaivala on 2009-04-23
I'm getting worse than that -- I get a Windows error "No Disk: Cancel - Retry - Continue" and nothing happens other than another error window no matter what I do.  I have to cancel a couple of python programs in my Windows Task Manager to get the error window to go away... and still no Jackalope.

---

### Post by zaivala on 2009-04-26
I don't know if anyone is listening... I have this thread and another one, "WUBI, WUBI, WUBI Do Ya Hate Me?"...  no responses there either.

I'd love to be reporting problems with 9.04... better still, I'd love to be running 9.04 with no problems... but right now I can't even load it.

---

### Post by Scipio_Publius on 2009-04-27
I can respond with ditto.  Must be a bug!  My experience is the same as the first post...the hour glass of nothing.

---

### Post by Peter Panter on 2009-04-28
I observed this: I use a desktop firewall (Sunbelt) which supervises whether a program wants to start another program. After clicking on wubi.exe (Wubi 9.04) the firewall asked whether wubi.exe should be allowed to start some Python process. I agreed. But wubi and the Python process died immediatly nevertheless. Therefore I completely disabled the desktop firewall and finally wubi.exe started flawlessly.  But now the installation process seems to stand still - for more than an hour now - at the stage where wubi creates the virtual disks. Wubi (Pyrun.exe) uses all free CPU power and Sysinternals Process Explorer shows that Pyrun.exe writes data to the memory or to the disk only at around 2 KB/s. That doesn't look good. :-(

---

### Post by dogpack on 2009-05-03
> **Scipio_Publius said:**
> I can respond with ditto.  Must be a bug!  My experience is the same as the first post...the hour glass of nothing.

Same story here, upgrade failed/killed Ubuntu so I decided to  start over.... wubi.exe will not run.

---

### Post by Raul1800 on 2009-05-03
> **kmand said:**
> I had no trouble with wubi 8.10, but when I run the wubi 9.04 install, nothing happens. The Icon shows busy for a few seconds, then nothing. If I run it from the command line, same thing no error messages.

Any idea?
I'm getting the same thing and all i do is hit continue like 30 times. but when i reboot windows and choose to run ubuntu a black screen appears with a bling line and doesn't do anything else. so i wonder if my pc frezees at the time of this black screen since i hit every button in my keyboard and nothing happens. PLZ HELP!

---

### Post by zaivala on 2009-05-03
Since it apparently only affects the version of WUBI sent with 9.04, and since I didn't have much luck with 8.10, I just gave up and used WUBI to install 8.04, then spent all day upgrading, first to 8.10 then to 9.04.  I now have Jaunty Jackalope installed.  Haven't checked it yet to see if it has any of the problems I've had in the past (no sound was the biggie).

Yeah, I know, I did it the way a Windoze user would do it.  Well, until I get a version of Ubuntu (or other Linux distro) working as well as I need it to, I won't be learning how to do things the Linux way.  Sosumi.

Moss

---

### Post by n4p1 on 2009-05-05
> **zaivala said:**
> I'm getting worse than that -- I get a Windows error "No Disk: Cancel - Retry - Continue" and nothing happens other than another error window no matter what I do.

I had that same error message. Try disconnect all card reader adapter or another usb-hub.

---

### Post by lisati on 2009-05-05
> **zaivala said:**
> I'm getting worse than that -- I get a Windows error "No Disk: Cancel - Retry - Continue" and nothing happens other than another error window no matter what I do.  I have to cancel a couple of python programs in my Windows Task Manager to get the error window to go away... and still no Jackalope.

This is a known problem, and some ideas on dealing with it have been discussed at [https://bugs.launchpad.net/ubuntu/+bug/365881](https://bugs.launchpad.net/ubuntu/+bug/365881)

---

### Post by Scipio_Publius on 2009-05-06
Any news on this issue?  Kinda sucks if the fix is to downgrade to 8.04 then use wubi.

---

