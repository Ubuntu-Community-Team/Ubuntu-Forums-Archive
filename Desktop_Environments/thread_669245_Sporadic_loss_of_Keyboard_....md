---
title: "Sporadic loss of Keyboard ..."
date: 2008-01-16
forum: Desktop Environments
---

### Post by asearle on 2008-01-16
I am running an ASUS z9200va laptop with Kubuntu 7.10 (all updates installed).  Most of the time this all works fine and I am very happy with the whole thing. 

But on occasions, when ...

- I boot the system
- the screen-saver cuts in
- when I restart from 'sleep mode'

... , I find that the keyboard is dead.  This is the case both with the laptop's keyboard and an external (usb) keyboard.  

The mouse and touchpad continue working normally.

Whenever this happens (which is quite sporadic) I then need to power-down (dirty!) and restart the system.  The keyboard normally then returns to normal and I can continue working.

In theory this is not such a big deal but it does mean that I have become completely paranoid about losing important work which might be blocked if the keyboard isn't available at any point (e.g. after the screensaver has kicked in).

I have tried to find a pattern to this problem but so far am completely stumped.

Does anyone out there have an idea that might help me?

Regards and many thanks,
Alan Searle.

---

### Post by Bobcatben on 2008-01-16
i get this same problem on my desktop computer, although it happens more times then not for me.

---

### Post by asearle on 2008-01-17
It's good to know that I am not the only one !

I hope that someone will notice this thread and maybe has a better idea of what it might be.

Let's keep our fingers crossed.

Regards,
Alan

---

### Post by Bobcatben on 2008-01-17
Its nothing new for me, its happened since day 1 with gutsy on my computer, iam on the live cd at the moment reinstalling, which it happened on the live cd too this morning.

---

### Post by asearle on 2008-01-18
It happened twice this morning.   Arrrggghhh!

Now I would like to try switching off the log-in password (both for log-in and after the screensaver has kicked in) in the hope that the keyboard problem is just with the log-in.  However I have not yet found how/where to disactivate password protection.

I have been looking in 'System Settings / User Management' but cannot find an option to switch off password security.  Can anyone help me with this?

These are desperate measures to solve a really stupid problem and I really wish I didn't have to worry all the time that I might lose the keyboard and have to power-down.

Regards and thanks,
Alan Searle

---

### Post by Bobcatben on 2008-01-18
sadly ive already tried that, its worse with login off, as you get no feedback, just the blank desktop colored screen you get right before the login pops up, and a working cursor on the times when the keyboard doesn't work.

i really wish this bug would get figured out, i really love 7.10, it properly uses my soundcards and video card, 7.04 doesn't.

---

### Post by asearle on 2008-01-19
Thanks for warning me off the password idea.  I'll forget that.

And, yes, I agree:  7.10 is the best Linux yet but this stupid problem is a real issue for me.

I'll make another posting if I find anything.

Regards,
Alan.

---

### Post by Bobcatben on 2008-01-25
Hmm, this morning i noticed something about the times when it messes up on mine, when i boot up and have no keyboard to login with, i try to restart/shutdown with the mouse, and it acts like its going to, but then never does, just sits on a flashing dash cursor on a black screen, and i have to power it down manualy.

My ubuntu is installed on a 8.4gb ibm deskstar, on a:
Athlon 64 3400+ (2.3ghz)
1gb of ddr1 dual channeled 2100(3800 cause of dual channel)

---

### Post by sauvaget on 2008-01-27
same problem here. as of this morning my wirelesse cherry keyboard lags and disconnects regularly. 
of course at first i thought it was the batteries. but i have replaced them with brand new ones. 

very strange bug, as i cannot remember apt-updating anything but wine this weekend.

---

### Post by asearle on 2008-02-10
Yes, I also tried using the mouse to shutdown but although it starts to shut down, it just hangs and I finally have to power-down manually.

