---
title: "HELP! KDE task/menu bar disappeared and I can't get it back!"
date: 2006-07-10
forum: Desktop Environments
---

### Post by Geshtar on 2006-07-10
I was using adept to install doxygen, graphviz, and lxr-cvs, but it had some error on install, gave an error message and stopped.  Within a few seconds of this error, my KDE task/menu/start bar disappeared.  

It does not want to come back.  I have tried staring new KDE sessions and it still is gone.  Without it, I cannot get into the KDE control panel because I do no remember the command line name for it...and I do not see anything that looks like it when I search /usr/bin/ for things starting with 'k'.

Weirdly, the applications that had an error when installing with adept, showed up as installed....I removed them from the system, but still no luck getting my start bar back.

Any suggestions on what to do would be greatly appreciated, I can still use my desktop thanks to the alt+space launcher program, but it is a big loss/inconvience without that bar/menu.

Thanks in advance.

---

### Post by bigken on 2006-07-10
boot into safe mode and type apt-get install kubuntu-desktop hope this helps ;)

---

### Post by MartinG on 2006-07-10
Try Alt-F2, and in that the command "kicker" (that's what KDE calls the task/menu bar).

---

### Post by Geshtar on 2006-07-10
thanks for the info on what it was called.  Turns out kicker was still running but was hidden and would not come up when I put my cursor on it. (Normally I have it set to auto-hide).  Once I looked up some more kde shortcuts, I managed to get into the System settings panel, where I turned off auto-hide and it came back.  Oddly enough, I tried turning auto-hide back on, and kicker now works properly(it pops up when I put my mouse at the bottom of the screen).  I guess it was some very rare bug.

---

### Post by Outworlder on 2006-11-19
> **Geshtar said:**
> thanks for the info on what it was called.  Turns out kicker was still running but was hidden and would not come up when I put my cursor on it. (Normally I have it set to auto-hide).  Once I looked up some more kde shortcuts, I managed to get into the System settings panel, where I turned off auto-hide and it came back.  Oddly enough, I tried turning auto-hide back on, and kicker now works properly(it pops up when I put my mouse at the bottom of the screen).  I guess it was some very rare bug.

I don't like thread necromancy, but I've got the same problem as well, on Edgy. The damn panel is hidden and I can't get it back.

Anyone knows how to unhide the bugger?

---

### Post by Outworlder on 2006-11-19
Fixed it.

I did a 
```

dcop kicker kicker showTaskBarConfig

```

Some panel settings were different, so I set them again an now everything works.

---

### Post by ringmaster on 2006-12-12
Today I had the same problem with kde 3.5.3. I did:
- sudo killall kicker
- kicker
And it appeared again, but when it goes auto-hiding then it doesn't comes up even with the cursor over the area. 
The problem is solved configuring to not to hide, aply, and then revert the configuration.
I could be a bug with the config file (positioning the cursor over the area doesn't get detected) and when the taskbarconfig is restored it is solved.

---

### Post by fajardo on 2007-01-20
had the same problem but now it's solved, due to you guys, but it's 100% a bug

---

### Post by thebadrash on 2007-01-27
This happened to me too. I went as far as reinstalling KDE to try and fix it... the fix that worked was:

dcop kicker kicker showTaskBarConfig

- so thanks a lot, but yes: this must be some sort of bug.

---

### Post by loclarkey on 2007-02-05
I can second this as well.  I had just installed a few extensions in firefox (I don't know if this is relevant), and the menu bar just disappeared.  I had it set to hide automatically, but it wouldn't pop back up.  The same fix as above worked:

dcop kicker kicker showTaskBarConfig

Brought up the dialog box for taskbar settings, and I unchecked autohide for the time being.

I'm relatively new, can someone point me to a HOWTO for bug submission?  I'd love to give my $0.02 back.

---

### Post by the79bomb on 2007-02-05
I have this same problem.  However I can't get a terminal window up because I can't find where it is in the filesystem.  I tried creating launchers with the commands listed already typed in but running this does nothing.  I have a blank desktop with the drive icons and nothing else.

Thanks, Tim

---

### Post by thebadrash on 2007-02-07
Hi - can you right-click the desktop? If so, you should see the menu option 'run command'. Choose this and then enter 'Konsole' as the command. This will display the terminal.

An alternative to the desktop right-click is to press Alt-F2.

---

### Post by Helladog on 2007-03-27
Same issue here, running kconrol wasn't of any use to me but the "dcop kicker kicker showTaskBarConfig" command is a keeper!  I'll be meeting her parents tomorow!

Thanks all for this fix!

---

### Post by hasinasi on 2007-10-13
Hey all,
I know this thread is ooooooold!
Anyway, I have the same problem. Simply after using it for some time, kicker auto-hide functionality gets broken. It won't un-hide. Also, in the same state it won't auto-hide any more. [I am in the lucky situation to be able to show it even when it's broken, as I have configured a shortcut to show the KDE ("start") menu, which also shows kicker].
The only thing it needs to work around this problem is unchecking "auto-hide" in the settings, and then checking it again and either close the settings menu or simply click "apply". This bug is not a big deal, but can get pretty annoying anyway. Has anyone cared to submit a bug somewhere? Or does there any other thread exist about the problem?
Best,
--hasi.

---

### Post by dpc_6 on 2007-10-25
[http://bugs.kde.org/show_bug.cgi?id=151330](http://bugs.kde.org/show_bug.cgi?id=151330)

---

### Post by stoobers on 2008-03-13
I have this same problem, under suse 10.1 (KDE 3.5) but this work around should work with Kubuntu, also.  Praise the Lord for KDE.  It's really united the different distributions together onto a common, GPL driven ground.

Here is how I fixed this problem:

hit Alt-F1 (this forces the task bar to appear.)

opposite click the task bar
click 'configure panel'
click 'hiding'
click 'only hide when panel hiding button is clicked'
click 'apply'
click 'ok'

THEN
repeat the above but instead of 'only hide when...' click 'hide automatically'

Viola!

Restarting X didn't solve it.  Restarting the computer didn't solve it.  I was also able to fix this by deleting my .kde directory and then logging in, but I lost all my settings, so I don't recommend it.

Christopher Stubban
[http://www.NetworkComputerRepair.com](http://www.NetworkComputerRepair.com)
$155 Flat Rate Computer Repair
Database / Programmer / Web Consultant
Windows 98/XP/Server 2003/5 & Linux

---

### Post by WurmD on 2008-04-11
Hello all, this threads title says it all.

Although my problem isn't the same, it isn't the auto-hide bug,
I was trying to remove a package with Adept Package Manager (i can't exactly recall what, maybe GSL or Glib) because the package provided was of an older version and i needed the newest, which i had already downloaded.
But in the middle of it, it stopped, when i asked to "show details" a little window explaining that usually when removing or updating ... KDE closed all sessions (maybe), but he wasn't able to close 1 of them, YES or NO to close that session.
But i couldn't click Yes or No, or do anything about it.
So i tried closing Adept; Everything exploded and i rebooted.

Now i have no TaskBar and no Konkeror..

The command "kicker" is not recognized so
dcop kicker kicker showTaskBarConfig
doesn't do anything for me
Also when i shut down, "kdevelop3 crashed and caused the signal 11 (SIGSEGV)"
Also Also "sudo apt-get install ..." doesn't work in recovery mode because it seems he can't acess the internet, and so can't download stuff, he says "blablabla.ubunto.pt can't be resolved" (i have internet by the Network, by a cable :P lol)

How do i reinstall what seems to be lacking? (i've tought about reinstalling Kubunto but was afraid of losing everything else installed, it took me the better part of 3 days to get everything up and running [YARP, Ace, OpenCV, GTk+, ...])

Thank you so much for your time

---

### Post by foof on 2008-04-28
I solved it this way:
[http://ubuntuforums.org/showthread.php?t=549818](http://ubuntuforums.org/showthread.php?t=549818)

---

### Post by fuzzybyte on 2008-05-01
this is a bug in KDE. please see

[http://bugs.kde.org/show_bug.cgi?id=127466](http://bugs.kde.org/show_bug.cgi?id=127466)

and vote it

---

