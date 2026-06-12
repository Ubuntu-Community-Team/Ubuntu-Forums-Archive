---
title: "Plasmashell memory usage rises up but never falls"
date: 2015-04-24
forum: Desktop Environments
---

### Post by craige2 on 2015-04-24
Hello,

as title mentions, plasmashell rises up but doesn't fall. I don't get any error related to this or at all for that matter.

Bellow I will try to describe the problem as thoroughly I can with out giving you headache. 

I have default widget and themes, windows, icons, colour e.t.c 

1)I boot up and log on on with memory: plasmashell 230M and total memory 1.1GB ( everything loads as normal, sys tray loads, kick start response fine, no hangs e.t.c )

2)I start, chromium, firefox, dolphin, amarok, skype. Each one of them contributes around 20-30MB on plasmashell and the normal addition to total memory, around 1.7-1.9GB

3)Now I close chromium, firefox, dolphin, amarok, skype and I give it sometime. 


                                                  Plasmashell doesnt fall. Total memery changes back to normal 1.1GB + the increase amount of plasmashell.


4)I kept doing steps 2-3 resulting in increase of plasmashel memoryusage up to 391M around. Then I stopped, as you can imagine it was a boring procedure. Again the total memory usage was the normal plus the increase of plasmashell.


Plasmashell doesn't fall. Also I noticed that, as I write this post, plasmashell keeps slowly build up. Tried it with kate, while I was writing in, the plasmashell slowly build up.


I google it and found out that plasmashell had a memory leak at a) transmission-qt and b) system notification messaging. I don't use transmission so a) is not an issue.


However about the system notification, I disabled the "Show application and system notifications" and "Track file transfer and other jobs". I only noticed a small decrease of the amount the plasmashell builds up. 


Also, I went on and used my pc as normal, doing what I do regularly and I noticed an increased amount of plasmashell memory. I was working on netbeans, having amarok and chromium and skype on and despite the expected netbeans memory usage, the plasmashell rised to huge amounts, having total memory usage little over 4GB with only 700MB used for netbeans. This is like Microsoft Windows.


This isn't normal right?


Do I have a broken plasmashell, OS installation or is this happening to others?


Any ideas what to do?


Thanks


Specs:-

Hardware:
AMD 6 core 1100TT black edition
2x Radeon HD 6870
GB 990 FXA UD3+
16GB RAM

Software:
Kubuntu 15.04 fresh install
fglrx-update activated
microcode for amd activated
system up to date

Installed software:
Java 8, netbeans, skype, chromium.


Edit 1: I mistakenly wrote K instead of MB. The amount increased is in MB
Edit 2: I kept doing test and I noticed, every single action I perform adds 20-30 MB. Like, I close chromium, firefox tab, plasmashell gets 20-30MB, I open dolphin, same, I close dolphin without doing anything, another 20-30MB gain, same happens with any application installed.
Edit 3: When memory is getting high, i reboot and its back to normal. I will try to switch memory cards to rule out hardware issue.

---

### Post by dino99 on 2015-04-25
i've already seen similar comments from other users using that recent plasmashell. It is nice but quite heavy and seems needing some more devs attention

---

### Post by alikazmi-2040 on 2015-05-25
Bump

Plasmashell is using 631.1 MB RAM privately with a further 67.3 MB shared with other programs. I don't think this is normal behaviour, is it?

---

### Post by Vladlenin5000 on 2015-05-25
It shouldn't be. Like dino99 already said it needs some love from the devs.

---

### Post by alikazmi-2040 on 2015-05-26
A possible workaround for now (that seems to work) is run 'killall plasmashell' followed by 'plasmashell' through krunner (alt+F2).

Memory usage for plasmashell went down to ~300 MB from ~650 MB after this. Netbeans, Firefox and Kate happily kept running without any apparent effects and windows retained their positions and sizes on their respective monitors.

Also, just opening and closing kicker a couple of times results in plasmashell consuming a few extra megabytes which never get unallocated (I guess it's something to do with garbage collection).

---

### Post by craige2 on 2015-05-27
Yeap what alikazmi-2040 said solves it temporarily. Restarting it, brings it down. 

Another workaround I found, is to delete the default panel. Completely. Without default panel, or any panel at all, plasmshell runs on ~80MB memory. No increases, no jumps on usuage.

Alt+F2 to run programs e.t.c. Any messages, like email received, chat message etc will be shown messed up in top center of screen.

However you are left with no panels at all.

I tried to use a dock station, tried a couple of them, like cairo etc. All of them seems to bug, crash, messed up, which makes me think that is caused by plasmashell's issues.

I think the systray and indexing bug is still alive, even if it's been reported a couple of years ago.

Definitely the systray/search indexing/etc needs some crazy love from devs.

---

### Post by zaoka on 2015-06-25
Anybody resolved this problem?

I have Kubuntu 15.04 where SystemLoad Widget reporting full emmory usage while SystemMonitor does not.

After system restart memory usage is OK for some time, after a while it becomes full even though I close all active apps ...


??

---

### Post by alikazmi-2040 on 2015-06-26
> **zaoka said:**
> Anybody resolved this problem?

I have Kubuntu 15.04 where SystemLoad Widget reporting full emmory usage while SystemMonitor does not.

After system restart memory usage is OK for some time, after a while it becomes full even though I close all active apps ...


??

Can you report the process(es) that are consuming the most ram by pressing 'Ctrl + Esc' to bring up the System Activity app along with the total amount of RAM and the processor architecture (32bit or 64bit)?

---

### Post by zaoka on 2015-07-01
Here is hte screenshoot...

---

