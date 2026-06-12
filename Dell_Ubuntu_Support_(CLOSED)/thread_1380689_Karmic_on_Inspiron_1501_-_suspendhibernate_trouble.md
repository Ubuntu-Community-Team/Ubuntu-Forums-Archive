---
title: "Karmic on Inspiron 1501 - suspend/hibernate trouble, etc."
date: 2010-01-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Beniamin on 2010-01-13
Hello all,

I have an Inspiron 1501 laptop that I've installed Ubuntu 9.10 on, and all has gone fairly well.  However, it has several issues, and since they may or may not be interconnected in some way, I will describe them all.

First of all, when you boot up the machine, instead of loading the GUI, it gives you this screen:

```
Ubuntu 9.10 computer-name tty1

computer-name login:
```

If you log in, it's like a terminal line, but regardless of whether you log in or not, it eventually brings up the GUI after a period of several minutes.  Not a major deal, but it's frustrating to have to wait so long.

**Suspension** - Sometimes it will suspend, sometimes not.  Often times when waking up from suspension, the screen will get stuck on two columns of scrolling grey lines, with a white column in the center.

**Hibernate** - It seems to go into hibernation, but upon waking up, it gets stuck on a black screen.

**Freezing up** - The computer just randomly freezes up from time to time--rather unusual for Ubuntu, I would think.

Any ideas?  Really I would most like to get the suspension working, and fix the freezing; the other things are second in priority.  Thanks in advance!

---

### Post by Nerdfest on 2010-01-16
I have a similar problem ... although a suspend will occasionally work, meaning a timing problem I assume. How much memory do you have installed?

---

### Post by Beniamin on 2010-01-16
It has 1 GB of RAM.

---

### Post by Nerdfest on 2010-01-17
Mine suspended fine until I went from 2GB to 4 ... but I'd rather just leave it on than lose the memory. It's only rated to work with 2. Perhaps I should try it again to see if that's still the case. It was several releases ago that it worked regularly.  I just tried a couple of things, and mine seems to suspend and resume successfully now, although I've only tried it 3 times so far. I haven't tried hibernate yet, but I generally had more luck with that anyway.  The changes that seemed to fix it for me were changing the following settings in  /etc/default/acpi-support:  POST_VIDEO=false (original value was true)  DOUBLE_CONSOLE_SWITCH=true (originally uncommented)  I'm hoping this takes care of our problems, but it's too early to tell for sure.

---

### Post by Nerdfest on 2010-01-17
This sounds interesting: [http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)

---

### Post by Nerdfest on 2010-01-17
I haven't actually addressed the freezing up you mentioned. The only time I have anything like this happen is after the laptop has been on (and not suspended, as I couldn't) for a month or 2. The display will occasionally get distorted with lines going through it, etc, and soon afterwards it will freeze. Looks like a problem with the video memory to me, but I'm no expert. Other than that, it never freezes up for me.

---

### Post by Nerdfest on 2010-01-17
At some point after a resume, I had a blank screen, and total lock-up ... unlikely to be a coincidence. I changed the POST_VIDEO back to true, and am trying SAVE_VIDEO_PCI_STATE set to true. I also see an interesting value called ACPI_SLEEP_MODE that shows promise.

---

### Post by Beniamin on 2010-01-19
Hmm...  Well, I tried what you suggested in #4, and haven't seen much of a change.

And actually, this is a computer I set up for my mother, so I won't have access to it for several months while I'm at college.  I'll play with it some more next time I'm home and see if I can figure anything out.

Thanks!

---

### Post by StuartN on 2010-02-28
Has anyone managed to sort out running Karmic on a Dell Inspiron 1501?

I just installed Karmic, having run Hardy without any issues for a long time. Now I have apparently random freezes, the system partition becomes readonly, resume from suspend fails, bootup reports that one or more of your mounts is not ready, etc.

I see many, many threads that have in common and AMD SB600 motherboard, the ATI graphics card and the Broadcom wireless (I guess a popular laptop combo across several vendors), but no solutions.

I did try adding "noapic" to my bootup options, but that interfered with wireless connectivity. It seems like Karmic just does not get on with this hardware, and probably Lucid will be no better.

---

### Post by elitenoobboy on 2010-03-01
> **StuartN said:**
> Has anyone managed to sort out running Karmic on a Dell Inspiron 1501?

I just installed Karmic, having run Hardy without any issues for a long time. Now I have apparently random freezes, the system partition becomes readonly, resume from suspend fails, bootup reports that one or more of your mounts is not ready, etc.

I see many, many threads that have in common and AMD SB600 motherboard, the ATI graphics card and the Broadcom wireless (I guess a popular laptop combo across several vendors), but no solutions.

