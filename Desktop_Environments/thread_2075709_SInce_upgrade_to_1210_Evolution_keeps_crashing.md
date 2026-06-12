---
title: "SInce upgrade to 12:10 Evolution keeps crashing"
date: 2012-10-24
forum: Desktop Environments
---

### Post by Jonners59 on 2012-10-24
Since upgrade to 12:10 from 12:04 Evolution keeps crashing.  I had this issue with 12:04 and fixed it by purging and reinstalling.  I followed the same steps, but this time it does not work.  I also find an issue with auto-signatures.

I have about 5 accounts I manage in my client.  One is my Default.  I have set different auto-signatures for each account.  When I create a message it adds the correct auto-signature, BUT also adds the default signature too.  I have disabled the auto-signature in the Default account and it has stopped happening, but I do not now have an auto-signature in the main account, I have to add it manually.

Any ideas, please?

---

### Post by jquirk on 2012-11-11
I'm running 32 bit Ubuntu  and I'm having the same problem. I haven't tried the remove and purge yet bit but give it a go to see what happens.

---

### Post by Jonners59 on 2012-11-12
I found doing the "purge"  process I have - detailed below, did noting.  As soon as I opened it up/reinstalled, it just started up with the same configs. 

No one is coming in to help either.  Poor show by the experts, unless this is in the wrong place.

---

### Post by Bucky Ball on 2012-11-12
I upgraded the wife's computer to 12.04 a few months ago and she won't go there because Evolution has been totally problematic. Will try the purge and reinstall, but hey devs, just cos Thunderbird is now the default there's no reason to treat Ev like a second class email client. That seems to be what's happened.

---

### Post by Jonners59 on 2012-11-12
> **Bucky Ball said:**
> I upgraded the wife's computer to 12.04 a few months ago and she won't go there because Evolution has been totally problematic. Will try the purge and reinstall, but hey devs, just cos Thunderbird is now the default there's no reason to treat Ev like a second class email client. That seems to be what's happened.
Yes, I agree.  I'll be honest, although I have used a number of clients on Ubuntu, including Thunderbird, I have to say I do not think any of them match MS Outlook for all its faults, and IF I could get it going on Ubuntu, then that is what I would use, no doubt.

That said of ALL the Ubuntu clients, I still think Evolution is the best, but since the 10:04 upgrade when they changed the way Evolution works, those not building from scratch, but upgrading have huge issues.  The diary and contacts issues have been fixed, but the eMail is not good.  I think the problems seem to occur with those that rely on eMail a lot and have large "data basses".  I run 5 accounts and they are over 2Gb each.  It seems to hang on the sync/retrieve messages.

I hope they fix this, and soon, or show me how to remove every trace of Evolution so I can try a re-install from fresh.

---

### Post by swissinvestor on 2012-11-12
I can confirm the crashes as well. It crashes on both an upgrade from 12.04 to 12.10 and on a fresh install.

I notice that before crashing it hangs when downloading mail. I have a substantial number of accounts and a sizeable amount of mails, but so far no clue what causes this.

Ubuntu 12.10 64-bit

---

### Post by jquirk on 2012-11-15
I had disabled the global menus and this is when it really went unstable on me - I restored the menus back to default and seems happier but again this is the 32 bit version.
I do run a 64 bit version of Ubuntu but not a desktop version so can't comment on the stability of Evolution on my other system.

---

### Post by Jonners59 on 2012-11-16
Seems it is common place.  My wife's laptop which was installed from new and is also 64-bit is fine bar the auto signature doubles, i.e. it goes in messages twice, one above the other, which I also get on my machine.

Also note that it hangs when synchronizing...  Not all the time, just  when it has a number of folders to synchronise.  I have to kill it and  reboot, which is not good.

---

### Post by Jonners59 on 2012-12-03
I have been running bugging and backtrace info...