I posted a bug-report and got the recommendation to try using 'magic keys' but these would not work:  The keyboard really was dead, dead, dead.  And indeed, even if I had got the magic keys thing to work, it would merely have allowed me to reboot rather than continue to log in.

Here is my posting ...

[https://answers.launchpad.net/ubuntu/+question/22605](https://answers.launchpad.net/ubuntu/+question/22605)

I hope that someone will come back with another suggestion as this problem is really getting on my nerves.

Regards,
Alan.

---

### Post by asearle on 2008-02-16
Arrrggghhh!

This loss of keyboard problem is becoming a REAL ISSUE for me:

Today I wanted to demonstrate something to a client and found that Kubuntu didn't find the keyboard 4 times in a row.  I had to power down FOUR TIMES before the keyboard was active.

Now that particular client thinks I'm an idiot and that Ubuntu is rubbish.  And I have lost a contract.  Arrrggghhh!

If I can't fix this problem soon, then I will need to find another platform.

This makes me REALLY sad because apart from this stupid keyboard issue, Ubuntu is absolutely FANTASTIC.

Please, please help me if you can.

Thanks,
Alan Searle

---

### Post by Bobcatben on 2008-02-21
Ya, i wish someone would figure out the problem, i don't know enough about linux to figure it out myself.

there were some theory's in [another thread]("http://ubuntuforums.org/showthread.php?t=586485&highlight=boot+keyboard") i posted in about it but nothings worked yet.

---

### Post by darsu on 2008-02-21
Oh, I think this is the same thing I've been having intermittent trouble with: the keyboard and mouse buttons stop functioning, and the mouse cursor moves but no longer interacts with widgets. I never posted here about it since I assumed it would've been ignored.

The sweet spot for the error seems to be about one minute after logging in; it very rarely happens to me a long time into a session. (And I've developed this stupid superstitious sort of startup ritual: log in, fire up browser, hit ctrl-F1, idle at the text terminal for about a minute, hit ctrl-f7 and *then* start doing things...)

I've never seen error messages in /var/log that look like they're related to this event, so I wouldn't even know where to look for an error.

---

### Post by Bobcatben on 2008-02-26
Well, i guess no one has figured out what it is yet, as even 8.04 Alpha5 has the bug still.

---

### Post by Bobcatben on 2008-03-24
Still does it in the hardy heron beta now too, this is getting so frustrating....

---

### Post by crocowhile on 2008-03-25
Same thing here, although it happens only after long screensaver times (overnight).
I think it is a problem with the ACPI support for the usb.

Try add these lines to  /etc/default/acpi-support
```

ACPI_SLEEP_MODE=standby
MODULES="ehci_hcd"

```

---

### Post by Bobcatben on 2008-03-25
i would but mine does it on bootup, and my keyboard and mouse are both ps2(tho i have tried them as usb too)

---

### Post by isotope_239 on 2008-03-26
Mine happens at random. I tired installing the i386 version and still the I lose my keyboard at random. Has anybody found the remedy for this yet? Gusty is a great version I agree but this glitch is irritating... :(

---

### Post by mattress on 2008-03-26
Not sure if this will help and it's not exactly a fix, but I found it while using Kubuntu / Gentoo a while back.

It seems that on KDE, sticky keys some how gets enabled at random. All you need to do is go into
the KDE control centre and enable then disable sticky keys and your keyboard should come right.
Easier and cleaner than a reboot.

Hope this helps...

-m

---

### Post by Robbyx on 2008-05-13
> **crocowhile said:**
> Same thing here, although it happens only after long screensaver times (overnight).
I think it is a problem with the ACPI support for the usb.

Try add these lines to  /etc/default/acpi-support
```

ACPI_SLEEP_MODE=standby
MODULES="ehci_hcd"

```

I am using Hardy and am finding my mouse is often loosing its power today. I have to change usb ports to make it work.

My acpi-support file has a line:

MODULES=""

I have left the line in and added the following after it. Is that correct, or should I remove the above line?

MODULES="ehci_hcd"

Robin

---