I have an inspiron 1501, and everything in karmic worked correctly except every once in a while, the gui would delay starting, bringing you to a console login screen for about a minute until the gui finally loaded. I upgraded to lucid alpha, and I haven't seen the gui boot delay yet (most likely the updated ati drivers fixed that problem), however suspend and resume are broken at the moment in lucid. Hopefully that will be fixed.

---

### Post by StuartN on 2010-03-01
> **elitenoobboy said:**
> I have an inspiron 1501, and everything in karmic worked correctly except every once in a while, the gui would delay starting, bringing you to a console login screen for about a minute until the gui finally loaded. I upgraded to lucid alpha, and I haven't seen the gui boot delay yet (most likely the updated ati drivers fixed that problem), however suspend and resume are broken at the moment in lucid. Hopefully that will be fixed.

Was the system possibly running a filesystem check during that delay? Do you have any line like "EXT3-fs: INFO: recovery required on readonly filesystem" in kern.log / messages / sys.log? (**grep -i recovery /var/log/*** is a quick check).

---

### Post by elitenoobboy on 2010-03-01
> **StuartN said:**
> Was the system possibly running a filesystem check during that delay? Do you have any line like "EXT3-fs: INFO: recovery required on readonly filesystem" in kern.log / messages / sys.log? (**grep -i recovery /var/log/*** is a quick check).

Nope. It was at the console login screen for that whole minute, and there was no hard drive activity. I could have logged in right there and then do a "startx", but then a minute later, my session would be interrupted when a second gui started up. filesystem checks typically give some sort of on screen feedback.

---

### Post by 7350 on 2010-03-04
Someone stated that after disabling the ATI driver, the issue was resolved.
I am a monkey-see-monkey-do keep the idiot's guide handy sort of guy. Is there someone who would tell me how to go about (safely) disabling this ATI driver?

Many, many thanks in advance.

---

### Post by elitenoobboy on 2010-03-04
> **7350 said:**
> Someone stated that after disabling the ATI driver, the issue was resolved.
I am a monkey-see-monkey-do keep the idiot's guide handy sort of guy. Is there someone who would tell me how to go about (safely) disabling this ATI driver?

Many, many thanks in advance.

The quickest way to disable it would probably be to uninstall it using synaptic. After telling synaptic to uninstall the driver, it should be smart enough to install something else in place, such as mesa or whatever. Though you should be warned that doing so can lead to X not starting up, so you should be able to use apt-get from a commandline if you have to put the ati drivers back in.

---

### Post by StuartN on 2010-03-05
> **elitenoobboy said:**
> Nope. It was at the console login screen for that whole minute, and there was no hard drive activity.

Mine has run for the whole of this week (Sunday-Friday) with multiple suspend and resumes, until this morning. Then it resumed to a black screen with no obvious activity of any kind. Behind the scenes it was doing this (from kern.log), probably for as long as you leave it:

```
[51491.625750] PM: resume devices took 2.012 seconds
[51491.629782] PM: Finishing wakeup.
[51491.629820] Restarting tasks ... done.
[51491.765690] attempt to access beyond end of device
[51491.765700] sda4: rw=0, want=31364604760, limit=20482875
[51491.773415] attempt to access beyond end of device
[51491.773423] sda4: rw=0, want=31364604760, limit=20482875
```

I forced a power shutdown and it restarted with the usual filesystem mounted readonly check recorded in dmesg.

---

### Post by elitenoobboy on 2010-03-05
> **StuartN said:**
> Mine has run for the whole of this week (Sunday-Friday) with multiple suspend and resumes, until this morning. Then it resumed to a black screen with no obvious activity of any kind. Behind the scenes it was doing this (from kern.log), probably for as long as you leave it:


That wouldn't be related then. It only does that when booting up, not when resuming from standby. When I was on karmic, standby and resume worked fine. I think my problem is related to the ati graphics driver, but I have no proof of that. I don't recall seeing anything happening in kern.log.  Now that I am on lucid, it boots up fine for the most part, but standby is broken and trying to use it cripples it to where it won't boot for a while (until an hd check?).

---

### Post by StuartN on 2010-03-06
Here are a couple of other threads about suspend / resume failure where laptops present a blank and unresponsive display at bootup with filesystem locking / corruption under Karmic:

Random freezing in 9.10 karmic [http://ubuntuforums.org/showthread.php?t=1309015&page=17](http://ubuntuforums.org/showthread.php?t=1309015&page=17)

Karmic won't wake up from suspend (sleep) mode [http://ubuntuforums.org/showthread.php?t=1363881&page=7](http://ubuntuforums.org/showthread.php?t=1363881&page=7)

Repetitive massive filesystem corruption [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528981](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528981)

system crashes. On boot, fsck gives inode *** part of an orphaned list. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/502318](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/502318)

---

