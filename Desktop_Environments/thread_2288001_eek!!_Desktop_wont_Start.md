---
title: "eek!! Desktop wont Start"
date: 2015-07-23
forum: Desktop Environments
---

### Post by Geoff_Lane on 2015-07-23
Ubuntu 12.04 LTS

Folks,

I have a multi boot machine;

12.04 LTS - Main system
14.04 LTS - Not used in general but installed to help a friend who has this version
MS Vista - Don't ask?????

For some reason today when I booted my system I got the following message;
The System is Running in Low Graphics Mode, went on to say my screen, graphics card and input device settings could not be detected and I would have to configure these myself..

Not a problem, I click OK then another message appears;
What would you like to do?

1. Run in low graphics for one session
2. Reconfigure graphics
3. Troubleshoot thew error
4.Exit to console login.

Now at this screen to keyboard input works, I cannot select the radio buttons 1,2,3 or 4 and I cannot select cancel or OK at the bottom of the message.

Tried TAB, Ctrl, Alt, Fn, shift, F keys, arrows, mouse.

Nothing works.

Screen, keyboard and graphic card are fine as 14.04 boots fine.

I can get into the 12.04 file system via terminal or using 14.04 if need be but am not sure what I need to do to correct this problem.

Any advice appreciated.

Geffers

---

### Post by Bashing-om on 2015-07-23
Geoff_Lane; Hi !

As we have this advisory:
> 
The System is Running in Low Graphics Mode, went on to say my screen, graphics card and input device settings could not be detected and I would have to configure these myself..

I would highly suspect that a proprietary graphics driver was in use, in an update process this driver got broke.

If it were me, I would purge the present driver and re-install the graphics driver.

Ubuntu has no control over
[INDENT][INDENT]3rd party (proprietary ) software
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2015-07-23
To be clear this problem is with Ubuntu 12.04 and not with Ubuntu 14.04? My I suggest that you select Recovery Mode at the boot menu and then at the recovery menu select Resume. If that gets you to a working desktop then use Additional Drivers to change video drivers.

With 14.04 Recovery Mode is in the Advanced Options for Ubuntu sub-menu. And we select video drivers at System Settings>Software & Updates>Additional Drivers tab. Things change bewteen 12.04 and 14.04. Or you can open the Dash and type Additional Drivers.

Regards.

---

### Post by Geoff_Lane on 2015-07-24
> **grahammechanical said:**
> To be clear this problem is with Ubuntu 12.04 and not with Ubuntu 14.04? My I suggest that you select Recovery Mode at the boot menu and then at the recovery menu select Resume. If that gets you to a working desktop then use Additional Drivers to change video drivers.


Regards.

Tried that, again boots into low graphics, click OK and the next screen gives me options

1. Run in low graphics for one session
2. Reconfigure graphics
3. Troubleshoot thew error
4.Exit to console login.

But at this point keyboard or mouse has no effect and I cannot go any further.

14.04 on same machine works fine.

Geffers

---

### Post by Geoff_Lane on 2015-07-24
Folks,

SOLVED, it was a lack of remaining hard drive.

I'd been helping a friend with a hard drive problem and had inadvertently created a rather LARGE disk image leaving me with virtually nothing.

Removed image and system booted fine.

Thanks for suggestions.

Geffers

---

### Post by Bashing-om on 2015-07-24
Geoff_Lane; Hey !

And thanks to you for providing what the actual problem was that led to the solution.

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]and just keep on keep'n on
[/INDENT][/INDENT]

---