[COLOR=#222222][FONT=arial]Commands I used were:[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Start the program under control of gdb:
[/FONT][/COLOR][COLOR=#222222][FONT=arial]```
gdb evolution 2>&1 | tee ~/gdb-evolution.txt
```[/FONT][/COLOR][COLOR=#222222][FONT=arial][COLOR=#222222][FONT=arial]
[/FONT][/COLOR][/FONT][/COLOR][COLOR=#222222][FONT=arial]```
(gdb) handle SIG33 pass nostop noprint
```[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]```
(gdb) set pagination 0
```[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]```
(gdb) run
```[/FONT][/COLOR][COLOR=#222222][FONT=arial][COLOR=#222222][FONT=arial][COLOR=#222222][FONT=arial]

[/FONT][/COLOR][/FONT][/COLOR]The program will start. Perform any actions necessary to reproduce the crash. If the program hangs but doesn't crash you can press ctrl+c in gdb while the program is frozen and then continue with the next step.

Retrieve a backtrace:
[/FONT][/COLOR][COLOR=#222222][FONT=arial]```
(gdb) backtrace full
```[/FONT][/COLOR][COLOR=#222222][FONT=arial][COLOR=#222222][FONT=arial]
[/FONT][/COLOR][/FONT][/COLOR][COLOR=#222222][FONT=arial]```
(gdb) info registers
```[/FONT][/COLOR][COLOR=#222222][FONT=arial][COLOR=#222222][FONT=arial]
[/FONT][/COLOR][/FONT][/COLOR][COLOR=#222222][FONT=arial]```
(gdb) x/16i $pc
```[/FONT][/COLOR][COLOR=#222222][FONT=arial][COLOR=#222222][FONT=arial]
[/FONT][/COLOR][/FONT][/COLOR][COLOR=#222222][FONT=arial]```
(gdb) thread apply all backtrace
```[/FONT][/COLOR][COLOR=#222222][FONT=arial][COLOR=#222222][FONT=arial]
[/FONT][/COLOR][/FONT][/COLOR][COLOR=#222222][FONT=arial]```
(gdb) quit
```[/FONT][/COLOR]

Output enclosed....

---

### Post by t.h.w. on 2013-01-16
Xubuntu/Ubuntu 64-bit fresh install.... Same problem. Will not start/import the backup from my old 32-bit compu. Keeps on crashing.

To make things worse: Since 12.04 the mail-folders are in a 'new way' stored so importing to Thunderbird is not as easy as it was, or not possible.

I have tried to doing it via the mbox-way, but when saving my 'inbox' as a mbox-file, the file grows and grows and grows..... I stopped the process it of when it was grown to 13GB (!!) and it was only at 4% !!!  :shock: Help.

I now can think of just one other solution: Install a 32-bit system in my brand new Corei5.... but that is not what I bought it for.... :roll:


**Off-topic solution**:
I switched to Thunderbird.
This was a hassle too, but with the right pythonscript foud through his site [http://askubuntu.com/questions/66969/how-to-port-email-from-evolution-to-thunderbird](http://askubuntu.com/questions/66969/how-to-port-email-from-evolution-to-thunderbird) I managed to transform the maildirectory to mbox format. Afer some tinkering I managed to get everything in Thnderbird.

---

### Post by t.h.w. on 2013-02-28
Hi,
Don' like Thunderbird, so I gave Evolution 3.6.2 another go. (I have a 64-bit Xubuntu 21.10 machine.) After initial install and importing the backup file from my 32-bit Ubuntu machine Evoluin wnts to import the backup again. I ignored he second 'attempt' of Evlution to import the backup and that was what got me into the program. Hurray... 

But wait. Now Eolution keeps crashing when not actively used for some time. ANyone ith the same issue and  solution/upgrade?

How can I tell if I am using Evolution 64-bit instead of Evolution 32-bit? Or is this only a system-issue? (Dumb question??)

Thanks!

---

### Post by Jonners59 on 2013-03-01
t.h.w
Agree with your Unity quote!  Me too.

As for the problems that is one of them.  I had that and fixed it myself.  I'll see if I can find what I did.  For me Evolution went bad when it moved to it's new backend way of working, if I recall at c10.04.  There are many "bugs", some have been resolved in releases (not forum) like the auto signature,  calendar and contacts issues, but others like the "reply" not always including the full history and taking the first character of the following line and adding it to the end of the preceding, then crashing when doing replies, and freezing, I believe when synchronizing.  These are on going and i have tried through this forum and the Evolution forum to get help, but no one responds or looks at the logs supplied.

It's a waiting game.  Sadly it's the best client for eMail on Ubuntu, so there is no alternative but to wait.

Here is the thread I created at the time and how I fixed the problem...
[http://ubuntuforums.org/showthread.php?t=1939948](http://ubuntuforums.org/showthread.php?t=1939948)

---

### Post by Jonners59 on 2013-05-10
Still not fixed.  Evolution still freezes.  Log attached.
[PHP]GNU gdb (GDB) 7.5-ubuntu
Copyright (C) 2012 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /usr/bin/evolution...(no debugging symbols found)...done.
(gdb) handle SIG33 pass nostop noprint
Signal        Stop    Print    Pass to program    Description
SIG33         No    No    Yes        Real-time event 33
(gdb) set pagination 0
(gdb) run
Starting program: /usr/bin/evolution 
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
[New Thread 0x7fffe00f0700 (LWP 28121)]
[New Thread 0x7fffde449700 (LWP 28122)]
[New Thread 0x7fffdda3d700 (LWP 28123)]
[New Thread 0x7fffdd23c700 (LWP 28124)]
[New Thread 0x7fffba1e4700 (LWP 28133)]
[New Thread 0x7fffb99e3700 (LWP 28171)]
[New Thread 0x7fffb91e2700 (LWP 28172)]
[New Thread 0x7fffb89e1700 (LWP 28173)]
[New Thread 0x7fffabfff700 (LWP 28174)]
[New Thread 0x7fffab7fe700 (LWP 28175)]
[New Thread 0x7fffaaffd700 (LWP 28176)]
[New Thread 0x7fffaa3f1700 (LWP 28177)]
[New Thread 0x7fffa9bf0700 (LWP 28178)]
[New Thread 0x7fffa93ef700 (LWP 28179)]
[New Thread 0x7fffa8bee700 (LWP 28190)]
[New Thread 0x7fff8bfff700 (LWP 28191)]
[New Thread 0x7fff8b7fe700 (LWP 28192)]
[New Thread 0x7fff8affd700 (LWP 28193)]
[New Thread 0x7fff8a7fc700 (LWP 28194)]
[New Thread 0x7fff89bcd700 (LWP 28195)]
[New Thread 0x7fff893cc700 (LWP 28196)]

(evolution:28112): e-web-view.c-WARNING **: Disabling webkit plugin: QuickTime Plug-in 7.6.6

(evolution:28112): e-web-view.c-WARNING **: Disabling webkit plugin: Windows Media Player Plug-in 10 (compatible; Totem)

(evolution:28112): e-web-view.c-WARNING **: Disabling webkit plugin: 2007 Microsoft Office system (CrossOver - NPOFF12.DLL)

(evolution:28112): e-web-view.c-WARNING **: Disabling webkit plugin: DivX® Web Player

(evolution:28112): e-web-view.c-WARNING **: Disabling webkit plugin: LibreOffice Plug-in

(evolution:28112): e-web-view.c-WARNING **: Disabling webkit plugin: VLC Multimedia Plugin (compatible Totem 3.4.3)

(evolution:28112): e-web-view.c-WARNING **: Disabling webkit plugin: 2007 Microsoft Office system (CrossOver - NPOFF12.DLL)

(evolution:28112): e-web-view.c-WARNING **: Disabling webkit plugin: DjView-4.9

(evolution:28112): e-web-view.c-WARNING **: Disabling webkit plugin: iTunes Application Detector
[Thread 0x7fffa8bee700 (LWP 28190) exited]
[Thread 0x7fff8a7fc700 (LWP 28194) exited]
[Thread 0x7fff8bfff700 (LWP 28191) exited]
[Thread 0x7fff8affd700 (LWP 28193) exited]
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.
[Thread 0x7fffb99e3700 (LWP 28171) exited]
[Thread 0x7fffa93ef700 (LWP 28179) exited]
[New Thread 0x7fffa93ef700 (LWP 28215)]
[New Thread 0x7fffb99e3700 (LWP 28216)]
[New Thread 0x7fff8affd700 (LWP 28217)]
[New Thread 0x7fff8bfff700 (LWP 28218)]
[New Thread 0x7fff2b0d8700 (LWP 28219)]
[New Thread 0x7fff2a8d7700 (LWP 28220)]
[New Thread 0x7fff2a0d6700 (LWP 28221)]
[New Thread 0x7fff298d5700 (LWP 28222)]
[Thread 0x7fffba1e4700 (LWP 28133) exited]
[Thread 0x7fffa9bf0700 (LWP 28178) exited]
[Thread 0x7fffb89e1700 (LWP 28173) exited]
[Thread 0x7fff298d5700 (LWP 28222) exited]
[Thread 0x7fffb99e3700 (LWP 28216) exited]
[Thread 0x7fff8affd700 (LWP 28217) exited]
[Thread 0x7fff8bfff700 (LWP 28218) exited]

(evolution:28112): Gtk-WARNING **: EAttachmentBar 0x5555569a74a0 is mapped but not visible

(evolution:28112): Gtk-WARNING **: EAttachmentBar 0x5555569a74a0 is mapped but not visible

(evolution:28112): Gtk-WARNING **: EAttachmentBar 0x5555569a74a0 is mapped but visible=0 child_visible=1 parent GtkBox 0x7fff7c038d50 mapped=1

(evolution:28112): Gtk-WARNING **: EAttachmentBar 0x5555569a74a0 is mapped but not visible

(evolution:28112): Gtk-WARNING **: EAttachmentBar 0x5555569a74a0 is mapped but visible=0 child_visible=1 parent GtkBox 0x7fff7c038d50 mapped=1

(evolution:28112): Gtk-WARNING **: EAttachmentBar 0x555555eaeb10 is mapped but not visible

(evolution:28112): Gtk-WARNING **: EAttachmentBar 0x555555eaeb10 is mapped but not visible

(evolution:28112): Gtk-WARNING **: EAttachmentBar 0x555555eaeb10 is mapped but visible=0 child_visible=1 parent GtkBox 0x555557345c30 mapped=1

(evolution:28112): Gtk-WARNING **: EAttachmentBar 0x555555eaeb10 is mapped but not visible

(evolution:28112): Gtk-WARNING **: EAttachmentBar 0x555555eaeb10 is mapped but visible=0 child_visible=1 parent GtkBox 0x555557345c30 mapped=1
[Thread 0x7fffaa3f1700 (LWP 28177) exited]
[Thread 0x7fff2b0d8700 (LWP 28219) exited]
[Thread 0x7fff2a8d7700 (LWP 28220) exited]
[New Thread 0x7fff2a8d7700 (LWP 28302)]
[Thread 0x7fff2a8d7700 (LWP 28302) exited]
[Thread 0x7fffb91e2700 (LWP 28172) exited]
[New Thread 0x7fffb91e2700 (LWP 28461)]
[New Thread 0x7fff2a8d7700 (LWP 28480)]
[New Thread 0x7fff2b0d8700 (LWP 28481)]
[New Thread 0x7fffaa3f1700 (LWP 28482)]
[Thread 0x7fffaa3f1700 (LWP 28482) exited]
[Thread 0x7fff2a8d7700 (LWP 28480) exited]
[New Thread 0x7fff2a8d7700 (LWP 28495)]
[New Thread 0x7fffaa3f1700 (LWP 28496)]
[New Thread 0x7fffa9bf0700 (LWP 28497)]
[New Thread 0x7fff8bfff700 (LWP 28498)]
[New Thread 0x7fff8affd700 (LWP 28499)]
[New Thread 0x7fff298d5700 (LWP 28500)]
[Thread 0x7fff2a8d7700 (LWP 28495) exited]
[Thread 0x7fff298d5700 (LWP 28500) exited]
[Thread 0x7fff8affd700 (LWP 28499) exited]
[Thread 0x7fff8bfff700 (LWP 28498) exited]
[Thread 0x7fffaa3f1700 (LWP 28496) exited]
[New Thread 0x7fffaa3f1700 (LWP 28513)]
[New Thread 0x7fff8bfff700 (LWP 28514)]
[New Thread 0x7fff8affd700 (LWP 28515)]
[Thread 0x7fffaa3f1700 (LWP 28513) exited]
[Thread 0x7fff8affd700 (LWP 28515) exited]
[New Thread 0x7fff8affd700 (LWP 28528)]
[Thread 0x7fff8bfff700 (LWP 28514) exited]
[New Thread 0x7fff8bfff700 (LWP 28542)]
[Thread 0x7fff8affd700 (LWP 28528) exited]
[New Thread 0x7fff8affd700 (LWP 28567)]
[Thread 0x7fff8bfff700 (LWP 28542) exited]
[New Thread 0x7fff8bfff700 (LWP 28568)]
[Thread 0x7fff8affd700 (LWP 28567) exited]
[New Thread 0x7fff8affd700 (LWP 28587)]
[New Thread 0x7fffaa3f1700 (LWP 28594)]
[Thread 0x7fffaa3f1700 (LWP 28594) exited]
[Thread 0x7fff8bfff700 (LWP 28568) exited]
[New Thread 0x7fff8bfff700 (LWP 28625)]
[New Thread 0x7fffaa3f1700 (LWP 28626)]
[New Thread 0x7fff298d5700 (LWP 28627)]
[Thread 0x7fff8affd700 (LWP 28587) exited]
[Thread 0x7fff298d5700 (LWP 28627) exited]
[New Thread 0x7fff298d5700 (LWP 28720)]
[New Thread 0x7fff8affd700 (LWP 28727)]
[Thread 0x7fff8affd700 (LWP 28727) exited]
[Thread 0x7fff298d5700 (LWP 28720) exited]
[New Thread 0x7fff298d5700 (LWP 28770)]
[New Thread 0x7fff8affd700 (LWP 28771)]
[New Thread 0x7fff2a8d7700 (LWP 28814)]
[New Thread 0x7fff290d4700 (LWP 28827)]
[New Thread 0x7fff288d3700 (LWP 28828)]
[Thread 0x7fff290d4700 (LWP 28827) exited]
[Thread 0x7fff288d3700 (LWP 28828) exited]
[New Thread 0x7fff288d3700 (LWP 28859)]
[New Thread 0x7fff290d4700 (LWP 28884)]
[Thread 0x7fff288d3700 (LWP 28859) exited]
[New Thread 0x7fff288d3700 (LWP 28909)]
[New Thread 0x7fff23fff700 (LWP 28910)]
[New Thread 0x7fff237fe700 (LWP 28911)]

(evolution:28112): Gtk-WARNING **: EAttachmentBar 0x5555569a74a0 is mapped but not visible

(evolution:28112): Gtk-WARNING **: EAttachmentBar 0x5555569a74a0 is mapped but not visible

(evolution:28112): Gtk-WARNING **: EAttachmentBar 0x5555569a74a0 is mapped but visible=0 child_visible=1 parent GtkBox 0x7fff7c038ab0 mapped=1

(evolution:28112): Gtk-WARNING **: EAttachmentBar 0x5555569a74a0 is mapped but not visible

(evolution:28112): Gtk-WARNING **: EAttachmentBar 0x5555569a74a0 is mapped but visible=0 child_visible=1 parent GtkBox 0x7fff7c038ab0 mapped=1

(evolution:28112): evolution-mail-WARNING **: Failed to write data to cache stream: Operation was cancelled

(evolution:28112): Gtk-WARNING **: EAttachmentBar 0x555555eaedd0 is mapped but not visible

(evolution:28112): Gtk-WARNING **: EAttachmentBar 0x555555eaedd0 is mapped but not visible

(evolution:28112): Gtk-WARNING **: EAttachmentBar 0x555555eaedd0 is mapped but visible=0 child_visible=1 parent GtkBox 0x7fff7c038ab0 mapped=1

(evolution:28112): Gtk-WARNING **: EAttachmentBar 0x555555eaedd0 is mapped but not visible

(evolution:28112): Gtk-WARNING **: EAttachmentBar 0x555555eaedd0 is mapped but visible=0 child_visible=1 parent GtkBox 0x7fff7c038ab0 mapped=1

(evolution:28112): evolution-mail-WARNING **: Failed to write data to cache stream: Operation was cancelled
[Thread 0x7fff288d3700 (LWP 28909) exited]
[New Thread 0x7fff288d3700 (LWP 28919)]
[Thread 0x7fff23fff700 (LWP 28910) exited]
[New Thread 0x7fff23fff700 (LWP 28938)]
[New Thread 0x7fff22de9700 (LWP 28939)]
[Thread 0x7fff22de9700 (LWP 28939) exited]
[Thread 0x7fff23fff700 (LWP 28938) exited]
[Thread 0x7fff8bfff700 (LWP 28625) exited]

(evolution:28112): evolution-mail-WARNING **: Failed to write data to cache stream: Operation was cancelled

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): camel-WARNING **: Truncated utf8 buffer

(evolution:28112): Gtk-WARNING **: EAttachmentBar 0x5555569a71e0 is mapped but not visible

(evolution:28112): Gtk-WARNING **: EAttachmentBar 0x5555569a71e0 is mapped but not visible

(evolution:28112): Gtk-WARNING **: EAttachmentBar 0x5555569a71e0 is mapped but visible=0 child_visible=1 parent GtkBox 0x7fff9c03ecd0 mapped=1

(evolution:28112): Gtk-WARNING **: EAttachmentBar 0x5555569a71e0 is mapped but not visible

(evolution:28112): Gtk-WARNING **: EAttachmentBar 0x5555569a71e0 is mapped but visible=0 child_visible=1 parent GtkBox 0x7fff9c03ecd0 mapped=1
[Thread 0x7fff237fe700 (LWP 28911) exited]
[Thread 0x7fffab7fe700 (LWP 28175) exited]
[Thread 0x7fffaa3f1700 (LWP 28626) exited]
[Thread 0x7fff8affd700 (LWP 28771) exited]
[Thread 0x7fff288d3700 (LWP 28919) exited]
[Thread 0x7fffabfff700 (LWP 28174) exited]
[New Thread 0x7fffabfff700 (LWP 29004)]
[Thread 0x7fff2a8d7700 (LWP 28814) exited]
[Thread 0x7fffabfff700 (LWP 29004) exited]
[New Thread 0x7fffabfff700 (LWP 29023)]
[New Thread 0x7fff2a8d7700 (LWP 29024)]
[New Thread 0x7fff288d3700 (LWP 29025)]
[New Thread 0x7fff8affd700 (LWP 29032)]
[New Thread 0x7fffab7fe700 (LWP 29033)]
[Thread 0x7fff288d3700 (LWP 29025) exited]
[Thread 0x7fffab7fe700 (LWP 29033) exited]
[New Thread 0x7fffab7fe700 (LWP 29052)]
[New Thread 0x7fff288d3700 (LWP 29053)]
[Thread 0x7fffab7fe700 (LWP 29052) exited]
[Thread 0x7fff288d3700 (LWP 29053) exited]
[New Thread 0x7fff288d3700 (LWP 29078)]
[Thread 0x7fff288d3700 (LWP 29078) exited]
[New Thread 0x7fff288d3700 (LWP 29141)]
[New Thread 0x7fffab7fe700 (LWP 29142)]
[Thread 0x7fff8affd700 (LWP 29032) exited]
[New Thread 0x7fff8affd700 (LWP 29173)]
[New Thread 0x7fffaa3f1700 (LWP 29174)]
[Thread 0x7fff8affd700 (LWP 29173) exited]
[Thread 0x7fffaa3f1700 (LWP 29174) exited]
[New Thread 0x7fffaa3f1700 (LWP 29187)]
[New Thread 0x7fff8affd700 (LWP 29188)]

(evolution:28112): e-web-view.c-WARNING **: Disabling webkit plugin: QuickTime Plug-in 7.6.6

(evolution:28112): e-web-view.c-WARNING **: Disabling webkit plugin: Windows Media Player Plug-in 10 (compatible; Totem)

(evolution:28112): e-web-view.c-WARNING **: Disabling webkit plugin: 2007 Microsoft Office system (CrossOver - NPOFF12.DLL)

(evolution:28112): e-web-view.c-WARNING **: Disabling webkit plugin: DivX® Web Player

(evolution:28112): e-web-view.c-WARNING **: Disabling webkit plugin: LibreOffice Plug-in

(evolution:28112): e-web-view.c-WARNING **: Disabling webkit plugin: VLC Multimedia Plugin (compatible Totem 3.4.3)

(evolution:28112): e-web-view.c-WARNING **: Disabling webkit plugin: 2007 Microsoft Office system (CrossOver - NPOFF12.DLL)

(evolution:28112): e-web-view.c-WARNING **: Disabling webkit plugin: DjView-4.9

(evolution:28112): e-web-view.c-WARNING **: Disabling webkit plugin: iTunes Application Detector

(evolution:28112): e-web-view.c-WARNING **: Disabling webkit plugin: QuickTime Plug-in 7.6.6

(evolution:28112): e-web-view.c-WARNING **: Disabling webkit plugin: Windows Media Player Plug-in 10 (compatible; Totem)

(evolution:28112): e-web-view.c-WARNING **: Disabling webkit plugin: 2007 Microsoft Office system (CrossOver - NPOFF12.DLL)

(evolution:28112): e-web-view.c-WARNING **: Disabling webkit plugin: DivX® Web Player

(evolution:28112): e-web-view.c-WARNING **: Disabling webkit plugin: LibreOffice Plug-in

(evolution:28112): e-web-view.c-WARNING **: Disabling webkit plugin: VLC Multimedia Plugin (compatible Totem 3.4.3)

(evolution:28112): e-web-view.c-WARNING **: Disabling webkit plugin: 2007 Microsoft Office system (CrossOver - NPOFF12.DLL)

(evolution:28112): e-web-view.c-WARNING **: Disabling webkit plugin: DjView-4.9

(evolution:28112): e-web-view.c-WARNING **: Disabling webkit plugin: iTunes Application Detector
[Thread 0x7fffaa3f1700 (LWP 29187) exited]
[New Thread 0x7fffaa3f1700 (LWP 29213)]
[Thread 0x7fffabfff700 (LWP 29023) exited]
[Thread 0x7fff298d5700 (LWP 28770) exited]
[New Thread 0x7fff298d5700 (LWP 29233)]
[New Thread 0x7fffabfff700 (LWP 29234)]
[Thread 0x7fff8affd700 (LWP 29188) exited]
[Thread 0x7fff288d3700 (LWP 29141) exited]
[New Thread 0x7fff288d3700 (LWP 30148)]
[Thread 0x7fff288d3700 (LWP 30148) exited]
[Thread 0x7fffaaffd700 (LWP 28176) exited]
[Thread 0x7fffabfff700 (LWP 29234) exited]
[New Thread 0x7fffabfff700 (LWP 31913)]
[Thread 0x7fffabfff700 (LWP 31913) exited]

Program received signal SIGINT, Interrupt.
0x00007ffff4293bc1 in g_mutex_get_impl (mutex=0x7ffff45051a0 <g__quark_global_lock>) at /build/buildd/glib2.0-2.34.1/./glib/gthread-posix.c:130
130    /build/buildd/glib2.0-2.34.1/./glib/gthread-posix.c: No such file or directory.
(gdb) backtrace full
#0  0x00007ffff4293bc1 in g_mutex_get_impl (mutex=0x7ffff45051a0 <g__quark_global_lock>) at /build/buildd/glib2.0-2.34.1/./glib/gthread-posix.c:130
        impl = 0x55555575d820
#1  0x00007ffff4293e19 in g_mutex_lock (mutex=mutex@entry=0x7ffff45051a0 <g__quark_global_lock>) at /build/buildd/glib2.0-2.34.1/./glib/gthread-posix.c:208
        _g_boolean_var_ = <optimised out>
        status = <optimised out>
#2  0x00007ffff426552b in g_quark_from_string (string=0x55555576dee6 "horizontal") at /build/buildd/glib2.0-2.34.1/./glib/gquark.c:203
        quark = 1480824272
#3  0x00007ffff4d77f4b in gtk_widget_path_iter_add_class () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#4  0x00007ffff4d73f55 in gtk_widget_path_append_for_widget () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#5  0x00007ffff4ba1b07 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#6  0x00007ffff4bfee07 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#7  0x00007ffff4ba6aff in gtk_container_get_path_for_child () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#8  0x00007ffff4b606a1 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#9  0x00007ffff4ba6aff in gtk_container_get_path_for_child () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#10 0x00007ffff4cbfc3e in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#11 0x00007ffff4cbfd27 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#12 0x00007ffff4cc0478 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#13 0x00007ffff4cc1f05 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#14 0x00007ffff4cc2062 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#15 0x00007ffff4cc2062 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#16 0x00007ffff4cc2062 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#17 0x00007ffff4cc2062 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#18 0x00007ffff4cc2062 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#19 0x00007ffff4cc2062 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#20 0x00007ffff4cc2062 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#21 0x00007ffff4cc2062 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#22 0x00007ffff4ba4e7e in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#23 0x00007ffff2ea9dd0 in ?? () from /usr/lib/x86_64-linux-gnu/libgdk-3.so.0
No symbol table info available.
#24 0x00007ffff4256ab5 in g_main_dispatch (context=0x555555792710) at /build/buildd/glib2.0-2.34.1/./glib/gmain.c:2715
        dispatch = 0x7ffff4253e60 <g_idle_dispatch>
        was_in_call = 0
        user_data = 0x7fff95d76cc0
        callback = 0x7ffff2ea9da0
        cb_funcs = 0x7ffff45049e0 <g_source_callback_funcs>
        cb_data = 0x555558132210
        current_source_link = {data = 0x5555571c9d00, next = 0x0}
        need_destroy = <optimised out>
        source = 0x5555571c9d00
        current = 0x5555557e1020
        i = <optimised out>
#25 g_main_context_dispatch (context=context@entry=0x555555792710) at /build/buildd/glib2.0-2.34.1/./glib/gmain.c:3219
No locals.
#26 0x00007ffff4256de8 in g_main_context_iterate (context=0x555555792710, block=block@entry=1, dispatch=dispatch@entry=1, self=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gmain.c:3290
        max_priority = 110
        timeout = 0
        some_ready = 1
        nfds = <optimised out>
        allocated_nfds = <optimised out>
        fds = 0x55555674b9c0
#27 0x00007ffff42571e2 in g_main_loop_run (loop=0x555555c555e0) at /build/buildd/glib2.0-2.34.1/./glib/gmain.c:3484
        __PRETTY_FUNCTION__ = "g_main_loop_run"
#28 0x00007ffff4c379b5 in gtk_main () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#29 0x0000555555557269 in main ()
No symbol table info available.
(gdb) info registers
rax            0x55555575d820    93824994367520
rbx            0x55555575d820    93824994367520
rcx            0x5555577d3530    93825028404528
rdx            0x55555576dee6    93824994434790
rsi            0x7    7
rdi            0x7ffff45051a0    140737292292512
rbp            0x7ffff45051a0    0x7ffff45051a0 <g__quark_global_lock>
rsp            0x7fffffffd6a0    0x7fffffffd6a0
r8             0x0    0
r9             0x20    32
r10            0x0    0
r11            0x7ffff3db6510    140737284629776
r12            0x555557b9d680    93825032377984
r13            0x555557b01560    93825031738720
r14            0x1    1
r15            0x555557ea7a20    93825035565600
rip            0x7ffff4293bc1    0x7ffff4293bc1 <g_mutex_get_impl+33>
eflags         0x202    [ IF ]
cs             0x33    51
ss             0x2b    43
ds             0x0    0
es             0x0    0
fs             0x0    0
gs             0x0    0
(gdb) x/16i $pc
=> 0x7ffff4293bc1 <g_mutex_get_impl+33>:    mov    0x8(%rsp),%rbp
   0x7ffff4293bc6 <g_mutex_get_impl+38>:    mov    (%rsp),%rbx
   0x7ffff4293bca <g_mutex_get_impl+42>:    mov    0x10(%rsp),%r12
   0x7ffff4293bcf <g_mutex_get_impl+47>:    add    $0x18,%rsp
   0x7ffff4293bd3 <g_mutex_get_impl+51>:    retq   
   0x7ffff4293bd4 <g_mutex_get_impl+52>:    nopl   0x0(%rax)
   0x7ffff4293bd8 <g_mutex_get_impl+56>:    callq  0x7ffff4293b00 <g_mutex_impl_new>
   0x7ffff4293bdd <g_mutex_get_impl+61>:    mov    %rax,%r12
   0x7ffff4293be0 <g_mutex_get_impl+64>:    mov    %rbx,%rax
   0x7ffff4293be3 <g_mutex_get_impl+67>:    lock cmpxchg %r12,0x0(%rbp)
   0x7ffff4293be9 <g_mutex_get_impl+73>:    jne    0x7ffff4293bf1 <g_mutex_get_impl+81>
   0x7ffff4293beb <g_mutex_get_impl+75>:    mov    0x0(%rbp),%rbx
   0x7ffff4293bef <g_mutex_get_impl+79>:    jmp    0x7ffff4293bbe <g_mutex_get_impl+30>
   0x7ffff4293bf1 <g_mutex_get_impl+81>:    mov    %r12,%rdi
   0x7ffff4293bf4 <g_mutex_get_impl+84>:    callq  0x7ffff4228560 <pthread_mutex_destroy@plt>
   0x7ffff4293bf9 <g_mutex_get_impl+89>:    mov    %r12,%rdi
(gdb) thread apply all backtrace

Thread 85 (Thread 0x7fff298d5700 (LWP 29233)):
#0  0x00007ffff400089c in __lll_lock_wait () from /lib/x86_64-linux-gnu/libpthread.so.0
#1  0x00007ffff3ffc09b in _L_lock_1006 () from /lib/x86_64-linux-gnu/libpthread.so.0
#2  0x00007ffff3ffc01c in pthread_mutex_lock () from /lib/x86_64-linux-gnu/libpthread.so.0
#3  0x00007ffff4293e21 in g_mutex_lock (mutex=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gthread-posix.c:208
#4  0x00007fffcf2c5631 in em_utils_contact_photo () from /usr/lib/evolution/3.6/libemail-engine.so.0
#5  0x00007fffcf74f6de in ?? () from /usr/lib/evolution/3.6/libevolution-mail.so.0
#6  0x00007ffff47c3e3e in run_in_thread (job=<optimised out>, c=0x555557743e60, _data=0x5555573f2160) at /build/buildd/glib2.0-2.34.1/./gio/gsimpleasyncresult.c:869
#7  0x00007ffff47b2236 in io_job_thread (data=0x5555575ce1b0, user_data=<optimised out>) at /build/buildd/glib2.0-2.34.1/./gio/gioscheduler.c:162
#8  0x00007ffff427ae62 in g_thread_pool_thread_proxy (data=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gthreadpool.c:309
#9  0x00007ffff427a645 in g_thread_proxy (data=0x55555786e540) at /build/buildd/glib2.0-2.34.1/./glib/gthread.c:797
#10 0x00007ffff3ff9e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#11 0x00007ffff3d26cbd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#12 0x0000000000000000 in ?? ()

Thread 84 (Thread 0x7fffaa3f1700 (LWP 29213)):
#0  0x00007ffff400089c in __lll_lock_wait () from /lib/x86_64-linux-gnu/libpthread.so.0
#1  0x00007ffff3ffc09b in _L_lock_1006 () from /lib/x86_64-linux-gnu/libpthread.so.0
#2  0x00007ffff3ffc01c in pthread_mutex_lock () from /lib/x86_64-linux-gnu/libpthread.so.0
#3  0x00007ffff4293e21 in g_mutex_lock (mutex=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gthread-posix.c:208
#4  0x00007fffcf2c46b8 in ?? () from /usr/lib/evolution/3.6/libemail-engine.so.0
#5  0x00007fffcf2c5572 in em_utils_in_addressbook () from /usr/lib/evolution/3.6/libemail-engine.so.0
#6  0x00007fffcf2c0b56 in ?? () from /usr/lib/evolution/3.6/libemail-engine.so.0
#7  0x00007ffff6d0cc91 in junk_test (f=0x7fff840084d0, argc=<optimised out>, argv=<optimised out>, fms=0x7fffaa3f09b0) at camel-filter-search.c:867
#8  0x00007ffff6d602b0 in camel_sexp_term_eval (sexp=0x7fff840084d0, sexp@entry=0x7fff24004978, term=0x7fffa0006af0, term@entry=0x35) at camel-sexp.c:812
#9  0x00007ffff6d6156d in camel_sexp_eval (sexp=sexp@entry=0x7fff840084d0) at camel-sexp.c:1730
#10 0x00007ffff6d0dda6 in camel_filter_search_match (session=<optimised out>, get_message=get_message@entry=0x7ffff6d09930 <get_message_cb>, data=data@entry=0x7fffaa3f0a60, info=<optimised out>, source=source@entry=0x555556292cb0 "1350248931.8773.2@chiara-laptop", expression=0x555557717720 "(junk-test)", error=0x555557711ae8) at camel-filter-search.c:954
#11 0x00007ffff6d0ba6e in camel_filter_driver_filter_message (driver=0x5555577119d0, message=<optimised out>, message@entry=0x0, info=info@entry=0x7fff95d17960, uid=0x7fffb4147030 "25098", uid@entry=0x55555786fca0 "25098", source=0x7fff9479a980, store_uid=store_uid@entry=0x555556292cb0 "1350248931.8773.2@chiara-laptop", original_store_uid=original_store_uid@entry=0x555556292cb0 "1350248931.8773.2@chiara-laptop", cancellable=cancellable@entry=0x5555575e0240, error=error@entry=0x7fffaa3f0b48) at camel-filter-driver.c:1733
#12 0x00007ffff6d20c2d in folder_filter (session=<optimised out>, cancellable=0x5555575e0240, data=0x555557814b20, error=0x7fffaa3f0b48) at camel-folder.c:380
#13 0x00007ffff6d5b18c in session_do_job_cb (simple=0x7fff946f9d60, session=0x555555912300, cancellable=0x5555575e0240) at camel-session.c:175
#14 0x00007ffff47c3e3e in run_in_thread (job=<optimised out>, c=0x5555575e0240, _data=0x5555575eb1a0) at /build/buildd/glib2.0-2.34.1/./gio/gsimpleasyncresult.c:869
#15 0x00007ffff47b2236 in io_job_thread (data=0x555556fb1520, user_data=<optimised out>) at /build/buildd/glib2.0-2.34.1/./gio/gioscheduler.c:162
#16 0x00007ffff427ae62 in g_thread_pool_thread_proxy (data=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gthreadpool.c:309
#17 0x00007ffff427a645 in g_thread_proxy (data=0x555557651140) at /build/buildd/glib2.0-2.34.1/./glib/gthread.c:797
#18 0x00007ffff3ff9e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#19 0x00007ffff3d26cbd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#20 0x0000000000000000 in ?? ()

Thread 79 (Thread 0x7fffab7fe700 (LWP 29142)):
#0  0x00007ffff400089c in __lll_lock_wait () from /lib/x86_64-linux-gnu/libpthread.so.0
#1  0x00007ffff3ffc09b in _L_lock_1006 () from /lib/x86_64-linux-gnu/libpthread.so.0
#2  0x00007ffff3ffc01c in pthread_mutex_lock () from /lib/x86_64-linux-gnu/libpthread.so.0
#3  0x00007ffff4293e21 in g_mutex_lock (mutex=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gthread-posix.c:208
#4  0x00007fffcf2c5631 in em_utils_contact_photo () from /usr/lib/evolution/3.6/libemail-engine.so.0
#5  0x00007fffcf74f6de in ?? () from /usr/lib/evolution/3.6/libevolution-mail.so.0
#6  0x00007ffff47c3e3e in run_in_thread (job=<optimised out>, c=0x5555577f7790, _data=0x55555775c7e0) at /build/buildd/glib2.0-2.34.1/./gio/gsimpleasyncresult.c:869
#7  0x00007ffff47b2236 in io_job_thread (data=0x555557100610, user_data=<optimised out>) at /build/buildd/glib2.0-2.34.1/./gio/gioscheduler.c:162
#8  0x00007ffff427ae62 in g_thread_pool_thread_proxy (data=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gthreadpool.c:309
#9  0x00007ffff427a645 in g_thread_proxy (data=0x5555577ea400) at /build/buildd/glib2.0-2.34.1/./glib/gthread.c:797
#10 0x00007ffff3ff9e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#11 0x00007ffff3d26cbd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#12 0x0000000000000000 in ?? ()

Thread 71 (Thread 0x7fff2a8d7700 (LWP 29024)):
#0  0x00007ffff400089c in __lll_lock_wait () from /lib/x86_64-linux-gnu/libpthread.so.0
#1  0x00007ffff3ffc09b in _L_lock_1006 () from /lib/x86_64-linux-gnu/libpthread.so.0
#2  0x00007ffff3ffc01c in pthread_mutex_lock () from /lib/x86_64-linux-gnu/libpthread.so.0
#3  0x00007ffff4293e21 in g_mutex_lock (mutex=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gthread-posix.c:208
#4  0x00007fffcf2c5631 in em_utils_contact_photo () from /usr/lib/evolution/3.6/libemail-engine.so.0
#5  0x00007fffcf74f6de in ?? () from /usr/lib/evolution/3.6/libevolution-mail.so.0
#6  0x00007ffff47c3e3e in run_in_thread (job=<optimised out>, c=0x55555778b390, _data=0x555556c39850) at /build/buildd/glib2.0-2.34.1/./gio/gsimpleasyncresult.c:869
#7  0x00007ffff47b2236 in io_job_thread (data=0x55555725d3b0, user_data=<optimised out>) at /build/buildd/glib2.0-2.34.1/./gio/gioscheduler.c:162
#8  0x00007ffff427ae62 in g_thread_pool_thread_proxy (data=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gthreadpool.c:309
#9  0x00007ffff427a645 in g_thread_proxy (data=0x5555575c5cf0) at /build/buildd/glib2.0-2.34.1/./glib/gthread.c:797
#10 0x00007ffff3ff9e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#11 0x00007ffff3d26cbd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#12 0x0000000000000000 in ?? ()

Thread 62 (Thread 0x7fff290d4700 (LWP 28884)):
#0  0x00007ffff400089c in __lll_lock_wait () from /lib/x86_64-linux-gnu/libpthread.so.0
#1  0x00007ffff3ffc09b in _L_lock_1006 () from /lib/x86_64-linux-gnu/libpthread.so.0
#2  0x00007ffff3ffc01c in pthread_mutex_lock () from /lib/x86_64-linux-gnu/libpthread.so.0
#3  0x00007ffff4293e21 in g_mutex_lock (mutex=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gthread-posix.c:208
#4  0x00007fffcf2c46b8 in ?? () from /usr/lib/evolution/3.6/libemail-engine.so.0
#5  0x00007fffcf2c5572 in em_utils_in_addressbook () from /usr/lib/evolution/3.6/libemail-engine.so.0
#6  0x00007fffcf2c0b56 in ?? () from /usr/lib/evolution/3.6/libemail-engine.so.0
#7  0x00007ffff6d0cc91 in junk_test (f=0x7fffa057de10, argc=<optimised out>, argv=<optimised out>, fms=0x7fff290d39b0) at camel-filter-search.c:867
#8  0x00007ffff6d602b0 in camel_sexp_term_eval (sexp=0x7fffa057de10, sexp@entry=0x7fff24004978, term=0x7fff9004db30, term@entry=0x35) at camel-sexp.c:812
#9  0x00007ffff6d6156d in camel_sexp_eval (sexp=sexp@entry=0x7fffa057de10) at camel-sexp.c:1730
#10 0x00007ffff6d0dda6 in camel_filter_search_match (session=<optimised out>, get_message=get_message@entry=0x7ffff6d09930 <get_message_cb>, data=data@entry=0x7fff290d3a60, info=<optimised out>, source=source@entry=0x555555ccb830 "1352476495.28161.6@baronipc", expression=0x5555576c1ed0 "(junk-test)", error=0x55555715e888) at camel-filter-search.c:954
#11 0x00007ffff6d0ba6e in camel_filter_driver_filter_message (driver=0x55555715e770, message=<optimised out>, message@entry=0x0, info=info@entry=0x7fffa45e2630, uid=0x7fffa449af50 "1722", uid@entry=0x555557785b90 "1722", source=0x7fffa03d8b40, store_uid=store_uid@entry=0x555555ccb830 "1352476495.28161.6@baronipc", original_store_uid=original_store_uid@entry=0x555555ccb830 "1352476495.28161.6@baronipc", cancellable=cancellable@entry=0x555557764460, error=error@entry=0x7fff290d3b48) at camel-filter-driver.c:1733
#12 0x00007ffff6d20c2d in folder_filter (session=<optimised out>, cancellable=0x555557764460, data=0x555557746390, error=0x7fff290d3b48) at camel-folder.c:380
#13 0x00007ffff6d5b18c in session_do_job_cb (simple=0x7fff946f9f20, session=0x555555912300, cancellable=0x555557764460) at camel-session.c:175
#14 0x00007ffff47c3e3e in run_in_thread (job=<optimised out>, c=0x555557764460, _data=0x5555575fbbb0) at /build/buildd/glib2.0-2.34.1/./gio/gsimpleasyncresult.c:869
#15 0x00007ffff47b2236 in io_job_thread (data=0x5555576c1590, user_data=<optimised out>) at /build/buildd/glib2.0-2.34.1/./gio/gioscheduler.c:162
#16 0x00007ffff427ae62 in g_thread_pool_thread_proxy (data=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gthreadpool.c:309
#17 0x00007ffff427a645 in g_thread_proxy (data=0x5555576298a0) at /build/buildd/glib2.0-2.34.1/./glib/gthread.c:797
#18 0x00007ffff3ff9e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#19 0x00007ffff3d26cbd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#20 0x0000000000000000 in ?? ()

Thread 38 (Thread 0x7fffa9bf0700 (LWP 28497)):
#0  0x00007ffff400089c in __lll_lock_wait () from /lib/x86_64-linux-gnu/libpthread.so.0
#1  0x00007ffff3ffc09b in _L_lock_1006 () from /lib/x86_64-linux-gnu/libpthread.so.0
#2  0x00007ffff3ffc01c in pthread_mutex_lock () from /lib/x86_64-linux-gnu/libpthread.so.0
#3  0x00007ffff4293e21 in g_mutex_lock (mutex=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gthread-posix.c:208
#4  0x00007fffcf2c5631 in em_utils_contact_photo () from /usr/lib/evolution/3.6/libemail-engine.so.0
#5  0x00007fffcf74f6de in ?? () from /usr/lib/evolution/3.6/libevolution-mail.so.0
#6  0x00007ffff47c3e3e in run_in_thread (job=<optimised out>, c=0x5555570fd8d0, _data=0x55555729c590) at /build/buildd/glib2.0-2.34.1/./gio/gsimpleasyncresult.c:869
#7  0x00007ffff47b2236 in io_job_thread (data=0x5555572901d0, user_data=<optimised out>) at /build/buildd/glib2.0-2.34.1/./gio/gioscheduler.c:162
#8  0x00007ffff427ae62 in g_thread_pool_thread_proxy (data=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gthreadpool.c:309
#9  0x00007ffff427a645 in g_thread_proxy (data=0x7fff84001e30) at /build/buildd/glib2.0-2.34.1/./glib/gthread.c:797
#10 0x00007ffff3ff9e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#11 0x00007ffff3d26cbd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#12 0x0000000000000000 in ?? ()

Thread 34 (Thread 0x7fff2b0d8700 (LWP 28481)):
#0  0x00007ffff400089c in __lll_lock_wait () from /lib/x86_64-linux-gnu/libpthread.so.0
#1  0x00007ffff3ffc09b in _L_lock_1006 () from /lib/x86_64-linux-gnu/libpthread.so.0
#2  0x00007ffff3ffc01c in pthread_mutex_lock () from /lib/x86_64-linux-gnu/libpthread.so.0
#3  0x00007ffff4293e21 in g_mutex_lock (mutex=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gthread-posix.c:208
#4  0x00007fffcf2c5631 in em_utils_contact_photo () from /usr/lib/evolution/3.6/libemail-engine.so.0
#5  0x00007fffcf74f6de in ?? () from /usr/lib/evolution/3.6/libevolution-mail.so.0
#6  0x00007ffff47c3e3e in run_in_thread (job=<optimised out>, c=0x55555717cf90, _data=0x5555570d7c80) at /build/buildd/glib2.0-2.34.1/./gio/gsimpleasyncresult.c:869
#7  0x00007ffff47b2236 in io_job_thread (data=0x555557132130, user_data=<optimised out>) at /build/buildd/glib2.0-2.34.1/./gio/gioscheduler.c:162
#8  0x00007ffff427ae62 in g_thread_pool_thread_proxy (data=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gthreadpool.c:309
#9  0x00007ffff427a645 in g_thread_proxy (data=0x55555733fad0) at /build/buildd/glib2.0-2.34.1/./glib/gthread.c:797
#10 0x00007ffff3ff9e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#11 0x00007ffff3d26cbd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#12 0x0000000000000000 in ?? ()

Thread 32 (Thread 0x7fffb91e2700 (LWP 28461)):
#0  0x00007ffff400089c in __lll_lock_wait () from /lib/x86_64-linux-gnu/libpthread.so.0
#1  0x00007ffff3ffc09b in _L_lock_1006 () from /lib/x86_64-linux-gnu/libpthread.so.0
#2  0x00007ffff3ffc01c in pthread_mutex_lock () from /lib/x86_64-linux-gnu/libpthread.so.0
#3  0x00007ffff4293e21 in g_mutex_lock (mutex=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gthread-posix.c:208
#4  0x00007fffcf2c5631 in em_utils_contact_photo () from /usr/lib/evolution/3.6/libemail-engine.so.0
#5  0x00007fffcf74f6de in ?? () from /usr/lib/evolution/3.6/libevolution-mail.so.0
#6  0x00007ffff47c3e3e in run_in_thread (job=<optimised out>, c=0x5555572a9780, _data=0x555556f78b10) at /build/buildd/glib2.0-2.34.1/./gio/gsimpleasyncresult.c:869
#7  0x00007ffff47b2236 in io_job_thread (data=0x555557349c90, user_data=<optimised out>) at /build/buildd/glib2.0-2.34.1/./gio/gioscheduler.c:162
#8  0x00007ffff427ae62 in g_thread_pool_thread_proxy (data=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gthreadpool.c:309
#9  0x00007ffff427a645 in g_thread_proxy (data=0x555557148850) at /build/buildd/glib2.0-2.34.1/./glib/gthread.c:797
#10 0x00007ffff3ff9e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#11 0x00007ffff3d26cbd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#12 0x0000000000000000 in ?? ()

Thread 29 (Thread 0x7fff2a0d6700 (LWP 28221)):
#0  0x00007ffff400089c in __lll_lock_wait () from /lib/x86_64-linux-gnu/libpthread.so.0
#1  0x00007ffff3ffc09b in _L_lock_1006 () from /lib/x86_64-linux-gnu/libpthread.so.0
#2  0x00007ffff3ffc01c in pthread_mutex_lock () from /lib/x86_64-linux-gnu/libpthread.so.0
#3  0x00007ffff4293e21 in g_mutex_lock (mutex=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gthread-posix.c:208
#4  0x00007fffcf2c46b8 in ?? () from /usr/lib/evolution/3.6/libemail-engine.so.0
#5  0x00007fffcf2c5572 in em_utils_in_addressbook () from /usr/lib/evolution/3.6/libemail-engine.so.0
#6  0x00007fffcf2c0b56 in ?? () from /usr/lib/evolution/3.6/libemail-engine.so.0
#7  0x00007ffff6d0cc91 in junk_test (f=0x555556ffd500, argc=<optimised out>, argv=<optimised out>, fms=0x7fff2a0d59b0) at camel-filter-search.c:867
#8  0x00007ffff6d602b0 in camel_sexp_term_eval (sexp=0x555556ffd500, sexp@entry=0x7fff24004978, term=0x7fff24004620, term@entry=0x35) at camel-sexp.c:812
#9  0x00007ffff6d6156d in camel_sexp_eval (sexp=sexp@entry=0x555556ffd500) at camel-sexp.c:1730
#10 0x00007ffff6d0dda6 in camel_filter_search_match (session=<optimised out>, get_message=get_message@entry=0x7ffff6d09930 <get_message_cb>, data=data@entry=0x7fff2a0d5a60, info=<optimised out>, source=source@entry=0x555556444d50 "1353064348.2234.2@baronipc", expression=0x5555566d0af0 "(junk-test)", error=0x555556fb8e58) at camel-filter-search.c:954
#11 0x00007ffff6d0ba6e in camel_filter_driver_filter_message (driver=0x555556fb8d40, message=<optimised out>, message@entry=0x0, info=info@entry=0x555556789e60, uid=0x7fff94011810 "41286", uid@entry=0x555556ff8020 "41286", source=0x7fff94008010, store_uid=store_uid@entry=0x555556444d50 "1353064348.2234.2@baronipc", original_store_uid=original_store_uid@entry=0x555556444d50 "1353064348.2234.2@baronipc", cancellable=cancellable@entry=0x555556f9f240, error=error@entry=0x7fff2a0d5b48) at camel-filter-driver.c:1733
#12 0x00007ffff6d20c2d in folder_filter (session=<optimised out>, cancellable=0x555556f9f240, data=0x55555700f490, error=0x7fff2a0d5b48) at camel-folder.c:380
#13 0x00007ffff6d5b18c in session_do_job_cb (simple=0x55555700f1f0, session=0x555555912300, cancellable=0x555556f9f240) at camel-session.c:175
#14 0x00007ffff47c3e3e in run_in_thread (job=<optimised out>, c=0x555556f9f240, _data=0x555557052f90) at /build/buildd/glib2.0-2.34.1/./gio/gsimpleasyncresult.c:869
#15 0x00007ffff47b2236 in io_job_thread (data=0x555557053ff0, user_data=<optimised out>) at /build/buildd/glib2.0-2.34.1/./gio/gioscheduler.c:162
#16 0x00007ffff427ae62 in g_thread_pool_thread_proxy (data=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gthreadpool.c:309
#17 0x00007ffff427a645 in g_thread_proxy (data=0x555557031ed0) at /build/buildd/glib2.0-2.34.1/./glib/gthread.c:797
#18 0x00007ffff3ff9e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#19 0x00007ffff3d26cbd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#20 0x0000000000000000 in ?? ()

Thread 23 (Thread 0x7fffa93ef700 (LWP 28215)):
#0  0x00007ffff3ffe0fe in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/x86_64-linux-gnu/libpthread.so.0
#1  0x00007fffef9c250c in WTF::ThreadCondition::timedWait(WTF::Mutex&, double) () from /usr/lib/libjavascriptcoregtk-3.0.so.0
#2  0x00007fffef80fb4f in JSC::BlockAllocator::waitForRelativeTime(double) () from /usr/lib/libjavascriptcoregtk-3.0.so.0
#3  0x00007fffef80fba8 in JSC::BlockAllocator::blockFreeingThreadMain() () from /usr/lib/libjavascriptcoregtk-3.0.so.0
#4  0x00007fffef9c2071 in ?? () from /usr/lib/libjavascriptcoregtk-3.0.so.0
#5  0x00007ffff3ff9e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#6  0x00007ffff3d26cbd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#7  0x0000000000000000 in ?? ()

Thread 22 (Thread 0x7fff893cc700 (LWP 28196)):
#0  0x00007ffff3ffdd84 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/x86_64-linux-gnu/libpthread.so.0
#1  0x00007ffff5b5f1bb in ?? () from /usr/lib/libwebkitgtk-3.0.so.0
#2  0x00007ffff5b5f4ae in ?? () from /usr/lib/libwebkitgtk-3.0.so.0
#3  0x00007fffef9c2071 in ?? () from /usr/lib/libjavascriptcoregtk-3.0.so.0
#4  0x00007ffff3ff9e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#5  0x00007ffff3d26cbd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#6  0x0000000000000000 in ?? ()

Thread 21 (Thread 0x7fff89bcd700 (LWP 28195)):
#0  0x00007ffff3ffdd84 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/x86_64-linux-gnu/libpthread.so.0
#1  0x00007fffef9b10fc in WTF::TCMalloc_PageHeap::scavengerThread() () from /usr/lib/libjavascriptcoregtk-3.0.so.0
#2  0x00007fffef9b1119 in WTF::TCMalloc_PageHeap::runScavengerThread(void*) () from /usr/lib/libjavascriptcoregtk-3.0.so.0
#3  0x00007ffff3ff9e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#4  0x00007ffff3d26cbd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#5  0x0000000000000000 in ?? ()

Thread 18 (Thread 0x7fff8b7fe700 (LWP 28192)):
#0  0x00007ffff3ffdd84 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/x86_64-linux-gnu/libpthread.so.0
#1  0x00007ffff429409f in g_cond_wait (cond=0x7fffd41e61a0, mutex=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gthread-posix.c:746
#2  0x00007ffff70388ac in e_flag_wait (flag=0x7fff7c021b60) at e-flag.c:130
#3  0x00007ffff70397e9 in e_gdbus_proxy_call_sync (proxy=proxy@entry=0x7fffac049980, cancellable=cancellable@entry=0x555557188640, error=error@entry=0x7fff8b7fd968, start_func=start_func@entry=0x7ffff1ba26e0 <e_gdbus_book_call_get_contact_list>, finish_func=finish_func@entry=0x7ffff1ba2d00 <e_gdbus_book_call_get_contact_list_finish>, in_type=in_type@entry=8, in_value=in_value@entry=0x7fff7c01ec30, out_type=out_type@entry=16, out_value=out_value@entry=0x7fff8b7fd9b8) at e-gdbus-templates.c:1503
#4  0x00007ffff703d119 in e_gdbus_proxy_call_sync_string__strv (proxy=proxy@entry=0x7fffac049980, in_string=in_string@entry=0x7fff7c01ec30 "(is \"email\"  \"group-digest@linkedin.com\")", out_strv=out_strv@entry=0x7fff8b7fd9b8, cancellable=cancellable@entry=0x555557188640, error=error@entry=0x7fff8b7fd968, start_func=start_func@entry=0x7ffff1ba26e0 <e_gdbus_book_call_get_contact_list>, finish_func=finish_func@entry=0x7ffff1ba2d00 <e_gdbus_book_call_get_contact_list_finish>) at e-gdbus-templates.c:1759
#5  0x00007ffff1ba44eb in e_gdbus_book_call_get_contact_list_sync (proxy=proxy@entry=0x7fffac049980, in_query=in_query@entry=0x7fff7c01ec30 "(is \"email\"  \"group-digest@linkedin.com\")", out_vcards=out_vcards@entry=0x7fff8b7fd9b8, cancellable=cancellable@entry=0x555557188640, error=error@entry=0x7fff8b7fd968) at e-gdbus-book.c:422
#6  0x00007ffff70359cb in e_client_proxy_call_sync_string__strv (client=0x5555557d4c50, in_string=in_string@entry=0x7fff7c01ec30 "(is \"email\"  \"group-digest@linkedin.com\")", out_strv=out_strv@entry=0x7fff8b7fd9b8, cancellable=cancellable@entry=0x555557188640, error=error@entry=0x7fff8b7fda38, func=0x7ffff1ba44d0 <e_gdbus_book_call_get_contact_list_sync>) at e-client.c:2738
#7  0x00007ffff1b8bf0b in e_book_client_get_contacts_sync (client=0x5555557d4c50, sexp=<optimised out>, contacts=0x7fff8b7fda30, cancellable=0x555557188640, error=0x7fff8b7fda38) at e-book-client.c:2028
#8  0x00007fffcf2c4965 in ?? () from /usr/lib/evolution/3.6/libemail-engine.so.0
#9  0x00007fffcf2c5692 in em_utils_contact_photo () from /usr/lib/evolution/3.6/libemail-engine.so.0
#10 0x00007fffcf74f6de in ?? () from /usr/lib/evolution/3.6/libevolution-mail.so.0
#11 0x00007ffff47c3e3e in run_in_thread (job=<optimised out>, c=0x555557188640, _data=0x555557262a30) at /build/buildd/glib2.0-2.34.1/./gio/gsimpleasyncresult.c:869
#12 0x00007ffff47b2236 in io_job_thread (data=0x5555571b1c30, user_data=<optimised out>) at /build/buildd/glib2.0-2.34.1/./gio/gioscheduler.c:162
#13 0x00007ffff427ae62 in g_thread_pool_thread_proxy (data=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gthreadpool.c:309
#14 0x00007ffff427a645 in g_thread_proxy (data=0x7fffd402c590) at /build/buildd/glib2.0-2.34.1/./glib/gthread.c:797
#15 0x00007ffff3ff9e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#16 0x00007ffff3d26cbd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#17 0x0000000000000000 in ?? ()

Thread 5 (Thread 0x7fffdd23c700 (LWP 28124)):
#0  0x00007ffff3d1b303 in poll () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x00007ffff4256d84 in g_main_context_poll (n_fds=1, fds=0x7fffc80b4250, timeout=-1, context=0x555555922740, priority=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gmain.c:3584
#2  g_main_context_iterate (context=0x555555922740, block=block@entry=1, dispatch=dispatch@entry=1, self=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gmain.c:3285
#3  0x00007ffff42571e2 in g_main_loop_run (loop=0x5555558e6790) at /build/buildd/glib2.0-2.34.1/./glib/gmain.c:3484
#4  0x00007ffff70543c4 in source_registry_object_manager_thread (data=0x55555587e4f0) at e-source-registry.c:804
#5  0x00007ffff427a645 in g_thread_proxy (data=0x555555923e30) at /build/buildd/glib2.0-2.34.1/./glib/gthread.c:797
#6  0x00007ffff3ff9e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#7  0x00007ffff3d26cbd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 4 (Thread 0x7fffdda3d700 (LWP 28123)):
#0  0x00007ffff3d1b303 in poll () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x00007ffff4256d84 in g_main_context_poll (n_fds=1, fds=0x7fffd40010c0, timeout=-1, context=0x5555558ee3d0, priority=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gmain.c:3584
#2  g_main_context_iterate (context=context@entry=0x5555558ee3d0, block=block@entry=1, dispatch=dispatch@entry=1, self=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gmain.c:3285
#3  0x00007ffff4256ea4 in g_main_context_iteration (context=0x5555558ee3d0, may_block=1) at /build/buildd/glib2.0-2.34.1/./glib/gmain.c:3351
#4  0x00007fffdda444ad in ?? () from /usr/lib/x86_64-linux-gnu/gio/modules/libdconfsettings.so
#5  0x00007ffff427a645 in g_thread_proxy (data=0x5555558d9e30) at /build/buildd/glib2.0-2.34.1/./glib/gthread.c:797
#6  0x00007ffff3ff9e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#7  0x00007ffff3d26cbd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 3 (Thread 0x7fffde449700 (LWP 28122)):
#0  0x00007ffff3d1b303 in poll () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x00007ffff4256d84 in g_main_context_poll (n_fds=1, fds=0x7fffd00008c0, timeout=-1, context=0x55555576aff0, priority=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gmain.c:3584
#2  g_main_context_iterate (context=context@entry=0x55555576aff0, block=block@entry=1, dispatch=dispatch@entry=1, self=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gmain.c:3285
#3  0x00007ffff4256ea4 in g_main_context_iteration (context=0x55555576aff0, may_block=may_block@entry=1) at /build/buildd/glib2.0-2.34.1/./glib/gmain.c:3351
#4  0x00007ffff4256ef1 in glib_worker_main (data=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gmain.c:5028
#5  0x00007ffff427a645 in g_thread_proxy (data=0x5555558d9c50) at /build/buildd/glib2.0-2.34.1/./glib/gthread.c:797
#6  0x00007ffff3ff9e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#7  0x00007ffff3d26cbd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 2 (Thread 0x7fffe00f0700 (LWP 28121)):
#0  0x00007ffff3d1b303 in poll () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x00007ffff4256d84 in g_main_context_poll (n_fds=3, fds=0x7fffd80010e0, timeout=-1, context=0x5555557970d0, priority=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gmain.c:3584
#2  g_main_context_iterate (context=0x5555557970d0, block=block@entry=1, dispatch=dispatch@entry=1, self=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gmain.c:3285
#3  0x00007ffff42571e2 in g_main_loop_run (loop=0x555555797060) at /build/buildd/glib2.0-2.34.1/./glib/gmain.c:3484
#4  0x00007ffff48224a6 in gdbus_shared_thread_func (user_data=0x5555557970a0) at /build/buildd/glib2.0-2.34.1/./gio/gdbusprivate.c:277
#5  0x00007ffff427a645 in g_thread_proxy (data=0x5555557d9190) at /build/buildd/glib2.0-2.34.1/./glib/gthread.c:797
#6  0x00007ffff3ff9e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#7  0x00007ffff3d26cbd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7fffe16cda00 (LWP 28112)):
#0  0x00007ffff4293bc1 in g_mutex_get_impl (mutex=0x7ffff45051a0 <g__quark_global_lock>) at /build/buildd/glib2.0-2.34.1/./glib/gthread-posix.c:130
#1  0x00007ffff4293e19 in g_mutex_lock (mutex=mutex@entry=0x7ffff45051a0 <g__quark_global_lock>) at /build/buildd/glib2.0-2.34.1/./glib/gthread-posix.c:208
#2  0x00007ffff426552b in g_quark_from_string (string=0x55555576dee6 "horizontal") at /build/buildd/glib2.0-2.34.1/./glib/gquark.c:203
#3  0x00007ffff4d77f4b in gtk_widget_path_iter_add_class () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#4  0x00007ffff4d73f55 in gtk_widget_path_append_for_widget () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#5  0x00007ffff4ba1b07 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#6  0x00007ffff4bfee07 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#7  0x00007ffff4ba6aff in gtk_container_get_path_for_child () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#8  0x00007ffff4b606a1 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#9  0x00007ffff4ba6aff in gtk_container_get_path_for_child () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#10 0x00007ffff4cbfc3e in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#11 0x00007ffff4cbfd27 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#12 0x00007ffff4cc0478 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#13 0x00007ffff4cc1f05 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#14 0x00007ffff4cc2062 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#15 0x00007ffff4cc2062 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#16 0x00007ffff4cc2062 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#17 0x00007ffff4cc2062 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#18 0x00007ffff4cc2062 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#19 0x00007ffff4cc2062 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#20 0x00007ffff4cc2062 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#21 0x00007ffff4cc2062 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#22 0x00007ffff4ba4e7e in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#23 0x00007ffff2ea9dd0 in ?? () from /usr/lib/x86_64-linux-gnu/libgdk-3.so.0
#24 0x00007ffff4256ab5 in g_main_dispatch (context=0x555555792710) at /build/buildd/glib2.0-2.34.1/./glib/gmain.c:2715
#25 g_main_context_dispatch (context=context@entry=0x555555792710) at /build/buildd/glib2.0-2.34.1/./glib/gmain.c:3219
#26 0x00007ffff4256de8 in g_main_context_iterate (context=0x555555792710, block=block@entry=1, dispatch=dispatch@entry=1, self=<optimised out>) at /build/buildd/glib2.0-2.34.1/./glib/gmain.c:3290
#27 0x00007ffff42571e2 in g_main_loop_run (loop=0x555555c555e0) at /build/buildd/glib2.0-2.34.1/./glib/gmain.c:3484
#28 0x00007ffff4c379b5 in gtk_main () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#29 0x0000555555557269 in main ()
(gdb) quit
A debugging session is active.

    Inferior 1 [process 28112] will be killed.

Quit anyway? (y or n) [/PHP]

---

