---
title: "GNOME randomly reverts to default theme, then refuses to touch Nautilus"
date: 2010-09-16
forum: Desktop Environments
---

### Post by napzilla on 2010-09-16
GNOME and Nautilus have been giving me some relatively minor, but really irritating, trouble. I'm using the standard version of the "New Wave" theme for GNOME. I do most of my file-manager-type stuff in a terminal window, but occasionally I use Nautilus to sort through photographs, PDFs, and videos. When it's working properly, it looks like thus:
[IMG]http://napoletano.net/media/nautilus-good.png[/IMG]
Lately, however, GNOME has been randomly reverting to its default theme right in the middle of my session. Even more bizarre, it then switches *back* to "New Wave" the instant I open the "Appearance Preferences" menu, but it refuses to touch Nautilus, so the File Browser still looks like thus:
[IMG]http://napoletano.net/media/nautilus-bad.png[/IMG]
I could probably live with the issue, except that this default Nautilus display plays those intolerable "popping" sounds every time I do something. That just drives me nuts.
I checked the system log the last time this happened, and the following line might correspond to the random theme change:
```
Sep 16 04:12:22 inspiron kernel: [1148313.906500] gnome-settings-[18663]: segfault at 4 ip 04b0096f sp bf8da180 error 4 in libclipboard.so[4afe000+5000]
```
Running the gnome-settings-daemon doesn't solve the issue with Nautilus, though. I searched the forums and couldn't find any indication that this has been an issue with other people, but it seems like it should be a simple problem to resolve. Any ideas?

Okay, it just did it again, and the syslog contains a similar message:
```
Sep 16 04:55:27 inspiron kernel: [1150898.781685] gnome-settings-[8926]: segfault at 4 ip 0133296f sp bfec7630 error 4 in libclipboard.so[1330000+5000]
```

---

### Post by OmegaPhil on 2010-09-19
Just posting to say that this is also an issue for me (has happened routinely recently) - my theme is Mist.

Example of the error here:

> gnome-settings-[25854]: segfault at 8 ip 00007f3450b31ffb sp 00007fffe4017870 error 4 in libclipboard.so[7f3450b2f000+6000]


I wasn't using the clipboard at the time.

---

### Post by inductiveload on 2010-09-28
This also happens for me, but I don't have libclipboard crash in my syslog, though I do have a lot of scim-bridge crashes, which seem to be related to [this scim-bridge bug]("https://bugs.launchpad.net/ubuntu/+source/scim-bridge/+bug/573103") and my have nothing to do with this.

```
kernel: [ 3796.858979] scim-bridge[2205]: segfault at c ip 00600ecc sp bfcc77a8 error 4 in libscim-1.0.so.8.2.4[5a8000+c2000]
```

My theme is (supposed to be) Nimbus.

---

### Post by darius.k on 2010-10-23
Bumping the thread, because this has started happening to me in the past two days. As soon as I open up the Appereance settings the normal theme is applied. I have to kill and restart nautilus to have it apply it though.

---

### Post by STurner31 on 2010-11-03
I'm bumping the thread because this is an issue for me, too.

I started with a clean install of Kubuntu 10.04 about three months ago, then I added GNOME with the Ubuntu Studio packages from the package manager. My theme should be the default Ubuntu Studio theme, but it changes randomly to the default GNOME theme. It usually happens after I have been running several programs at once for an extended period.

E.G. 1) I was running OOffice Impress and Calc, Opera, Okular, the GIMP, and Dolphin for about 3 hours yesterday while I was building a presentation. After closing Okular, the GIMP and both OOffice programs, I noticed my Desktop Icons had changed.

2)Today I was running Konqueror, Dolphin, Opera, and had a terminal open while I was sorting and editing files (about 1 hour). After closing Konqueror, Dolphin, and Terminal, the icons had changed again.

The common element in my case is running multiple programs and then closing most (or all) of them at the same time. If I logout and log back in, the theme resets to the Ubuntu Studio theme. I hope this information helps.

---

### Post by Damiel on 2010-11-04
same problem here.

```
Nov  3 20:51:51 amnesiac kernel: [ 5749.638558] gnome-settings-[1912]: segfault at 4 ip 022b596f sp bfd8b290 error 4 in libclipboard.so[22b3000+5000]
```

---

### Post by STurner31 on 2010-11-05
It happened again just a moment ago. This time I was running Opera, Konqueror, Audacious, and Kate. I had 3 files open in Kate, and after I was done editing them I closed each one. Immediately, the theme changed to the default GNOME theme. When I pulled up the GNOME menu to go to System->Preferences->Appearances, the window borders and menu appearance changed back from default GNOME to default Ubuntu Studio, but the icons remained default GNOME. Changing the icon setting under Appearance had no effect.

BTW, I would like to verify that I have the same message in Syslog as the rest of the posters ITT, but where do I look to check it? I'm a quick learner, but I'm still new to this OS.

Also, where and how do I report this as a bug? I feel like this thread is a good place to verify that this issue is affecting multiple users, but it's probably not the official place to come to notify someone that can fix this.

---

### Post by OmegaPhil on 2010-11-05
System -> Administration -> Log File Viewer. Its a GUI frontend to the text files in '/var/log'.

Check out the syslog file (I think this contains everything that is thrown at the syslog daemon - other files represent a filtered subset of those messages).

---

### Post by STurner31 on 2010-11-08
```
gnome-settings-[1411]: segfault at 4 ip 0838396f sp bfaebdc0 error 4 in libclipboard.so[8381000+5000]
```

That's what I found in syslog. Thanks, OmegaPhil, for telling me how to check it. Now if we can only figure out what causes it...

---

### Post by STurner31 on 2010-11-08
After googling "error 4 in libclipboard" I found this:

[http://osdir.com/ml/debian-bugs-dist/2010-10/msg02731.html](http://osdir.com/ml/debian-bugs-dist/2010-10/msg02731.html)

where it is recommended to do a backtrace as described here:

[http://wiki.debian.org/HowToGetABacktrace](http://wiki.debian.org/HowToGetABacktrace)

the trouble is, this looks a little too advanced for me. Can someone else try to get a backtrace and maybe we can get this bug sorted out?

In the meantime, I'll certainly try to do it myself, but I'm going to have to teach myself how.

---

### Post by RutherfordTheBrave on 2010-11-09
I just had the some thing happen -- was working and suddenly my whole theme reverted, with Nautilus refusing to switch back. However, I was unable to locate the segfault in my system log. I was running Chrome, FireFox, and Virtual Box at the time.

---

### Post by darius.k on 2010-11-11
My issues seem to be a bit different from the ones people in this thread are experiencing.

In my case the theme only reverts to gnome default upon boot. The login screen got the correct theme, but as soon as I log in it's the gnome default. This does not happen every time I boot, but only sometimes.
Also I do not have such a error message in my syslog. It happened again today, and there's nothing from gnome-settings.

I had this issues already with previous ubuntu versions, but they never persisted.

---

### Post by STurner31 on 2010-11-15
Bumpin with a status report. I'm still trying to get a backtrace, but it's kind of a tricky process.

The problem I'm having now is that I don't know how to track the gnome-settings daemon using gdb. The daemon starts at (or before) the gnome session startup. So, I tried Ctrl-Alt-F2 to a new terminal, started a new X-session on display :1, started gdb, and then started a new gnome session. If I'm correct, this should allow gdb to track the gnome session and all of its daemons. Unfortunately, I was unable to recreate the bug. Can anyone confirm that this is the best way to generate a backtrace for this bug? Am I on the right track?

---

### Post by STurner31 on 2010-11-15
Success?

So, I managed to recreate the bug by using gdb to start a second gnome session. After the bug occured, I killed the gnome session in the terminal running gdb, then I used "bt" to get the following output:

```
(gdb)bt
#0 0x0012d422 in ?? ()
#1 0x00a16b86 in poll () from /lib/tls/i686cmov/libc.so.6
#2 0x007ac4eb in g_poll () from /lib/libglib-2.0.so.0
#3 0x0079f0ac in ?? () from /lib/libglib-2.0.so.0
#4 0x0079f817 in g_main_loop_run () from /lib/libglib-2.0.so.0
#5 0x002873c9 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#6 0x08062033 in ?? ()
#7 0x0096dbd6 in __libc_start_main () from /lib/tls/i686/cmov/libc.co.6
#8 0x08051291 in ?? ()
(gbd)
```

I don't know if this is helpful to anyone, but hopefully one of the more experienced Ubuntu geeks can make sense of it. It would make me feel a little more confident about this backtrace if someone else ITT could generate the same output on their machine.

---

### Post by motorcity909 on 2010-11-15
The second solution in post 4 of this thread 
[http://ubuntuforums.org/showthread.php?t=1483838](http://ubuntuforums.org/showthread.php?t=1483838)

has worked for me.  It did mess up my desktop icons so I had to resize them and it lost some font sizes (Window border)

I first had this problem occur last Friday after I upgraded to 10.10 and after using that solution it was fine over the weekend but then reoccurred this morning, so I had to run that solution again.

I hope I don't have to do this every 3-4 days!

---

### Post by STurner31 on 2010-11-15
> **motorcity909 said:**
> The second solution in post 4 of this thread 
[http://ubuntuforums.org/showthread.php?t=1483838](http://ubuntuforums.org/showthread.php?t=1483838)

has worked for me.  It did mess up my desktop icons so I had to resize them and it lost some font sizes (Window border)

I first had this problem occur last Friday after I upgraded to 10.10 and after using that solution it was fine over the weekend but then reoccurred this morning, so I had to run that solution again.

I hope I don't have to do this every 3-4 days!

I appreciate the help. As far as I can tell (and I'm still new to Ubuntu) that command that is suggested simply removes the configuration file(s) for your desktop and restarts the computer. That's why it's not a permanent fix. Earlier ITT, a few of us noted that logging out and logging back in fixes the theme, but again, it doesn't fix the bug.


In other news, I think what we have is a repeat of the bug reported here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/588155](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/588155)

so I linked this thread to that one and vice-versa. Hopefully, someone with some code-knowledge can sort this thing out soon.

---

### Post by STurner31 on 2010-11-18
Update: I did a clean install of Ubuntu Lucid last night. After going through all the updates, I added the Ubuntu Studio suite again. Then, after some more updates, I installed the sun-java6-plugin package through Synaptic and its required libraries. It was at this point that the bug surfaced again.

I'm going to remove the sun-java plugin, but I do have some apps that won't work with its openjdk/icedtea analogues. My expectation is that if the sun-java plugin is causing the bug, then removing it will remove the bug. This might explain why the bug affects multiple users, yet clearly is not affecting all users (if it were affecting everyone, I assume this thread would have exploded with comments by now).

I realize this bug could be caused by numerous other things, like gnome-do/docky, anything from the Studio suite, planetary alignment, emotional fragility of my RAM, and/or graphics-driver syphilis. I'm going to start removing these packages one by one until I get a solid week without seeing the bug. I'll report back here periodically, and I'd really appreciate if someone else would join me in trying to isolate this bug.

---

### Post by GN_ on 2010-11-21
I have the same problem. When I close Qt app (for example: Krusader), my theme reverts to default theme :(

**/var/log/messages:**
```
Nov 21 12:22:20 gn-desktop kernel: [ 4802.407815] gnome-settings-[1698]: segfault at 4 ip 051c796f sp bf9388b0 error 4 in libclipboard.so[51c5000+5000]
```

p.s. GNU/Linux Ubuntu 10.04

---

### Post by STurner31 on 2010-11-30
As promised, here's the update. Not counting the Thanksgiving holiday, I have now had about a week of normal usage without seeing this bug. What I did:

1)removed the sun java plugin for firefox
2)stopped using Gnome-Do/Docky

I think the problem lies in Gnome-Do/Docky. After I removed the sun-java plugin, I was still experiencing the random theme changes. Then I went back to using the regular Gnome-panel instead of Docky, and the bug hasn't been seen since. 

I realize that there also might have been some package updates that came down the line and fixed the problem. So my next step is to start using Docky again to try and recreate the bug behavior.

---

### Post by darius.k on 2010-12-02
I stopped using Gnome Do yesterday, because I switched to Synapse. This morning my theme reverted again, but I hadn't removed the remaining config up to that point. It did not use Docky though.

Concerning the firefox java plugin, I've got it installed but I am not using firefox (chromium).

Since I've also had a relief period in the recent week, there might be some updates that are related.

---

### Post by STurner31 on 2010-12-02
Apparently, I spoke too soon. I haven't re-installed the sun-java6-plugin package, nor have I gone back to using Docky, but I just saw my theme revert to the Gnome default.

I was trying to print a pdf to a networked printer (that worked fine this morning) and having a lot of trouble. The job would get added to the queue but then it would never print. After poking around in CUPS, I tried to open System->Administration->Printing and then view the printing queue. That's when the revert happened.

I'm starting to think that this bug is related to available system resources. Since I only see it when several programs are running simultaneously, and it seems to only show itself when one of those programs is closed or when a new program is opened (i.e. an operation that requires even more resources is requested).

My hardware is older, I'm using a 5 year-old Sony Vaio PCG-K45 with a 3.2GHz P4 and 1Gb of RAM. Is anyone else out there using something modern and seeing this bug?

---

### Post by ubuntwinkel on 2010-12-12
Similar issue, I think.  My system had been idle for some time while I was at work.  On return, Gnome-panel was frozen (which it does fairly regularly, and is related to NFS or SSHFS flakiness, and has never caused, in the past, any reversion to default theme).  Interacting with Nautilus to detect which network share was down caused Nautilus to freeze, with a huge spike in overall system load, briefly freezing everything a couple times over about a minute. Gradually the Gnome theme reverted to the default, starting with the system tray, then spreading throughout the system.  Gnome panel came back to life.  Starting 'Appearance Preferences' restored my chosen theme throughout the system EXCEPT in Nautilus.  But only for my user.  Nautilus started as root had the chosen theme, not the default, as shown below.

[IMG]http://burgwinkel.com/img/Screenshot-19.png[/IMG]  
(Nautilus-root is on top with the chosen theme, Nautilus for user joe is beneath with the default theme, and farthest back is the Log File Viewer, again with the chosen theme.  

Below is the only untoward event noted in syslog, and it occurred four times, all coinciding with the Nautilus crash:

> Dec 12 01:08:42 blubox kernel: [260640.660215] INFO: task nautilus:10277 blocked for more than 120 seconds.
Dec 12 01:08:42 blubox kernel: [260640.660223] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Dec 12 01:08:42 blubox kernel: [260640.660229] nautilus      D ffff88010dc1a4c0     0 10277   2559 0x00000004
Dec 12 01:08:42 blubox kernel: [260640.660239]  ffff88010fc09bd8 0000000000000082 0000000000015bc0 0000000000015bc0
Dec 12 01:08:42 blubox kernel: [260640.660249]  ffff88010ccc4858 ffff88010fc09fd8 0000000000015bc0 ffff88010ccc44a0
Dec 12 01:08:42 blubox kernel: [260640.660257]  0000000000015bc0 ffff88010fc09fd8 0000000000015bc0 ffff88010ccc4858
Dec 12 01:08:42 blubox kernel: [260640.660265] Call Trace:
Dec 12 01:08:42 blubox kernel: [260640.660284]  [<ffffffff81542907>] __mutex_lock_slowpath+0xf7/0x180
Dec 12 01:08:42 blubox kernel: [260640.660293]  [<ffffffff815427eb>] mutex_lock+0x2b/0x50
Dec 12 01:08:42 blubox kernel: [260640.660302]  [<ffffffff8114ce6e>] real_lookup+0x3e/0x160
Dec 12 01:08:42 blubox kernel: [260640.660310]  [<ffffffff8114eeb8>] do_lookup+0xb8/0xf0
Dec 12 01:08:42 blubox kernel: [260640.660317]  [<ffffffff8114f42d>] __link_path_walk+0x1ad/0xf80
Dec 12 01:08:42 blubox kernel: [260640.660326]  [<ffffffff810845b0>] ? wake_bit_function+0x0/0x40
Dec 12 01:08:42 blubox kernel: [260640.660334]  [<ffffffff81543e0e>] ? _spin_lock+0xe/0x20
Dec 12 01:08:42 blubox kernel: [260640.660343]  [<ffffffff81135842>] ? __slab_alloc+0x92/0x2d0
Dec 12 01:08:42 blubox kernel: [260640.660351]  [<ffffffff8115047a>] path_walk+0x6a/0xe0
Dec 12 01:08:42 blubox kernel: [260640.660358]  [<ffffffff8115064b>] do_path_lookup+0x5b/0xa0
Dec 12 01:08:42 blubox kernel: [260640.660366]  [<ffffffff81151317>] user_path_at+0x57/0xa0
Dec 12 01:08:42 blubox kernel: [260640.660374]  [<ffffffff8127ec2d>] ? aa_dup_task_context+0x3d/0x70
Dec 12 01:08:42 blubox kernel: [260640.660382]  [<ffffffff812842c0>] ? apparmor_cred_prepare+0x40/0x60
Dec 12 01:08:42 blubox kernel: [260640.660392]  [<ffffffff81252626>] ? security_prepare_creds+0x16/0x20
Dec 12 01:08:42 blubox kernel: [260640.660400]  [<ffffffff81141ea1>] sys_faccessat+0xd1/0x1d0
Dec 12 01:08:42 blubox kernel: [260640.660407]  [<ffffffff81141fb8>] sys_access+0x18/0x20
Dec 12 01:08:42 blubox kernel: [260640.660416]  [<ffffffff810121b2>] system_call_fastpath+0x16/0x1b

I haven't restored the chosen theme to Nautilus (for my user), despite many attempts and several restarts of Nautilus.  Rebooting will work, I suspect.  But rebooting will also eliminate whatever evidence of this bug is extant right now in my system.  I will report back any discoveries, but in this thread, more methodical minds than mine have yet to discover the cause, so I doubt I'll be able to.  

PS: I recently installed the text editors Kate and Kwrite (because gedit balks way too often, giving 'unknown encoding' errors).  And Kate was open at the time of this malfunction (along with OOOcalc, gnome-terminal, Rhythmbox, Chromium, uTorrent, and Thunar).  Also, I'm running Compiz, and restarting that didn't help.

---

### Post by Kupfer on 2010-12-13
Same thing started happening to me two days ago on an Asus EeePC with Ubuntu 10.10 desktop edition. The Ambiance and Radiance themes keep randomly reverting to the Gnome default when logging in. When I start the Appearence Preferences, it partly fixes the problem, but my theme is shown as 'Custom'. Whenever I choose Ambiance or Radiance again, after logging in (and the default gnome theme greets me to my annoyance), it always reverts to 'Custom'.
I even reinstalled Ubuntu - had the 64bit edition running with loads of ppas enabled, so I figured maybe some update from an untrusted source is responsible - but the issue just appeared on Ubuntu 32bit with minimal number of ppas enabled.
Good thing I keep my OS and data on separate partitions so I can reinstall happily, because until this is sorted out, I'm going to look for a replacement distro. This bug really annoys the hell out of me. It is the second day this is going on and I'm not happy about it. 

This is how my Radiance looks right now:

[IMG]http://i52.tinypic.com/30svzt1.png[/IMG]

---

### Post by bloodorange on 2010-12-13
> **darius.k said:**
> My issues seem to be a bit different from the ones people in this thread are experiencing.

In my case the theme only reverts to gnome default upon boot. The login screen got the correct theme, but as soon as I log in it's the gnome default. This does not happen every time I boot, but only sometimes.


Just to say I'm getting exactly the same problem.  It started only a couple of days ago.  I'm running 64-bit Maverick.

---

### Post by holmes102980 on 2010-12-13
Same problem here too. It seemed to start after I installed updates on my machine. It just randomly reverts to the system theme and icons. Hope there is a fix soon.

---

### Post by holmes102980 on 2010-12-14
The updates this morning seem to have fixed the problem so far.

---

### Post by STurner31 on 2010-12-14
Thanks to those who replied for confirming that this bug is not simply due to older hardware.

Also, as Holmes pointed out, there is a new update for gnome-settings-daemon. Hopefully, this update includes a fix for the problem, but I'm not expecting too much.

---

### Post by Kupfer on 2010-12-15
I used this bug as an opportunity to repartition my hard drive and I would like to reinstall Maverick if the problem has been solved. So, is anyone still experiencing this rather annoying bug since updating or did it resolve the issue? Thanks for the feedback.

---

### Post by rookcifer on 2010-12-16
Same exact thing is happening to me.  I get that ugly grey theme when logging in every time.  After I right-click on desktop and hit "change background" (which will lead you to the theme manager) it automatically fixes it, but only partly.  The icons on my desktop remain with the ugly grey theme and nautilus itself remains with the grey theme.

Gotta be a bug somewhere.  This has happened to me on and of for weeks, but has been doing it every time I log-in lately.  I really hope the Gnome team gets this sorted out.

I am going to check for updates right now (been about 2 days since I updated), so we'll see.

I am running 64-bit Maverick and my hardware is not old (X2 Athlon, 2GB RAM, new Nvidia graphics card).


EDIT:

Just checked for updates and there are none.  **So, this is still an issue as of Dec 16th.**

---

### Post by NonStop on 2010-12-16
> **Kupfer said:**
> Same thing started happening to me two days ago on an Asus EeePC with Ubuntu 10.10 desktop edition. The Ambiance and Radiance themes keep randomly reverting to the Gnome default when logging in. When I start the Appearence Preferences, it partly fixes the problem, but my theme is shown as 'Custom'. Whenever I choose Ambiance or Radiance again, after logging in (and the default gnome theme greets me to my annoyance), it always reverts to 'Custom'.
I even reinstalled Ubuntu - had the 64bit edition running with loads of ppas enabled, so I figured maybe some update from an untrusted source is responsible - but the issue just appeared on Ubuntu 32bit with minimal number of ppas enabled.
Good thing I keep my OS and data on separate partitions so I can reinstall happily, because until this is sorted out, I'm going to look for a replacement distro. This bug really annoys the hell out of me. It is the second day this is going on and I'm not happy about it. 

This is how my Radiance looks right now:

[IMG]http://i52.tinypic.com/30svzt1.png[/IMG]

This is what is happening to me also, exactly the same. Very frustrating.

---

### Post by Kupfer on 2010-12-16
Thanks for the replies. I'm using a Lucid partition now and won't be reinstalling Maverick until this has been resolved. I installed Lucid a couple of days ago, and I'm using it pretty heavily (installing and tweaking all sorts of stuff), but not once did the problem occur. So even though I'm pretty satisfied with my Lucid 32bit now I would also like to have a Maverick 64bit partition again (don't know whether this bug is architecture related) 

By the way, is there a bug report for this? I suscribed to this one (not sure it's the right one - the symptoms described are basically identical to my problems) but not much seems to be happening:

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/588155](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/588155)

---

### Post by Script Warlock on 2010-12-17
is the issue been addressed?  same problem here.. part of the theme was restored but the icons and nautilus hasn't...

---

### Post by STurner31 on 2010-12-17
There was a gnome-settings-daemon update for Lucid 32-bit that I saw a few days ago when I did my morning update/upgrade:

```
sudo apt-get update && sudo apt-get upgrade
```

Since then, I haven't seen any symptoms of this bug, but I also haven't been using my computer that much. I don't know if there are any Maverick updates yet, as I don't use that system.

As for bug reports, I also subscribed to this one:

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/588155](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/588155)

and I saw the same distinct lack of activity, other than more "me too" reports. The early part of that bug report requested a backtrace, so I tried to provide one (a month ago) by opening a new terminal session (Ctrl+Alt+F2, then login), starting an x-session 
```
xinit -- :01
```
then starting gdb and running a new gnome-session in debug mode, according to these instructions:

[https://wiki.ubuntu.com/DebuggingProgramCrash](https://wiki.ubuntu.com/DebuggingProgramCrash)

I assumed that was the only way to get a backtrace of any gnome-settings-daemon errors. Since there hasn't been much activity in that bug report, I assume the info I gave wasn't that useful (or maybe it was since we got an update this week). So, maybe someone running Maverick (32- or 64-bit) can provide that bug report with a backtrace?

E: when your theme randomly changes, to treat the symptom, you can go to System->Preferences->Appearance to get everything but icons to change to your settings. To fix the icons: Alt+F2, then
```
killall nautilus
``` should fix the icons. That code will momentarily stop nautilus, which will instantly respawn itself. Again, that will treat the symptom without logging out, but the bug will still occur.

---

### Post by PC_load_letter on 2010-12-18
I am experiencing this same problem w/ Maverick 32bit on a Thinkpad 43 that never had this bug w/ Jaunty. 
I experience it at first login, I can fix the panel + icons from the Appearance menu, but the Nautilus windows do not change, only by killing Nautilus I got that fixed. 

FYI, I do run sun-java-jre because I need it to run Sage Math correctly, and I use Do + Docky.

---

### Post by bradshawd on 2010-12-19
I am afraid I have to report I also am suffering with this.  Seems to be upon start up that it happens.  Going into appearence will normally cure it all of its own accord.  but for some reason does not always cure it within Nautilus

Even Killing Nuatilus does not necesarily fix the issue. still looking at a default gray boxy window.

Have just doneanother update and no change..

Maverick 10.10 on an older Toshiba M2 (Nvidia graphics)

All other functions work fine....  Just This default theme issue.

Derek

P.S. Sorry this is just and me addition to the thread.  But lets keep it at the top of the list.

---

### Post by scooby359 on 2010-12-19
I'm having the same problem too, when switching my laptop on, the basic theme is used as others have described.

Another thing I've noticed is that I can't make a Live USB stick at the mo, it's freezing in the last stage. Not sure if this is a related bug or just bad timing of a seperate bug.

---

### Post by brocos on 2010-12-19
I have exactly the same problem reported in this thread. I'm running 10.10 desktop edition. I have remove the top and bottom panel and installed Avant Window Navigator as well as Compiz Fusion.

---

### Post by Kalimol on 2010-12-19
I have this problem, although it's not pervasive - about one out of ten boots, my icons, theme, and sound profile are all set to defaults. If I log out and return, everything is back to normal.

---

### Post by rookcifer on 2010-12-20
The updates from a couple of days ago fixed this issue for me (I think Java was one of the updates).

---

### Post by vagrantjoe on 2010-12-20
so what's the solution for this problem guys?

---

### Post by AgenT on 2010-12-20
Found a quick temporary solution. Open terminal and type:
```
gnome-settings-daemon
```(press enter)

Just do that anytime you encounter this problem.

I suggest making sure gnome-settings-daemon is not already started by:
```
ps -ef | grep gnome-settings-daemon
```If you get no output, it means it's not running.

I think when going to sleep or logging in or out once in awhile something causes the settings daemon to crash. After recent updates it still happens.

---

### Post by nyteryder79 on 2010-12-20
I had this problem in 10.10 x64, but it only started today when I did updates.  I noticed that there was a nvidia-current-modaliases package updated, but I'm running ATI.  I uninstalled this package and my gnome-theme-reset issue is now resolved.  May work for others.

---

### Post by vagrantjoe on 2010-12-21
even updates ain't working for me.... How do i contact Mark Shuttleworth? I like ubuntu so much.... But my friend is teasing both me and ubuntu ever since this glitch... I know it's so minor... Guys come one... Help... Write some program and make it ok...

---

### Post by rookcifer on 2010-12-22
OK, bad news.  I posted a couple of days ago that the last updates solved this issue.  That is they did until today's updates (a new kernel).  Now it is doing the same thing again -- ugly grey theme at startup.

**[SIZE="3"]Hello, Ubuntu developers.  Are you listening?[/SIZE]**

---

### Post by Kupfer on 2010-12-22
Maybe we should file another bug report all of us can subscribe to, because the old one ([https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/588155](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/588155)) doesn't look encouraging. I'm not an expert on bug reports, so maybe someone who is can add his two cents, but the fact that it is marked 'incomplete', is set to 'unassigned', there is a warning about expiration and the only activity regarding it seems to come only from "me too"-reports, is not encouraging. Maybe another bug report (or reports) would wake up the bug-fixers.

I would have already filed a bug report already (i was active in the old one), but as I said, I'm not an expert in bug reporting-guidelines, so maybe I'm wrong and the problem IS being looked at. Anyone have more information?

Some activity or feedback that the developers are aware of the problem would be reassuring.

---

### Post by rookcifer on 2010-12-22
> **Kupfer said:**
> Maybe we should file another bug report all of us can subscribe to, because the old one ([https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/588155](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/588155)) doesn't look encouraging. I'm not an expert on bug reports, so maybe someone who is can add his two cents, but the fact that it is marked 'incomplete', is set to 'unassigned', there is a warning about expiration and the only activity regarding it seems to come only from "me too"-reports, is not encouraging. Maybe another bug report (or reports) would wake up the bug-fixers.

I would have already filed a bug report already (i was active in the old one), but as I said, I'm not an expert in bug reporting-guidelines, so maybe I'm wrong and the problem IS being looked at. Anyone have more information?

Some activity or feedback that the developers are aware of the problem would be reassuring.

I just posted in that bug report thread and asked what the heck is going on with this bug.  I hope they are working on it.

---

### Post by Kupfer on 2010-12-22
@rookcifer

Thank You! Let's see if anything happens.

---

### Post by linux_burner on 2010-12-23
I had the same problem which started two weeks ago. I uninstalled nvidia-current-modaliases as suggested by one of the guys and its been working correctly for me so far. I have a SiS chipset with shared graphic memory. Hope this helps.

---

### Post by Kupfer on 2010-12-23
> **linux_burner said:**
> I had the same problem which started two weeks ago. I uninstalled nvidia-current-modaliases as suggested by one of the guys and its been working correctly for me so far. I have a SiS chipset with shared graphic memory. Hope this helps.


Can anyone else confirm that this is working? Unfortunately I can't because I removed Maveric because of this bug and I'm using Lucid Lynx, and in Lucid the bug doesn't appear (at least for me). I would like to reinstall Maverick when this issue is resolved.

Also, I filed another bug report on the issue here: [https://bugs.launchpad.net/ubuntu/+bug/693832](https://bugs.launchpad.net/ubuntu/+bug/693832)

So far, no reaction. I understand that it's the Christmas Season and everything, but yesterday I filed a Hplip related bug report and I got my problem resolved in just under three hours!! So the silence regarding this bug does strike me as strange.

Then again, I may be overrreacting. :D

---

### Post by PC_load_letter on 2010-12-23
The problem seems to have been fixed for me, latest updates or whatever it was, everything gnome is normal now.

---

### Post by rookcifer on 2010-12-23
> **PC_load_letter said:**
> The problem seems to have been fixed for me, latest updates or whatever it was, everything gnome is normal now.

It will start back.  The updates a few days ago fixed the problem for me, but only for a day.  Now it's back.

---

### Post by twodogs on 2010-12-24
I re-installed nautilus and nautilus-data in synaptic and rebooted three times with no problem. Yet.  I do have Nautilus Elementary installed and it didn't mess that up.  Theme looks good as usual.

---

### Post by Kupfer on 2010-12-24
We are getting closer to an explanation why this problem hasn't been adressed so far. 

I posted a Question on Launchpad with the title 'No reaction to bug reports. Are the developers aware of them?':

[https://answers.launchpad.net/ubuntu/+question/138930](https://answers.launchpad.net/ubuntu/+question/138930)

And I just got an answer:

> [mycae]("https://launchpad.net/%7Emycae")          said     6 minutes ago:   
    gnome-settings-daemon is maintained by the gnome project ([http://www.gnome.org/](http://www.gnome.org/)), which is not related to Canonical.
 So chances are that the actual devs are not seeing your bug. If  canonical has the resources, or prioritises your bug, then maybe they  will look at it themselves, seperately from gnome. But looking at that  bug, I (not a dev) have no idea what is going on, and the backtraces  provided are not useful, as they do not have debugging symbols. So its  not even clear what is going on.
 Clarifying this transferrs some of the workload from the devs to the  users, and the devs are much fewer in number than users, so this means  that your bug is more likely to get fixed if you can at least nail down  the problem



I already posted a bug report on bugzilla.gnome.org even before I asked this question on Launchpad (I updated the Gnome bug report with mycae's answer):

[https://bugzilla.gnome.org/show_bug.cgi?id=637921](https://bugzilla.gnome.org/show_bug.cgi?id=637921)

So that's it folks, that's all I can do. If someone more experienced notices, that I posted the bug report wrong (I didn't file it under gnome-settings-daemon but under Nautilus), maybe that person could file a new one on bugzilla.gnome.org. That would be very nice.

But for some reason I think the solution will come down to us users. So if anymore people have experiences to report regarding the nvidia-current-modealiases removal idea, or any other fix ideas in this thread, please report them!

---

### Post by rookcifer on 2010-12-24
Kupfer,

I went ahead and posted on your Gnome Bugzilla thread asking for help and confirming your report.  Hopefully we can get some feedback there from someone.

---

### Post by Kupfer on 2010-12-24
Thanks, rookcifer

Also, there is further movement in my Ubuntu Questions report. Unfortunately I can't try the steps described as I only reinstalled my Maverick 64bit two hours ago. I'm trying to induce the bug, but unfortunately or fortunately it didn't appear yet, so I can't really test it as described here (maybe someone can):

> Well, as long as the status is 'incomplete' rather than 'confirmed' the bug will expire (as it says on top).
 [https://help.launchpad.net/BugExpiry](https://help.launchpad.net/BugExpiry)
To determine if a bug has been abandoned, Launchpad uses the following conditions:
* it has the "Incomplete" status
 In addition, someone who does experience the issue may report it  upstream to raise attention, of course after searching gnome bug  database.
[https://wiki.ubuntu.com/Bugs/Upstream/GNOME](https://wiki.ubuntu.com/Bugs/Upstream/GNOME)
 Since I never had such issue it might be one regarding user config,  (beside the preference of clean installation rather than upgrading).
 However, create a test-user, monitor if the issue remains in order to exclude the case of culprit user config.
 Does this reveal anything meaningful?
gnome-settings-daemon --debug --no-daemon
 Or try via tty (ctrl+alt+f1):
gconftool --recursive-unset /apps/gnome_settings_daemon
and reboot.
 Just in case, if there're any saved gnome-sessions remove them and disable saving sessions.
.config/gnome-session/saved-session

also
> 
Regarding the 'BadMatch' error there is still an unsolved [Bug #447431]("https://answers.launchpad.net/bugs/447431").I don't know whether this BadMatch error is related to our bug or not:

[https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/447431](https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/447431)

---

### Post by moon_raker on 2010-12-25
I thought I was the only one. With me it only happens in Lucid and not in Maverick.
Furthermore it only _happens after exiting a Kde app. like Okular or K3b_ and then only sometimes, it doesn't do this when simply logging in/out. Whether or not Emerald or Compiz is running makes no difference. I have Lucid with Gnome New Wave theme and Gnome Wine icon theme and Emerald. As I mentioned it does not occur with Maverick at all. Minor inconvenience but irritating. Problem identical to the one described by the OP.

---

### Post by rookcifer on 2010-12-25
I just did a fresh install of Maverick and on my 3rd reboot, this bug began appearing.  I am going now to backtrace what exactly I did that might have caused it (though I think there's obviously a bug somewhere).

EDIT:  All I did was install the following packages:

Thunderbird, Gimp, Pidgin, and flashplugin64.

---

### Post by trozamon on 2010-12-27
Normally, I have my theme set to radiance, but it keeps changing to  clearlooks. Here's what I did, but I really don't know why this would  work. I opened the file browser to my home directory and looked at the  hidden folders. I found one called .gconfd and inside was a file  called saved_state. I deleted this file and logged back in. My  appearance then went back to radiance.

EDIT: I found a small problem: after a few boots, my appearance changed again. So, I created a bash script containing:

```
#! bin/bash
sudo rm /home/MY_HOME_DIRECTORY/.gconfd/saved_state
sudo shutdown -P now
```

I use this to shut down my computer now so that the saved_state file is automatically cleared every time I shut down.

---

### Post by slob_2006 on 2010-12-29
this worked for me!

---

### Post by vagrantjoe on 2010-12-30
I did nothing regarding the bug and for a week now, the bug doesn't happen... I didn't install any updates either... It's so mysterious, this bug... It came silently and left silently... Or did it leave? may be it's dormant at the moment... lol... Where's harry potter?

---

### Post by joonpy on 2010-12-31
I'm a openSUSE user (Gnome, 64x), but I'm having a similar problem. First of all, I always have an Opera window open. In my case, this reverting to the default theme happens when I close some KDE applications (Choqok or Okular), especially multiple windows in short interval.

-Joon

---

### Post by Rocket38 on 2011-01-02
[SIZE=5]I have this problem too but it happens to me when I start up my computer and when i change the appearance back it keeps the icons and right click menu the same 

Any help??? thnx :smile:[/SIZE]

---

### Post by johnny.n3xu5 on 2011-01-02
gnome-appearance-properties
killall gnome-appearance-properties
nautilus -q

---

### Post by catrincm on 2011-01-03
> **johnny.n3xu5 said:**
> gnome-appearance-properties
killall gnome-appearance-properties
nautilus -q
As a temporary fix is there a way to get this to run on default as soon as the computer starts?

---

### Post by muhammadnk on 2011-01-03
> **catrincm said:**
> As a temporary fix is there a way to get this to run on default as soon as the computer starts?

in your home ( ~/ ) directory; create a file called .xinitrc and add these values in it:

gnome-appearance-properties
killall gnome-appearance-properties
nautilus -q

save it and try it out.

Cheers.

---

### Post by stinkeye on 2011-01-04
> **muhammadnk said:**
> in your home ( ~/ ) directory; create a file called .xinitrc and add these values in it:

gnome-appearance-properties
killall gnome-appearance-properties
nautilus -q

save it and try it out.

Cheers.

By starting and killing gnome-appearance-properties your merely starting the gnome-settings-daemon
The failure to load or crashing of gnome-settings-daemon seems to be the problem.

so you could just use
```
gnome-settings-daemon
pkill nautilus
```

---

### Post by helbent forleder on 2011-01-05
Same problem here on 10.10. Completely random on two machines: one C2D e4600 and on an Asus eee 1000H.
Opening appearance manager fixes bars - restart nautilus fixes icons.
:P

---

### Post by BigSilly on 2011-01-05
Could be barking up the wrong tree, but I think I'm noticing on mine that if I set a wallpaper and stick with it, the issue goes away, but if I change my backgrounds a lot, the issue is more prevalent. Possibly. :D

I am noticing too that any walls I add to the Appearance settings disappear on the next boot too. Dunno if it's related.

---

### Post by psidrum on 2011-01-05
I am getting the same problem, i think it started when i installed Opera and started using it as default browser,

it would go back to default theme

i have Karmic 9.10

---

### Post by Kupfer on 2011-01-07
The problem just returned for me on Maverick, which I'm going to ditch now completely. I would like to see the issue resolved for Natty though. I have a Lucid on my machine too, no problem there.

Maverick has really been a mess for me since day one, but most problems were minor bugs. This problem, however, leads me to remove "The perfect 10" as it is described on the main website for good and never use it again. I'll be back for Natty, if the bug somehow solves itself till then or someone finally takes a look at it.

For those hoping to see the bug resolved, I can only tell to really get on the nerves of the developers. I don't think you have another option as nobody is willing to take any action regarding it. The Ubuntu devs are pointing at the Gnome people, but the bugzilla.gnome.org report lists the problem as 

**[Status]("https://bugzilla.gnome.org/page.cgi?id=fields.html#status")**:                 RESOLVED           NOTGNOME       

Meanwhile the Launchpad bug report is still "Unassigned".

Here are the links to make your voice heard:

[https://answers.launchpad.net/ubuntu/+question/138930](https://answers.launchpad.net/ubuntu/+question/138930)

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/588155](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/588155)

[https://bugzilla.gnome.org/show_bug.cgi?id=637921](https://bugzilla.gnome.org/show_bug.cgi?id=637921)


Good luck, I'm looking for an alternative now until the release of Natty.

---

### Post by campbell2644 on 2011-01-07
Another one with the same irritating problem. Still seems unresolved.

---

### Post by BigSilly on 2011-01-07
> **Kupfer said:**
> The problem just returned for me on Maverick, which I'm going to ditch now completely. I would like to see the issue resolved for Natty though. I have a Lucid on my machine too, no problem there.

Maverick has really been a mess for me since day one, but most problems were minor bugs. This problem, however, leads me to remove "The perfect 10" as it is described on the main website for good and never use it again. I'll be back for Natty, if the bug somehow solves itself till then or someone finally takes a look at it.

For those hoping to see the bug resolved, I can only tell to really get on the nerves of the developers. I don't think you have another option as nobody is willing to take any action regarding it. The Ubuntu devs are pointing at the Gnome people, but the bugzilla.gnome.org report lists the problem as 

**[Status]("https://bugzilla.gnome.org/page.cgi?id=fields.html#status")**:                 RESOLVED           NOTGNOME       

Meanwhile the Launchpad bug report is still "Unassigned".

Here are the links to make your voice heard:

[https://answers.launchpad.net/ubuntu/+question/138930](https://answers.launchpad.net/ubuntu/+question/138930)

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/588155](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/588155)

[https://bugzilla.gnome.org/show_bug.cgi?id=637921](https://bugzilla.gnome.org/show_bug.cgi?id=637921)


Good luck, I'm looking for an alternative now until the release of Natty.

Hmmm, it certainly seems to have gotten worse of late. I can't log into Maverick without something desktop related has gone peculiar. The main issue I'm having is still this one, but I'm getting lots of little bugs that I just don't understand, such as appearance settings not remembering my wallpapers, gadgets resetting, and general Gnome tomfoolery. 

I just don't get it. I was mostly fine for months, and then just before Christmas this issue kicked in. :confused:  Really hope Natty fixes these issues, but you just know other ones will rear up if they do.

---

### Post by ybytyruzu on 2011-01-09
Hi, same problem here, 10.10, but now I reinstalled Nautilus and for now is working ok.
Regards

---

### Post by 1984dc on 2011-01-11
Hello everyone!

I've been having the same problem since it seems to affect my top panel as which makes me think that it might not be connected to the nautilus package (please correct me if i am wrong, as i am fairly new to ubuntu).

This is a screenshot of the panel with the ugly grey theme

[IMG]http://img190.imageshack.us/img190/1535/screenshotuglygrey.png[/IMG]

and this is it as it should be

[IMG]http://img691.imageshack.us/img691/671/screenshotofhowitshould.png[/IMG]

Kind regards

Dc

---

### Post by helbent forleder on 2011-01-12
Just a comment:
I also was having problems with gnome-do, which wouldn't launch at start-up and I had (and still have) dropbox installed.
A few posts back, ybytyruzu suggested **reinstalling nautilus**, which I have done. I have been using the system for 2 days and probably rebooted 10 times with no more appearance settings nor nautilus troubles.
**I recommend following ybytyruzu's advice!**
I think that the problem could be influenced by dropbox - you know how the installation always insists on restarting nautilus... maybe I skipped that part of the installation process and that messed it up.

---

### Post by hsoulen on 2011-01-12
Same problem for me in Maverick...

First I thought it might be a problem with Cairo Dock but that has proven not to be the issue.

Seems to me that this started occurring around the 22-25th of December just after an update, should have paid better attention to what was being updated I guess.

Frustrating part is the complete lack of response or urgency from the Ubuntu folks considering how widespread this problem seems to be.

Getting tired of all the "funky" issues that have been popping up since Jaunty... Seems like every new release my stability goes down and my frustration goes up. I am spending way too much time "tweaking" for my liking.

Don't even know what distro to look at these days, seems like they are all going the Windows route with way too many patches. I understand that part of the responsibility falls on me for clicking "update" without paying enough attention, but I think there should be a bit more focus on maintaining the current release and a little less time on changing my UI to unity...

My Two Cents, Worth One Cent.

Hank

---

### Post by helbent forleder on 2011-01-12
Have you tried reinstalling nautilus?

---

### Post by sosukeinu on 2011-01-12
> **helbent forleder said:**
> Have you tried reinstalling nautilus?

You just marked nautilus for reinstallation in Synaptic then applied that, right? Or is there a more involved in reinstalling nautilus? Thank you.

---

### Post by helbent forleder on 2011-01-12
Just in synaptic.

---

### Post by BigSilly on 2011-01-12
> **helbent forleder said:**
> Have you tried reinstalling nautilus?

Nope didn't work for me. The next reboot was fine, but the one after that was broken. :(

---

### Post by helbent forleder on 2011-01-12
Then I'm stumped. Sorry.
5 more reboots and still fine for me.

---

### Post by campbell2644 on 2011-01-12
Reinstalling Nautilus doesn't make any difference in my case

---

### Post by hsoulen on 2011-01-13
> **helbent forleder said:**
> Have you tried reinstalling nautilus?

Done, but did not survive a reboot.

In my case I get this problem from a cold boot 60-80% of the time and the solution is to log out and back in (works 100%)...

But then again that is not a "solution" right?

Does not seem to matter which "theme" is applied, always the same thing, top panel goes default as does nautilus, frames around other apps seem to be pretty random. In Appearance it shows as "custom" and changing this to another theme only partially resolves. Log out and back in seems to fix it for that session.

Things attempted:

[LIST=1]
[*]Re-install Gnome
[*]Re-install Nautilus
[*]Remove Cairo dock
[/LIST]

Result: Nada.

Ugh.

Hank

---

### Post by stinkeye on 2011-01-13
This problem has been described in numerous threads with no real solution yet.
The problem seems to be the failure to load of **gnome-settings-daemon**.
Instead of logging out and back in you could...
Alt + F2 and run 
```
gnome-settings-daemon && killall nautilus
```

---

### Post by hsoulen on 2011-01-13
> **stinkeye said:**
> This problem has been described in numerous threads with no real solution yet.
The problem seems to be the failure to load of **gnome-settings-daemon**.
Instead of logging out and back in you could...
Alt + F2 and run 
```
gnome-settings-daemon && killall nautilus
```

Thanks stinkeye,

I have found that when I kill the daemon from the command line (think you might need a sudo in there) sometimes the gnome settings daemon will crash on me again (logs have a few nasties) and the appearance settings are still in "custom". Seems like the log out/back in has the best results for me but this is a good suggestion, and one that is also listed as a workaround in the bugs that have been logged on the subject.

Cheers,

Hank

---

### Post by giowck on 2011-01-13
are there any news on this isse?

I have this bug on 2 netbooks, it's really annoying!!

---

### Post by Agapooka on 2011-01-13
First, I wish to make the point that I am of the opinion that this thread concerns two "sub-bugs" of the same bug - that is, the same symptoms are happening, but they are triggered differently. I see people complaining that they experience the symptoms described in this thread when they are running many programs, of which many have listed Opera and various KDE applications. I, on the other hand, find that these symptoms are triggered at startup. 

There is one thing that I have noticed that nobody has mentioned in this thread, but it is related to logging out. Like many of you, if I log out and log back in, I find that my theme looks as it should. What I have also discovered, but not tested enough to preach with confidence, is that if I **log out before shutting down**, the theme is displayed properly the next time I boot up. This, so far, is consistent, but if others who experience this issue on startup would like to test it, I would be more confident in pinpointing this as a source of the problem.

That said, if this fixes the problem, I can only deduce that logging out and shutting down as separate acts accomplish something relevantly different to shutting down within an active user session. 

EDIT: I'll add that I've shut down from within an active user session and booted about 5 times since I logged out and shut down separately and I have not experienced the bug yet since, but it may be too early to tell. For those who have not tried what I put in bold, please try that first and if you get consistent results, start shutting down from within an active session again.

Agapooka

---

### Post by beczka2005 on 2011-01-13
Also a victim here:

First login after boot I am fine. Log out then log in and theme is gone.

What I did found is that if I disable my AMD videocard driver and use the opensource one I can get the theme to come back if I execute gnome-setting-daemon.

---

### Post by oksig3n on 2011-01-15
im also too.. please, give me a guide.. huuuu :p

---

### Post by clenceo on 2011-01-15
I'm in the same boat! Weird thing, I have to desktops, one does it almost after every reboot.
The second never does it. The difference between the both is that the second desktop is not completely up to date. its been about a month since I updated.

I even deleted most of the themes I dont use and left the good ones!:p

No change :(

I hope there's a fix soon

---

### Post by Agapooka on 2011-01-15
Did anyone try what I suggested **three posts ago*? I'm curious, because this issue hasn't been a problem for me since I did.

Please read my post, apply it and post the results here! 

*> 
 			 		   		 		 		First, I wish  to make the point that I am of the opinion that this thread concerns two  "sub-bugs" of the same bug - that is, the same symptoms are happening,  but they are triggered differently. I see people complaining that they  experience the symptoms described in this thread when they are running  many programs, of which many have listed Opera and various KDE  applications. I, on the other hand, find that these symptoms are  triggered at startup. 

There is one thing that I have noticed that nobody has mentioned in this  thread, but it is related to logging out. Like many of you, if I log  out and log back in, I find that my theme looks as it should. What I  have also discovered, but not tested enough to preach with confidence,  is that if I **log out before shutting down**, the theme is displayed  properly the next time I boot up. This, so far, is consistent, but if  others who experience this issue on startup would like to test it, I  would be more confident in pinpointing this as a source of the problem.

That said, if this fixes the problem, I can only deduce that logging out  and shutting down as separate acts accomplish something relevantly  different to shutting down within an active user session. 

EDIT: I'll add that I've shut down from within an active user session  and booted about 5 times since I logged out and shut down separately and  I have not experienced the bug yet since, but it may be too early to  tell. For those who have not tried what I put in bold, please try that  first and if you get consistent results, start shutting down from within  an active session again.

Agapooka



Agapooka

---

### Post by boywithaxe on 2011-01-16
> **STurner31 said:**
> As promised, here's the update. Not counting the Thanksgiving holiday, I have now had about a week of normal usage without seeing this bug. What I did:

2)stopped using Gnome-Do/Docky

I think the problem lies in Gnome-Do/Docky. After I removed the sun-java plugin, I was still experiencing the random theme changes. Then I went back to using the regular Gnome-panel instead of Docky, and the bug hasn't been seen since. 



This seems to have resolved the issue for me, I am gutted that I have to stop using Gnome-do, I don't mind Docky, but Gnome-do is a must for me :(
Hopefully this will be resolved soon.


EDIT:
Nope, Gnome-Do and Docky were not causing that, but I will try Agapooka's solution next time I reboot. Ah well, long live open source

---

### Post by stinkeye on 2011-01-16
I don't use gnome-do or docky or any mono apps for that matter.
Have the bug though. #-o

---

### Post by rchiossi on 2011-01-17
This bug occurrence seems completely random for me. I've been experiencing this bug on a fresh install of maverick x64. I just use this system for code compilation, I have nothing installed besides the C compiler. It reproduces 1 out of 2 boots. It's quite annoying...

---

### Post by BigSilly on 2011-01-17
> **Agapooka said:**
> Did anyone try what I suggested **three posts ago*? I'm curious, because this issue hasn't been a problem for me since I did.

Please read my post, apply it and post the results here! 

*


Agapooka

OK, so because you asked so nicely (:D), I decided to give your suggestion a shot for a few days, and have been logging out first before shutting down. So far, the main issue of the Ambiance theme reverting to the default Gnome theme has not arisen, and it seems so far to do the trick. I'm still getting other Gnome bugs that aren't related to this bug (panel indicators crashing on log in, the Me menu goes a bit wazzy occasionally for some reason, etc, etc), but this main issue seem to have been "fixed" by logging out first. 

So, what next?

---

### Post by Sturmeh on 2011-01-17
Wow I thought I was the only person with this bug, it's so blatantly obtrusive to be widespread and STILL not fixed! D:

It has nothing to do with gnome-do and docky, or any dock for that matter, it happens on a clean install after a few boots.

If you log out before shutting down it seems to prevent it from happening (Perhaps it does what that script mentioned previously does for you...) but can't be certain.

Re-installing nautilus doesn't fix it.

I've been opening appearances then running 'killall nautilus' in terminal.

---

### Post by stinkeye on 2011-01-17
Whenever this happens if you check in System Monitor you'll find that
gnome-settings-daemon is not running.

So I added ```
**gnome-settings-daemon**
``` to startup applications and after a half a dozen reboots all is good.

---

### Post by Johni0574 on 2011-01-17
I'm gona try the "gnome-settings-daemon" trick... Before this started happening for me, i was having VERY slow bootup times.. i went into Ubuntu Tweak, into the Package Cleaner and did the 4 cleans and the purge.. Afterwards my boot up times increased dramatically of course.. The side effect is the GNOME default theme occasionally starting (1 out of 3 reboots)..Its almost like i'm starting up to fast, making Ubuntu not start in the proper order.. It is quite annoying, and ruins the whole feel of Ubuntu which i've come to love.. For the record i'm not using, and never have used Gnome-do or Docky... 
   Edit: since adding "Gnome-Settings-Daemon" to start up, ive seen the default GNOME theme flash for only a fraction of a second, then my Orta theme started perfectly.. the only reason i noticed it flash at all was due to the horrible bright silver color of the default theme.. Seems to be good temporary fix so far..

---

### Post by rookcifer on 2011-01-18
> **stinkeye said:**
> Whenever this happens if you check in System Monitor you'll find that
gnome-settings-daemon is not running.

So I added ```
**gnome-settings-daemon**
``` to startup applications and after a half a dozen reboots all is good.

I think you have figured out the problem.  The guy above who said to log-out before shutting down discovered a fix that just so happens to somehow trigger gnome-settings-daemon to load properly at boot.  

All in all this bug is a result of something not loading in proper order on boot.  And I guess that "something" is indeed gnome-settings-daemon.  I haven't tried to add it to my start-up scripts yet, but I will and check back.

BTW, Stinkeye: can you hear can you hear the thunder?  Ya better run, ya better take cover!

---

### Post by stinkeye on 2011-01-18
> **rookcifer said:**
> 

BTW, Stinkeye: can you hear can you hear the thunder?  Ya better run, ya better take cover!

"Do you speak-a my language?"
If you do here's a Vegemite sandwich.
[[img]http://www.divshare.com/img/thumb/13803228-77d.jpeg[/img]](http://www.divshare.com/download/13803228-77d)

---

### Post by mathjazz on 2011-01-18
Thanks, stinkeye!

I went to System -> Preferences -> Startup Applications and added gnome-settings-daemon and now I'm happy.

---

### Post by mathjazz on 2011-01-18
Thanks, stinkeye!

I went to System -> Preferences -> Startup Applications and added gnome-settings-daemon and now I'm happy.

---

### Post by Sturmeh on 2011-01-18
Nice!

> **stinkeye said:**
> "Do you speak-a my language?"
If you do here's a Vegemite sandwich.
[[img]http://www.divshare.com/img/thumb/13803228-77d.jpeg[/img]](http://www.divshare.com/download/13803228-77d)

Om nom nom nom...

---

### Post by BigSilly on 2011-01-18
But something's stopping this from launching in the first place, isn't it? I've added the script to startup, and hopefully this will fix it, but shouldn't this have already been part of the startup scripts anyway?

:confused:

Either way, thanks for the fix dudes. :)

---

### Post by helbent forleder on 2011-01-19
Hey Stinkeye!
That seems to REALLY do the trick! Thanks!

---

### Post by rchiossi on 2011-01-19
Hmm, nice... I'll give this fix a try. But, as BigSilly pointed, this is more of a workaround than an fix. gnome-settings-daemon should be executed without user intervention and something is preventing it to happen. Finding out what it is and stopping this behaviour would be the actual fix.

---

### Post by BigSilly on 2011-01-19
Unfortunately this fix hasn't worked for me. The following two reboots I did gave me the errors as before. :(  In fact it's worse this time, as it seems to crash my Google Gadgets. On both reboots the gadgets disappeared on log in. :( :(

I'm going to remove the script from start up and just wait for a fix from...well, whoever wants to fix it, as Canonical say it isn't their responsibility.

---

### Post by KJ KJ KJ on 2011-01-19
I've been doing "logout" from the panel and then "shutdown" from the welcome screen. Things are much better.

Annoyingly, I wrote this script as a workaround, and haven't yet had to use it in anger since using the "logout first" method. Here it is, FWIW:

```
#!/bin/dash
#
# Workaround for an annoying bug that loses the current theme.
# http://ubuntuforums.org/showpost.php?p=10314526&postcount=66
#

pidof gnome-settings-daemon > /dev/null 2>&1
if test $? -ne 0 ; then
    gnome-settings-daemon > /dev/null 2>&1
    pkill nautilus > /dev/null 2>&1
    pidof gnome-settings-daemon  # PID indicates success.
fi

#
# Done.
#

```

It only does something if the daemon isn't running, what it does in that case is start the daemon, kill nautilus and print the PID of the newly started daemon as confirmation.

What I'm thinking is that if you add a delay using sleep and stick this in your startup, then when everything looks normal, nothing happens, if things look ugly, this script will apply the fix.

---

### Post by BigSilly on 2011-01-20
Thanks for that KJ, will give it a go. I'm still getting the problem here, and like you I am having to log out first before shutting down. What a pain!

---

### Post by BigSilly on 2011-01-20
Great. The 'logging out and then logging in' thing isn't working any more. Whoop-de-doo. :(

---

### Post by BigSilly on 2011-01-20
Great. The 'logging out and then logging in' thing isn't working any more. Whoop-de-doo. :(

---

### Post by clenceo on 2011-01-20
I've done the following:

System -> Preferences -> Startup Applications and added gnome-settings-daemon

I still experienced my theme reverting back to a default theme.

I then began to log out, then shut down my computer. All was good and consistent. 
My update manager showed I had some updates a few days ago, installed all the updates.

Now, I dont have to logout first and then shut down. 
I shut down my computer directly from Cairo dock. I've had no trouble in the last few days. I may have shut down and restarted atleast 20 times.

Anybody experience this?

---

### Post by hsoulen on 2011-01-21
> **clenceo said:**
> I've done the following:

System -> Preferences -> Startup Applications and added gnome-settings-daemon

I still experienced my theme reverting back to a default theme.

I then began to log out, then shut down my computer. All was good and consistent. 
My update manager showed I had some updates a few days ago, installed all the updates.

Now, I dont have to logout first and then shut down. 
I shut down my computer directly from Cairo dock. I've had no trouble in the last few days. I may have shut down and restarted atleast 20 times.

Anybody experience this?

Yep, last updates seem to have fixed it for me as well.

Wish someone would have told us it WAS a problem and they were working on it... Guess I need to check the bugs in launchpad and see if anyone finally admitted this was a problem!

Oh well, I guess the fix came just in time as I was evaluating a couple of other distros in Vbox ;)

Hank

---

### Post by BigSilly on 2011-01-21
But you still had to apply a manual fix where you shouldn't have had to. Plus, I'm really not sure there has been a fix committed for this, certainly not in the last round of updates.

I dunno what's happening, but I'll try the gnome-settings-daemon at startup thing again and go back to logging out, see if I get any joy. I'll post back later.

---

### Post by Johni0574 on 2011-01-21
Well i have begun to have this happen on startup again.. its reverting to the Gmome default window decoration only now, but the "gnome-setting-daemon" trick in the startup is preventing my gnome panel from reverting along with it.. Just happened on my login.. It also happened mid session yesterday when my window decoration changed to the default Gnome theme, but the Gnome panel stayed my chosen theme... So its still not fixed and an issue here... Is there any verification its currently being looked into and hopefully repaired? Its not an issue with having the Orta theme installed is it? Just a thought. It is when i first begun to noticed this issue originally... Hopefully not, i love the theme.. I used its little installer to tweak it to my liking, and apply it...As i said its just a thought.

---

### Post by BigSilly on 2011-01-22
[Bug report here]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/588155"). Looks to me that so far no fix has been committed. Fingers crossed someone will pick it up, but I'm sure someone mentioned earlier that this is a Gnome bug, not an Ubuntu bug, and Canonical will have nothing to do with it.

Still getting the issue here, albeit randomly. I have to remember to log out first, then shutdown still.

---

### Post by Johni0574 on 2011-01-22
8-[I would like to have thought that since Gnome is packaged together with the stock Ubuntu install that it would be classified as a "Canonical" type of problem not just a Gnome one..At least an "everyone" issue maybe...I began to think "Maybe i should just let the problem rest and wait..They have more important issues to work on." But then i quickly thought "An issue that randomly changes the entire look of your operating system during use and or 1 of 3 times you boot up is a significant issue, and is one of those thing that should never happen to an operating system." After all putting aside for a moment the wonderful multitasking ability and functionality of Ubuntu, i also love it because i can make it look as beautiful as i so desire.. This bug completely kills that loved feature and which i have have been dealing with for several months now like many of you..

I think this evening i will start a thread on the Gnome forums.. Maybe they have fixed it in the 3.0 release due in April..Doing a quick search there revealed no threads.. Doing a "gnome settings daemon" search brought up some posts from 2007 on the Gnome forums... :-(

---

### Post by Kupfer on 2011-01-23
> **Johni0574 said:**
> I think this evening i will start a thread on the Gnome forums.. 

Please do that. Although it is still a question for me whether this is a Gnome or an Ubuntu issue. Shouldn't the bug surface with other Gnome distros too? I'm using Fedora 14 too and the bug didn't occur once and I can definitely remember that I received a gnome-settings-daemon update at some point. 
But I'm no expert. So thanks to everyone trying to backtrace the source of the problem.

---

### Post by Johni0574 on 2011-01-23
Noticing something else, Cairo Dock which i have running on startup has the "show desktop" application running on it.. Every time on bootup the fancy little icon was turned into the default gnome folder icon until i used it. Then it would revert back to the fancy icon it was supposed to have.. I put a delay timer under the start up applications for Cairo dock to force it to wait before loading.. The icon shows up fine in Cairo dock when it boots up now...
 
_bash -c "sleep 14; /usr/bin/cairo-dock -o"_

I had to do the same thing with Google Gadgets starting a while ago.. It was booting before the Window Composter was. I had to do the bash script to delay its boot as well. This allowed the proper transparent window deco to show on my goggle gadgets.. Just another Decoration fix if anyone needs it while we wait for a White Knight to rescue.. 
I comment so much on this issue because it is the only problem i have not found resolution for since i began running Ubuntu and its driving me nuts!

---

### Post by hsoulen on 2011-01-24
Well I was fine for a few days but now it's back...

One thing I have noticed is timing on login. If I let the computer sit at the login screen for 10-30 Seconds before I login I have about 98% chance that my theme will be correct, if I log straight in after booting then chances are my gnome panels will be screwed up.

As far as I can tell from launchpad bugs, neither Gnome nor Ubuntu teams are accepting responsibility for the issue... So we wait.

Guess the search for distros continues for me.

Hank

---

### Post by Copper Bezel on 2011-01-24
At least it's a quick fix from the command line. The delayed startup script with the settings daemon is a nice idea - maybe combine that with a killall nautilus at the same time. 

Such a weird error, and weirder still, as folks have said, that it isn't being noticed.

I don't have the Orta theme installed, or know what it is, for that matter, so it's definitely not related to that.

---

### Post by BigSilly on 2011-01-24
> **hsoulen said:**
> Well I was fine for a few days but now it's back...

One thing I have noticed is timing on login. If I let the computer sit at the login screen for 10-30 Seconds before I login I have about 98% chance that my theme will be correct, if I log straight in after booting then chances are my gnome panels will be screwed up.

As far as I can tell from launchpad bugs, neither Gnome nor Ubuntu teams are accepting responsibility for the issue... So we wait.

**Guess the search for distros continues for me.**

Hank

Yeah me too. I've decided to do a bit of distro hopping since this bug (and other ones if I'm honest) reared it's ugly head. I installed the new Pardus Linux 2011 over the weekend, and have to say it's blown me away. Well worth a look for Ubuntu users looking for a change. Didn't realise just how much I'd missed KDE, and it's been lovely to try a fresh new Linux after years of Ubuntu. I'm still using Ubuntu alongside it, but the bugs that go unfixed have been driving me potty for some time.

---

### Post by rvchari on 2011-01-24
i was facing similar problem when i was using buuf 1.2 or some thing as icon and elementary theme. nautilus displayed just its dumb default icons....
i had ignored it and when i came across buuf2.30, i simply uninstalled previous buuf, removed them from my .icons directory too and made a clean install to /usr/share/icons, then copied the folder buuf2.30 to my .icons directory (just did that out of intuition..)
now nautilus is functioning good and displays buuf icons under all circumstances...

i know the bug must be in the icon theme, blankon icons still r not working for me in nautilus !

---

### Post by rchiossi on 2011-01-24
I don't think it has anything to do with the icons... it's not just the icons, it's the entire theme that is reverted back to default.

---

### Post by rvchari on 2011-01-24
in my case, the window borders and menu style is as per theme, its the icon set that messes up....
i think such bugs going un noticed does seem wierd...
now i m happy with the theme thats acceptable to my sys !!! (as the wise saying goes, if u cant beat'em, join them ;))

---

### Post by hsoulen on 2011-01-25
> **BigSilly said:**
> Yeah me too. I've decided to do a bit of distro hopping since this bug (and other ones if I'm honest) reared it's ugly head. I installed the new Pardus Linux 2011 over the weekend, and have to say it's blown me away. Well worth a look for Ubuntu users looking for a change. Didn't realise just how much I'd missed KDE, and it's been lovely to try a fresh new Linux after years of Ubuntu. I'm still using Ubuntu alongside it, but the bugs that go unfixed have been driving me potty for some time.

Indeed.

So my problem is that almost all distros nowadays are either geared toward "usability" (trying to win over the Windows crowd) or geeks (trying to win over the Linux crowd) so I am trying to figure out what fits.

[LIST]
[*]Ubuntu - Getting more bugs per release...
[*]Mint - Too much custimization to get rid of that god-aweful menu!
[*]Debian - Stable but well... boring.
[*]Fadora - Ugh... I can't go back to RPM!
[*]Gentoo - I just don't have that kind of time!
[*]Slackware - My firewall yes, my desktop NO!
[*]Mandriva - Huh?
[*]Jolicloud - Just kidding...
[/LIST] 

I have never heard of Pardus until you mentioned it, looking to load up a VM and check it out so thanks for the suggestion. What is the support for packages like? Is it Debian based?

I have no idea at this point so any suggestions are awesome!

Cheers,

Hank

---

### Post by rvchari on 2011-01-25
if i m not mistaken, pardus ships with kde. so mint users might find it more pleasinf or for that matter kde users ?
as the previous posting said.. have to vm before trying anything new...
as of now gud ol'buntu seems to have more options !!! to get bumped into a problem and getting it solved... now aint that a nostalgic feeling ?;)

---

### Post by BigSilly on 2011-01-25
> **hsoulen said:**
> Indeed.

So my problem is that almost all distros nowadays are either geared toward "usability" (trying to win over the Windows crowd) or geeks (trying to win over the Linux crowd) so I am trying to figure out what fits.

[LIST]
[*]Ubuntu - Getting more bugs per release...
[*]Mint - Too much custimization to get rid of that god-aweful menu!
[*]Debian - Stable but well... boring.
[*]Fadora - Ugh... I can't go back to RPM!
[*]Gentoo - I just don't have that kind of time!
[*]Slackware - My firewall yes, my desktop NO!
[*]Mandriva - Huh?
[*]Jolicloud - Just kidding...
[/LIST] 

I have never heard of Pardus until you mentioned it, looking to load up a VM and check it out so thanks for the suggestion. What is the support for packages like? Is it Debian based?

I have no idea at this point so any suggestions are awesome!

Cheers,

Hank

Like your list. :D  You missed OpenSuse. I'll presume this was for a political reason. ;) :D

Pardus is pretty much a fresh new Linux. It has it's own packages (PiSi, or .pisi), and isn't based on any other distro. I'm really enjoying it at the moment. It's fairly quick, very pretty, and fun to use everyday. I will add though, there's not a great deal of software in the repos, but I imagine as the distro gathers pace you'll see that change. I don't mind waiting. :)  It's had no bother at all with any of my hardware, and it ships will all those craaaazy codecs everyone wants. I didn't really have to do anything other than add a couple of bits of software after installing, like Amarok, Chromium, VLC etc. Really sweet. Hope it gathers some traction.

Off topic I suppose but meh. :)

---

### Post by Kupfer on 2011-01-25
I left Ubuntu Maverick because of this bug too (I'm still running Lucid), but I will be back for Natty if this bug is resolved. Unfortunately it doesn't look like it because neither Ubuntu nor Gnome want to accept responsibility - as correctly noted by others too. 

I'm running Pardus 2011 now (and loving it) but unfortunately for me there is a bug regarding Date & Time settings not lasting after reboot (doesn't seem to be widespread though... my usual bad luck). So I'm actually looking at Scientific Linux. I have no problem with rpm based distros (thanks to my Fedora experience), it uses Gnome, and the fact that it is based on Red Hat Enterprise Linux and is created by the guys at CERN are very good credentials! This Ubuntu bug reminded me that maybe it is time to leave cutting/bleeding edge behind in favor of rock hard stability. I tried Scientific Linux and although it was outdated, it made a very good impression on me. The new version is currently in beta and until the final is released I will be distrohopping. Maybe its finally time to give Opensuse a serious look. I may have had my problems with it in the past (mostly finding it relatively uninspiring), but stability was never one of them.

The fact that so many of us are seriously considering changing to other distros shows how badly the Gnome or Ubuntu folks (I suspect its more of an Ubuntu problem) need to fix this bug.

---

### Post by Kalimol on 2011-01-25
The Gnome Settings Daemon thing fixed it for me permanently. So that didn't work for everyone? What about making a script to run it, then restart Nautilus, to run after logging in?

Really, if it's that troublesome, why not just switch to KDE or XFCE?

---

### Post by BigSilly on 2011-01-25
> **Kupfer said:**
> I'm running Pardus 2011 now (and loving it) but unfortunately for me there is a bug regarding Date & Time settings not lasting after reboot (doesn't seem to be widespread though... my usual bad luck).

Hmm, can't say I've had that bug either. There is a current one regarding the display showing some funny symbols at the top on log in, but they're on it and it's nothing deal breaking. Glad you like it though and it's not just me. :)  I like OpenSuse too in spite of the various campaigns going off (not that I particularly disagree with their sentiments, I just like the OS). Will give it a look again on the next release for sure, but I'm gonna stick with Pardus for a while and see how it progresses. 

> **Kalimol said:**
> The Gnome Settings Daemon thing fixed it for me permanently. So that didn't work for everyone? What about making a script to run it, then restart Nautilus, to run after logging in?

Really, if it's that troublesome, why not just switch to KDE or XFCE?

Not fixed permanently here. Still getting random theme changes on random log ins. For my part though I'm still using Ubuntu and hope it gets fixed, but it's interesting to note neither Ubuntu nor Gnome want responsibility. Personally, knowing nothing about coding at all, I suspect it's it's an Ubuntu issue. It doesn't turn up on other distros as has been noted previously, which is a good indicator surely. I'd switch to KDE on Ubuntu but it just doesn't feel the same as a proper KDE distro. Just imho. And I'm not a big fan of XFCE. Plus, that's all a bit of a shoo in. Shouldn't Gnome be working properly?

Fingers crossed someone hands it some love and fixes it. :)

---

### Post by Johni0574 on 2011-01-25
> **Kalimol said:**
> The Gnome Settings Daemon thing fixed it for me permanently. So that didn't work for everyone? What about making a script to run it, then restart Nautilus, to run after logging in?

Really, if it's that troublesome, why not just switch to KDE or XFCE?
 It is that troublesome unfortunately... Its changing the look of the OS entirely mid session or on boot..It just should not happen ever, and shouldn't require a workaround that does a partial fix..."Gnome Settings Daemon" did work to fix the boot issue albeit partially here which i posted before..My Gnome panel stays the way it should on boot, but my window decoration still reverts to Gnome theme default.. I've had 2 mid session reverts of the entire theme.. Embarrassing also when your showing someone the beauty of Linux then to have frankenstein flash his junk at you and then he wont put it away.. " oops, huh-huh-huh (i chuckle) he does that sometimes.." ewwww, no i dont think so! One more comparison? Sure, why not..Its like the random porn popup mid session in windows except its 10 internet explorer windows all missing their title bars, and it locks up your Win XP... :popcorn: Ubuntu is still wonderful and i will continue to use it, it seems like such an amateurish bug to have this far into Ubuntu's life so lets not downplay this issue to be resolved with a partial user based workaround..

> **Kalimol said:**
> Not fixed permanently here. Still getting random theme changes on random log ins. For my part though I'm still using Ubuntu and hope it gets fixed, but it's interesting to note neither Ubuntu nor Gnome want responsibility. Personally, knowing nothing about coding at all, I suspect it's it's an Ubuntu issue. It doesn't turn up on other distros as has been noted previously, which is a good indicator surely. I'd switch to KDE on Ubuntu but it just doesn't feel the same as a proper KDE distro. Just imho. And I'm not a big fan of XFCE. Plus, that's all a bit of a shoo in. Shouldn't Gnome be working properly?

Fingers crossed someone hands it some love and fixes it.

I like your post so much i was going to push the "like" button..

---

### Post by lancest on 2011-01-26
For several years I've noticed Ubuntu having loading problems with:
[LIST=1]
[*]Titlebars
[*]Themes.
[/LIST]

Occurs randomly, just enough to spoil my idea of perfect computing.

---

### Post by Copper Bezel on 2011-01-26
> It is that troublesome unfortunately... Its changing the look of the OS  entirely mid session or on boot..It just should not happen ever, and  shouldn't require a workaround that does a partial fix..."Gnome Settings  Daemon" did work to fix the boot issue albeit partially here which i  posted before..My Gnome panel stays the way it should on boot, but my  window decoration still reverts to Gnome theme default.. I've had 2 mid  session reverts of the entire theme.. Embarrassing also when your  showing someone the beauty of Linux then to have frankenstein flash his  junk at you and then he wont put it away.. " oops, huh-huh-huh (i  chuckle) he does that sometimes.." ewwww, no i dont think so! One more  comparison? Sure, why not..Its like the random porn popup mid session in  windows except its 10 internet explorer windows all missing their title  bars, and it locks up your Win XP... :popcorn:  Ubuntu is still wonderful and i will continue to use it, it seems like  such an amateurish bug to have this far into Ubuntu's life so lets not  downplay this issue to be resolved with a partial user based  workaround..

I guess I got desensitized to it before I got the fix. It scared the crap out of me the first time, and it *is* terribly unprofessional-looking; I know what you mean about more or less not wanting to have to apologize for your operating system. 

I haven't had the midsession thing happen, ever, though. That's doubly disturbing.

---

### Post by freakengine on 2011-01-26
I've recently installed Maverick on an Acer Aspire One netbook and have had this issue rear its ugly head.  Thing is, I have Maverick installed on a desktop since October 2010 and this bug has never surfaced on that machine!  Could it be a resource issue?

---

### Post by Johni0574 on 2011-01-27
> **Copper Bezel said:**
> I guess I got desensitized to it before I got the fix. It scared the crap out of me the first time, and it *is* terribly unprofessional-looking; I know what you mean about more or less not wanting to have to apologize for your operating system. 

I haven't had the midsession thing happen, ever, though. That's doubly disturbing.

The midsession revert has only happened the 2 times.. I was using an mp3 re-tagger called "puddletag"  and the second mid session revert i was browsing the Ubuntu software center... I was also desensitized to the issue before i found this forum thread..I will check here daily for new information, but right i have nothing more to add..

---

### Post by Kupfer on 2011-01-27
> **freakengine said:**
> I've recently installed Maverick on an Acer Aspire One netbook and have had this issue rear its ugly head.  Thing is, I have Maverick installed on a desktop since October 2010 and this bug has never surfaced on that machine!  Could it be a resource issue?

I have the bug on a netbook too. Asus EeePC 1005PE.

---

### Post by tzily on 2011-01-29
goddamnit, this happened again
someone fix it already

---

### Post by tha_chriz on 2011-01-29
hello,
Bug is also on my notebook.

Waiting for some cure.
Bye
Chris

---

### Post by Copper Bezel on 2011-01-29
I had it happen again last night. This time, I had to kill gnome-settings-daemon and restart it - it was there, but it clearly wasn't doing its thing.

---

### Post by moz_21 on 2011-01-29
Mine has been doing it also. Deleting ~/.gconfd/saved_state" had been fixing it, but not anymore. Nothing seems to be working for me.

Edit: removal of the Nvidia proprietary driver brought back the correct theme. However, I lost the TwinView feature.

---

### Post by leadpen on 2011-02-06
My netbook has this problem too. A few weeks ago, the problem had accured randomly - but now it shows up on every reboot. Also unity seems to have a similar problem - so its not only a gnome bug?
Has someone made any steps forward to solve this problem?

---

### Post by Kupfer on 2011-02-06
I removed EVERY installed nvidia related package my Synaptic listed as search results for 'nvidia' as multiple people reported that removing one or the other nvidia package solved the problem for them. But even after removing ALL nvidia related packages listed, the problem still pops up. 

So it doesn't look like an nvidia packages problem.

---

### Post by leadpen on 2011-02-06
I just removed any nvidia-related packages, too. The problem still exists (on every reboot).

---

### Post by jazzworksweb on 2011-02-06
this is happening to me also. this is a fresh 10.10 install. none of these suggestions have fixed it. I've tried deleting gnome settings, i.e. ~/.gnome2 and ~/.gconfd etc etc, I've tried changing the theme, I've tried removing proprietary drivers (nvidia and broadcom) but to no avail

the "fix" for this issue - logging out and then logging back in - is the most annoying time wasting aggravating "fix" I can possibly imagine.

this is extraordinarily unprofessional and makes me loose faith in Ubuntu as a legitimate alternative to The Other OS (TM)

---

### Post by msandoy on 2011-02-06
Hi.

I had this problem, and I think I have found a sollution.
Do a : sudo gconf-editor
Go into apps>nautilus>preferences, and scroll all the way down. The next to last item should say theme. edit the item, and remove the word default.
Close gconf-editor, log out and log back in. Now the themes should show up correctly in nautilus again. At least it worked for me, with nVidia GFX and 10.10 64bit.

---

### Post by leadpen on 2011-02-07
Thanks!!! WIth the 'gnome-settings-daemon' under System -> Preferences ->Startup Applications and the steps described as above, the problem really seems to be fixed (tested with a few restarts).

---

### Post by rookcifer on 2011-02-09
This bug hadn't been happening to me for several days, then when booting while ago, I noticed it was back.  The interesting thing, however, is that during boot I noticed that "ureadahead" had crashed (I got the little warning message during boot for a split second).  Would this have something to do with it?

---

### Post by sosukeinu on 2011-02-09
I can't be sure, but it has been a month for me since this bug last appeared. It seemed to go away after installing nautilus-elementary and the orta theme. I've restarted probably 50 times, sometimes after a few seconds, sometimes after the computer sitting all night. One time I had to use compiz-fusion to restart my window manager because the bar across the top of the windows didn't show up, but nautilus was not affected. It's a shot in the dark, but is anyone who is experiencing this problem running nautilus-elementary?

---

### Post by neglect on 2011-02-09
Just wanted to add my experience as well: I installed Lucid 10.10 Maverick two days ago and experienced this very same issue of resetting themes on multiple occasions. The first solution I found was deleting most of the hidden folders in the home folder such as .gconf. While this fixed the problem it also removed all my custom icon settings, fonts, email setup in Evolution and a few other things. Not advisable. 

Then there is the log out - log in option. Seems to work fine, disadvantage is the... well... log in - log out part of it. 

The workaround to restart the gnome-settings-daemon worked best for me so far. I added it to my start up and hope this will solve the problem. I must say I'm a bit disappointed by this as stability was the reason I returned to Linux after my Windows 7 had once again succumbed to BSOD's. I might try a few of the distros mentioned earlier in this thread.

---

### Post by federal_topone on 2011-02-09
> **Kupfer said:**
> I have the bug on a netbook too. Asus EeePC 1005PE.

on my acer notebook (4738) also found a bug, touchpad not working:(:(






[MY BLOG]("http://syahmei.blogspot.com")

---

### Post by Orbital_sFear on 2011-02-10
Hey Guys,

My issue wasn't fixed until I restarted gnome-settings-daemon.

 Here's what I did, it works 100% of the time, but its a total hack.
 Go in synaptic, reinstall nautilus. (Prop not needed, but I did it, so it might matter)



 I made a one liner shell script that runs when my computer starts:
sleep 5; ps -aef | grep gnome-settings-daemon | grep -v grep | awk '{ print $2 }' | xargs kill -9; sleep 2; gnome-settings-daemon


Save that to a script and then have it run in the startup programs.



 This completely 'fixed' the problem, but again, total hack and would like to know why gnome-settings-daemon is having issues in the first place.


 -Orbital

---

### Post by Kupfer on 2011-02-10
> **Orbital_sFear said:**
> I made a one liner shell script that runs when my computer starts:
sleep 5; ps -aef | grep gnome-settings-daemon | grep -v grep | awk '{ print $2 }' | xargs kill -9; sleep 2; gnome-settings-daemon


Save that to a script and then have it run in the startup programs.


I tried it, and indeed, the script restores some of the theme BUT unfortunately it doesn't restore the theme inside Nautilus! So having this script run at startup results in automatically restoring the theme for the panels, but once you go into Nautilus, you see that it still shows the ugly, wrong theme. At least that's the case for me...

> **msandoy said:**
> Hi.

I had this problem, and I think I have found a sollution.
Do a : sudo gconf-editor
Go into apps>nautilus>preferences, and scroll all the way down.  The next to last item should say theme. edit the item, and remove the  word default.
Close gconf-editor, log out and log back in. Now the themes should show  up correctly in nautilus again. At least it worked for me, with nVidia  GFX and 10.10 64bit.

Unfortunately, this fix doesn't work for me either. 

> **leadpen said:**
> Thanks!!! WIth the 'gnome-settings-daemon' under  System -> Preferences ->Startup Applications and the steps  described as above, the problem really seems to be fixed (tested with a  few restarts).

Nope, unfortunately, msandoys fix doesn't work with putting gnome-settings-daemon in the Startup Applications either.


This is getting really annoying, the Canonical guys should be much active on Launchpad, given the severity of the bug.

I don't want to install Natty thinking somehow the bug has magically resolved itself (Someone testing Natty Daily Builds? Does the bug surface? Wouldn't be surprised if it doesn't) and then two months later having it appear again, because the problem wasn't attended to during Maverick!!

---

### Post by Copper Bezel on 2011-02-10
> I tried it, and indeed, the script restores some of the theme BUT unfortunately it doesn't restore the theme inside Nautilus! So having this script run at startup results in automatically restoring the theme for the panels, but once you go into Nautilus, you see that it still shows the ugly, wrong theme. At least that's the case for me...

Add killall nautilus to the last line of the script. The "sleep" delay on the gnome-settings-daemon means that Nautilus loads before the Gnome Settings Daemon does, which means it's not affected. Since Nautilus is a "Required Session," it'll restart as soon as it's killed, and since the Gnome Settings Daemon will already be running when that happens, it'll load properly.

Quite a kludge, and I'm glad the startup application listing worked by itself for me, but it's just a matter of getting the right things to load at the right times.

---

### Post by Kupfer on 2011-02-10
Thanks, Copper Bezel, adding killall nautilus to Orbital sFear's script resulted in Nautilus displaying the correct theme too. It's not a perfect solution (I could see the script in action on startup as it was correcting the wrong theme, but that's no biggie) but it's the only solution we have at is point. Thanks, guys!

Still, I would like to see the Canonical team working on this more... or at all!__

---

### Post by tofudrifter on 2011-02-14
I have also been having this issue with Maverick, although only on my AMD pc, I have another pc and a netbook where this issue has not arisen at all.

After skimming this thread only fix I've found that works is to kill/restart gnome-settings-daemon and then kill nautilus.

---

### Post by Copper Bezel on 2011-02-14
Right, but again, you can make that a script with a delay and have it run on startup, so that other than a momentary flicker, you don't have to worry about it. Some of us aren't having to add the delay, and I don't have to include Nautilus in the whole thing, either - it stopped being a problem for me with just gnome-settings-daemon as a startup app. Nautilus apparently launches after the startup applications do, including gnome-settings-daemon, so I don't have to restart it.

---

### Post by EarlsFurniture on 2011-02-17
Same issue here on Lucid 10.04 32 bit happened today with a batch of updates and a restart.

So far, a restart has resolved the issue.  Will report back if anything changes.

This makes Canonical look like amateurs.

And no, it apparently is not Gnome's problem, because other Gnome distros aren't experiencing this.

I've converted many people to Ubuntu in the last 6 months.  If they experience this bug, they will be lost back to winblows.

---

### Post by KJ KJ KJ on 2011-02-17
> **KJ KJ KJ said:**
> Annoyingly, I wrote this script as a workaround, and haven't yet had to use it in anger since using the "logout first" method. 

Just to say, the script I gave in that post (#108 ) has successfully restored my panel and nautilus theme several times since then.

---

### Post by Kupfer on 2011-02-18
> **EarlsFurniture said:**
> This makes Canonical look like amateurs.


It seems a user was finally able to provide a backtrace for the problem on the launchpad bugreport for this issue:
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/588155/comments/36](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/588155/comments/36)

So I guess now we will see what Canonical is made of.

So far, there isnt even a sign of someone working on it, bug is still unassigned. Hopeful I'm not...

---

### Post by hsoulen on 2011-02-18
Hi Folks.

Just a quick update from my side...

Couple of updates to Cairo Dock and the problem seems to have been resolved for me. I cannot confirm it was specifically the dock as there were a few other updates (mostly security updates for sec libs) but I am thinking it was Cairo Dock.

Best of luck and hoping the bug gets assigned!

Hank

---

### Post by rvchari on 2011-02-18
i ve been following this thread for quite some time and today i faced it !!! theme refused to touch nautilus but was functioning otherwise good.
i simply deleted .nautilus and logged out, then logged back in. now theme seems to touch nautilus.
whatever it is, i feel this bug should be fixed (cant expect one and all to write scripts or do juggleries like this !!!

---

### Post by kanaifu on 2011-02-19
@all

RESOLUTION described in post #146? - I think so (thanks @msandoy)!

I experienced the same problem for couple of weeks (Ubuntu 10.10, custom kernel compiled locally, avant-window-navigator, etc).

I thought it must be the avant-window-navigator (at first look), and my compiled kernel (at second look), hence I didn't take the time needed to search the net for similar problems.

Now I have been browsing this thread for an hour, and the explanation in one of the previous posts regarding 

   1. sudo gconf-editor
   2. /apps/nautilus/preferences/theme
   3.  --> delete "default" string
   4. restart

resolved my issue for now.

Let us see if this is indeed the general solution.


@msandoy

Thanks, this fixed the issue, at least right now immediately after the first rebooot.

Regards folk!

---

### Post by blueadept on 2011-02-19
Happens to me, with a rather old machine updated from 10.04 to 10.10... but also with a brand new machine running Natty Alpha2 + Patches.  The new machine is absolutely vanilla, I even deleted all my gnome configuration and started from scratch to see if it would continue to happen, it does.... and it happens usually within 30 seconds of logging in.

---

### Post by BigSilly on 2011-02-20
> **kanaifu said:**
> @all

RESOLUTION described in post #146? - I think so (thanks @msandoy)!

I experienced the same problem for couple of weeks (Ubuntu 10.10, custom kernel compiled locally, avant-window-navigator, etc).

I thought it must be the avant-window-navigator (at first look), and my compiled kernel (at second look), hence I didn't take the time needed to search the net for similar problems.

Now I have been browsing this thread for an hour, and the explanation in one of the previous posts regarding 

   1. sudo gconf-editor
   2. /apps/nautilus/preferences/theme
   3.  --> delete "default" string
   4. restart

resolved my issue for now.

Let us see if this is indeed the general solution.


@msandoy

Thanks, this fixed the issue, at least right now immediately after the first rebooot.

Regards folk!

Can confirm, at least for me, that this doesn't work.

:(

Just rebooted and the issue is back.

:( :(

---

### Post by BigSilly on 2011-02-20
Ah, maybe I spoke too soon. Spotted in gconf-editor later on, that after using sudo the value hadn't changed for the regular user but for root only. So I just re-entered the change in gconf-editor without sudo, and now there seems to be no problems and the value change has stayed.

Will keep an eye on it. :)

---

### Post by Isaacgallegos on 2011-02-21
> **kanaifu said:**
> @all

resolution described in post #146? - i think so (thanks @msandoy)!

I experienced the same problem for couple of weeks (ubuntu 10.10, custom kernel compiled locally, avant-window-navigator, etc).

I thought it must be the avant-window-navigator (at first look), and my compiled kernel (at second look), hence i didn't take the time needed to search the net for similar problems.

Now i have been browsing this thread for an hour, and the explanation in one of the previous posts regarding 

   1. Sudo gconf-editor
   2. /apps/nautilus/preferences/theme
   3.  --> delete "default" string
   4. Restart

resolved my issue for now.

Let us see if this is indeed the general solution.


@msandoy

thanks, this fixed the issue, at least right now immediately after the first rebooot.

Regards folk!

solved!

---

### Post by BigSilly on 2011-02-21
No it isn't. Back again on my next reboot. :mad:

Gah! This bug is doing my head in!

---

### Post by daglamier on 2011-02-21
I am having a similar issue, but it is only affecting my gnome panels. Nautilus seems ok on my build.

---

### Post by odysseusjak on 2011-02-21
This is happening to me, too. Just started happening.

---

### Post by leadpen on 2011-02-23
> **leadpen said:**
> Thanks!!! WIth the 'gnome-settings-daemon' under System -> Preferences ->Startup Applications and the steps described as above, the problem really seems to be fixed (tested with a few restarts).

The bug is back! 
It was quiet for several days, but now the bug is back.

---

### Post by BigSilly on 2011-02-23
> **leadpen said:**
> The bug is back! 
It was quiet for several days, but now the bug is back.

Yeah that's what I'm finding. It goes away, but then seems to come back with a vengeance particularly when I make any theme changes. Had it numerous times today.

---

### Post by Johni0574 on 2011-02-24
Well i've been using the "gnome settings daemon" in the startup, and the bash script to delay (by 10 seconds each) google gadgets, cairo dock, and empathy here.. So far in almost a month i've been quiet for startups with only 1 mid session nautilus revert... I still see "gnome settings daemon" initially revert the gnome default theme over to my chosen one ever so briefly on boot, and i can deal with that for now... Sad to see no news on a fix for this.. My dual boot winxp-ubuntu computer now has this issue after i updated it 3 weeks ago (the updates needed dated back several months)..I've been letting the updates install on it as they come out, hoping to see a hidden fix happen with each one but to no avail... My daughters began to exhibit this also on there acer laptops on which i put Ubuntu on also..I've used the same settings above on my Toshiba notebook to keep the issue quiet on theirs as well... I'm continuing to follow his one thread on here hoping someone finds a perma fix.. Its so disturbing to see this going on this long and such an obvious problem... Sooooo thats 4 units in one house here all of which are having this issue... :(

---

### Post by Ultraviolet_1986 on 2011-02-25
[SIZE=2]Hi everyone, I've only been using Ubuntu since Karmic but in that time, I've learned a lot and I think I may be able to help you. I'm having the same problem and have suffered it for a while. I'm using an Advent 4213 Netbook with Ubuntu 10.10 Desktop on it (because I'm not that fond of Unity).

I've found that every time my computer restarts, the theme reverts in the same way that you all have seen and suffered, and I believe I've cracked it. I found myself reasoning this way: it the theme keeps reverting but nautilus checks out as okay, then the themes themselves must logically be the issue so I found that the 'bug' is related to GTK and the Crux theme. But Crux is not installed so the theme pack(s) must be broken. When I found this out, I opened Synaptic and searched for "crux," it brought up these two packages:

gnome-themes
gtk2-engines

One was installed while the other was not so I decided to mark the installed one to reinstall. The other one I simply marked to install. Both of these took around 2Mb to download and once this was done, I changed the theme back to "Ambiance" and restarted the computer. The problem seems to have gone now. The theme would revert on every restart and I've shut down / restarted my netbook a few times and the problem has stopped (for now?).

I know we've all seen it randomly go away and come back so I'm just keeping my fingers crossed.

I just hope this helps you all. But at least we're trying eh? :smile:
[/SIZE]

---

### Post by w3rt on 2011-02-25
I often get this problem, used debian for a long time and always had this problem with gnome, now I have been getting it with ubuntu, both 10.10 and 11.04

---

### Post by Krytarik on 2011-02-25
Hi all,

as you can see, I'm not running 10.10, so I'm not experiencing this issue at all. But I'm following this issue/thread closely.

*Ultraviolet_1986*'s post brought me to an idea: How about to try if upgrading the Murrine engine to the most recent version would fix this? At least the "Light Themes" (Ambiance and Radiance) use those.

You can use the PPA of the Elegant Gnome theme to do this, it provides version 0.98 instead of 0.91 in "murrine-daily", but there may be other PPAs (if you find one more official, please post it ;-)):
[http://gnome-look.org/content/show.php/Elegant+Gnome+Pack?content=127826](http://gnome-look.org/content/show.php/Elegant+Gnome+Pack?content=127826)

---

### Post by leadpen on 2011-02-25
> **Ultraviolet_1986 said:**
> [SIZE=2]Hi everyone, I've only been using Ubuntu since Karmic but in that time, I've learned a lot and I think I may be able to help you. I'm having the same problem and have suffered it for a while. I'm using an Advent 4213 Netbook with Ubuntu 10.10 Desktop on it (because I'm not that fond of Unity).

I've found that every time my computer restarts, the theme reverts in the same way that you all have seen and suffered, and I believe I've cracked it. I found myself reasoning this way: it the theme keeps reverting but nautilus checks out as okay, then the themes themselves must logically be the issue so I found that the 'bug' is related to GTK and the Crux theme. But Crux is not installed so the theme pack(s) must be broken. When I found this out, I opened Synaptic and searched for "crux," it brought up these two packages:

gnome-themes
gtk2-engines

One was installed while the other was not so I decided to mark the installed one to reinstall. The other one I simply marked to install. Both of these took around 2Mb to download and once this was done, I changed the theme back to "Ambiance" and restarted the computer. The problem seems to have gone now. The theme would revert on every restart and I've shut down / restarted my netbook a few times and the problem has stopped (for now?).

I know we've all seen it randomly go away and come back so I'm just keeping my fingers crossed.

I just hope this helps you all. But at least we're trying eh? :smile:
[/SIZE]

Thanks for the hint, but after those steps, the problem still exists.

---

### Post by BigSilly on 2011-02-25
> **w3rt said:**
> I often get this problem, used debian for a long time and always had this problem with gnome, now I have been getting it with ubuntu, both 10.10 and 11.04

That puts the ball squarely back in Gnome's court surely.

---

### Post by TimelessP on 2011-02-26
I'm having this issue too, using Ubuntu 10.10 64. Fresh install today, not even applying updates to test this (even after updates the problem exists, so whatever prior effort(s) that may have been done did not tackle the real issue).

I suspect the problem is a race condition, when logging in, the ecryptfs mounts *after* the user's gnome session starts, so you get the unencrypted version of the user's profile (... on faster systems/hard drives such as SSDs?). This could conceivably cause a disparity between expected theme and the one it actually loads and would be difficult to point a finger at it after login is completed because your ecryptfs would have mounted by then.

This is a gut feeling, and I still need help solving it, preferably with an Ubuntu update. Thanks.

---

### Post by TimelessP on 2011-02-26
> **TimelessP said:**
> I'm having this issue too, using Ubuntu 10.10 64. Fresh install today, not even applying updates to test this (even after updates the problem exists, so whatever prior effort(s) that may have been done did not tackle the real issue).

I suspect the problem is a race condition, when logging in, the ecryptfs mounts *after* the user's gnome session starts, so you get the unencrypted version of the user's profile (... on faster systems/hard drives such as SSDs?). This could conceivably cause a disparity between expected theme and the one it actually loads and would be difficult to point a finger at it after login is completed because your ecryptfs would have mounted by then.

This is a gut feeling, and I still need help solving it, preferably with an Ubuntu update. Thanks.
OK I've disproved my own theory by logging in via the shell (on Alt F1, after boot up) and then Alt F7 and log in to Ubuntu Desktop. Even if I change the theme it stays on a &quot;default&quot; like theme. Sorry I got yours and my hopes up.

---

### Post by Ultraviolet_1986 on 2011-02-26
...that's odd - the issue hasn't returned for me (yet), but I did a few more things than I said. I didn't think they were relevant but they may just be.

When I was looking around for causes of the issue, I was toying around with *gconf-editor* and I searched for "themes" and I changed all of them from "Ambiance" and "ubuntu-mono-dark" to "default" which changed my theme automatically to the one we've all grown to hate. Farily early on in my search I came across "Crux" and realised it was not installed so I installed the themes to refresh them and changed it back to "Ambiance."

I've shut down, restarted, logged in, logged out more times than I can count and it seems to have stopped for me but that's just it - we've seen all this before. Just because mine's working at the moment, it doesn't mean it'll stay that way. I've gotten a bit paranoid about starting up my computer now to be honest.

Let's face it though, I'm definitely not going back to Windows. We'll find a way to solve this - we Linux people are a noble breed :D

I'll keep you all posted in case it happens again but there could be any number of things that set this off and for all we know, each of our problems could stem from something different. I hope not but I've seen this sort of thing happen before. There should be a fix made for it someday. It's been said that it's happened on Debian as well, but Ubuntu is built on it so it could potentially happen on any GNOME desktop. I've read elsewhere and it seems that the developers aren't too bothered about fixing it - I don't know if that's a fact though (I read it as a comment on Launchpad).

I just hope that I'm helping in some way. It may be more simple than we all expect it to be.

---

### Post by BigSilly on 2011-02-26
Gah. It'll take more than this to drive me away from Linux! I've been having a real pain in the rear recently trying to get W7 SP1 from Windows Updates. I keep my Windows 7 install up to date and virus free, but for some reason I cannot download SP1 from Updates. It just hangs and crashes, then won't shutdown. It's a small download too; about 80Mb. What's the problem? I've had two days pratting about with it, and it's sending me daft.

This, by comparison, though still a drag, isn't as painful as good old Microsoft Updates!

---

### Post by Ultraviolet_1986 on 2011-02-27
Yeah, I'm like that - I bought Windows 7 brand new when it came out and I liked is SO much that I totally turned away from Windows XD It's a shame because it promised so much and delivered so little. I rely on it for two things: Phantasy Star Universe: Ambition of the Illuminus (which I have on PS2 anyway) and iTunes because it has the best mp3 encoder (LAME's great but iTunes mp3s are just that little bit clearer). If iTunes ever came to Ubuntu, I'd never use Windows again. I'm having a shocker with my Desktop computer at the moment - I had Ubuntu on a brand-new 250Gb SATA disk and I've just found it's riddled with bad sectors. So only Windows is left :( Being skint as well means it'll take a LOOOONG time to afford another. So I started using my Netbook more and then this theme thing starts...

It's started again by the way, first thing this morning. It seems to be more aggressive than last time because I followed my steps to sorting it again and it didn't change a single thing this time. Back to the drawing board...

I'm beginning to think I may have to just back up my home folder and apt-cache and flatline my netbook - try a clean install. I didn't have this problem with my Desktop (while it worked XD) or when I was using good ol' Lucid. Oh, Lucid, why did I ever leave you? :<

Still, there must be a way to fix it. If I reisntalled Ubuntu and all the updates, chances are it would only come back again. But it seems like any fix is only temporary - I was beginning to think this may be a mythical Linux Virus but ClamAV/TK came up with nothing after scanning the entire filesystem.

---

### Post by The Cog on 2011-02-27
I've just been trying out Debian to see if it's any more stable than Ubuntu. I've been getting tired of every new version being an exploration of "What have they broken this time?". In spending a day and a half getting the nvidia drivers to work, I have seen the problem described in this thread, so it's not just an Ubuntu problem.

And sound for UT and UT2004 is broken on Debian too, so I can no longer blame the Ubuntu folks for that. I'm running back to Xubuntu, where it looks just the same every time you log in, in a boring but reassuring way.

---

### Post by BigSilly on 2011-02-27
> **The Cog said:**
> I've just been trying out Debian to see if it's any more stable than Ubuntu. I've been getting tired of every new version being an exploration of "What have they broken this time?". In spending a day and a half getting the nvidia drivers to work, I have seen the problem described in this thread, so it's not just an Ubuntu problem.

And sound for UT and UT2004 is broken on Debian too, so I can no longer blame the Ubuntu folks for that. I'm running back to Xubuntu, where it looks just the same every time you log in, in a boring but reassuring way.

Well that's the final proof then isn't it? If it's the same on Debian, then it must be a Gnome bug and not an Ubuntu one. And it was Gnome who were immediately dismissive of the bug initially.

Hope they take another look at it.

---

### Post by Kupfer on 2011-02-27
I think a bug report should be filed for the Debian developers by someone experiencing the problem on Debian. (Don't know where to do it, maybe here... somewhere?: [http://www.debian.org/Bugs/](http://www.debian.org/Bugs/))

I opened the bug report on bugzilla.gnome.org which was later closed by a developer with "GNOME cannot fix bugs in Ubuntu. Closing as NOTGNOME."

And I'm not sure I would blame the Gnome developers just yet. I'm using both Scientific Linux 6 RC (with older packages) and Fedora 14 (with the latest packages) and none of them exhibit the problem seen in Ubuntu and Debian, as we know now. So if Gnome is working fine on Red Hat based distros, it could be Debian, on which Ubuntu is built.

Of course, I'm a layman, so I'm just guessing here, but knocking on the Debian developers door seems to be the most logical conclusion, now that we know that Debian shows the symptom too. That doesn't mean it can't be a Gnome problem, but we would have a better case for it if non-Debian distros would show signs too. I will report back if I see it (and, other folks using non-Debian distros also, please do it too), but as I have said, I'm using Fedora 14 for a while now on the same netbook showing the symptom with Ubuntu and on F14 the bug didn't occur once so far.

---

### Post by Ultraviolet_1986 on 2011-02-28
I've just reformatted my netbook and reinstalled Ubuntu on it to see if the problem will occur again - I don't know if it'll help but at least if it happens again, I'll have a better idea on what's causing it - I'm keeping track of what's installed out of the ordinary like Docky, GUFW, ClamAV/TK, Bleachbit and the like because one of the programs I've installed could be the cause - something may cause the bug and it may not actually be present by default.

To be honest, I tried to install Ubuntu-Netbook and it just kept failing because the ISO was on my old hard disk, it must have become corrupted so after an entire day of burning dud copies and non-working SD Card versions, I cursed lots and then just put everything back the way it was XD

Still, the fact that Red Hat distros don't show this (that we've seen) is interesting in itself. If Debian shows this then the problem may be related to the .deb package manager and installer. I can't see how though but at least we have a conclusive fact.

If this happens again though after what I went through backing up and restoring my netbook, then Mr Flibble will be very cross...

Nah, I'll just go back to Lucid or change to KDE, either's cool - I don't care if I go over my download limit - I'm over it now after a new install (and thanks to Windows 7 and Norton 2011's constant failure to update successfully - I has a strong dislike of teh Windows, it be well mean! :< )

I'll stop now.

---

### Post by Ultraviolet_1986 on 2011-03-01
I guess I spoke too soon - it's happening again. I cannot believe how persistent this is.

I think I'll give KDE a try - at least until this issue is resolved.

Think I'll watch some Death Note and smooth it over :smile:

---

### Post by clenceo on 2011-03-01
i've been running ubuntu since 8.04. never had this happen until 10.10.

I've made a temporary switch to Linux Mint 10 "Julia" and have yet to experience this issue.

Any thoughts?

---

### Post by rvchari on 2011-03-02
> **The Cog said:**
> I've just been trying out Debian to see if it's any more stable than Ubuntu. I've been getting tired of every new version being an exploration of "What have they broken this time?". In spending a day and a half getting the nvidia drivers to work, I have seen the problem described in this thread, so it's not just an Ubuntu problem.

And sound for UT and UT2004 is broken on Debian too, so I can no longer blame the Ubuntu folks for that. I'm running back to Xubuntu, where it looks just the same every time you log in, in a boring but reassuring way.

your note is worthy of keeping track of the issues. as i am not a geek nor a programming buff, i usually take to frugal ways of sorting out probs...

everytime i get this nautilus behave its funny way by not accepting the theme, i simply delete .nautilus directory from my home folder, logout and log in again. i get back my theme ! wonder whats wrong here. is it due to .nautilus directory not updating itself with the change in the theme ? or is the theme to be configured to touch nautilus ?

a point to be given a thought !

---

### Post by motorcity909 on 2011-03-04
This hadn't reoccurred for me for a few weeks but did today when I installed Libre Office 3.3 using 

sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update && sudo apt-get install libreofficefrom the ppa.

Don't if the two are connected......

---

### Post by BigSilly on 2011-03-04
Trust me. They aren't.

It's just something that happens randomly, and it just happened to coincide with your recent software install. Sometimes it happens a lot to me, but then it'll disappear for a couple of weeks before abruptly returning and being difficult to shake, with even resetting X not always doing the trick.

I'm seriously worried this bug is going to persist through not only the Maverick cycle, but also the Natty one too.

---

### Post by tiggerntatie on 2011-03-04
This has suddenly started happening FREQUENTLY on my Ubuntu Netbook remix. The last time it happened I immediately looked and found this in my syslog:


```
Mar  4 17:43:22 eric-netbook kernel: [14362.152519] gnome-settings-[6044]: segfault at 0 ip 001c06f7 sp bfe3fdd4 error 4 in libglib-2.0.so.0.2600.1[15f000+cd000]

```

Temporary Fix: run gnome-settings-daemon on the command line to restore the settings.

---

### Post by username.1919 on 2011-03-06
Hi all. Fairly new to ubuntu and this is my first time posting. Anyways this problem bugged me for quite a while now, I've tried various fixes as described in previous posts to no avail. I was however, able to fix this problem by forcing ureadahead to reprofile by deleting *pack files from /var/lib/ureadahead.

---

### Post by BigSilly on 2011-03-07
OK, I'll try this and see if it works.

---

### Post by leadpen on 2011-03-08
> **username.1919 said:**
> Hi all. Fairly new to ubuntu and this is my first time posting. Anyways this problem bugged me for quite a while now, I've tried various fixes as described in previous posts to no avail. I was however, able to fix this problem by forcing ureadahead to reprofile by deleting *pack files from /var/lib/ureadahead.

sorry, but this didn't solve the problem - it still persists

---

### Post by castelinop on 2011-03-08
> **kanaifu said:**
> @all

RESOLUTION described in post #146? - I think so (thanks @msandoy)!

   1. sudo gconf-editor
   2. /apps/nautilus/preferences/theme
   3.  --> delete "default" string
   4. restart

 

Solved my problem so far, not sure how long it would last but hopefully until a definite fix comes out for the bug the above solution keeps the bug away.

---

### Post by adityavpratap on 2011-03-09
> **castelinop said:**
> Solved my problem so far, not sure how long it would last but hopefully until a definite fix comes out for the bug the above solution keeps the bug away.

Thanks! It seems to have sorted out my problem.

---

### Post by castelinop on 2011-03-09
> **adityavpratap said:**
> Thanks! It seems to have sorted out my problem.

Nope, the problem is still there. Lasted the whole day but after a couple of shutdowns the problem still haunts me.

---

### Post by magic75 on 2011-03-09
Had this problem for a while now, and I think I found the cause for my issues (crossing fingers). It has worked for a few days now.

My problems seems to be caused by Ubuntu One syncing. I have disabled two Ubuntu One entries in the "Startup Programs" (using swedish version) and have not had any issues since.

I noticed that there was a lot of HDD activity prior to theme reverting (gnome-settings-daemon crash), and saw that in some Ubuntu One sync log that there was a sync going on at the exact time of the crash. So I checked the bug reports for Ubuntu One and waddya know...
[https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/720305](https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/720305)

---

### Post by Kupfer on 2011-03-09
Unfortunately I can't test this new theory as I don't have Maverick on  my computer anymore (happy new Scientific Linux 6.0 user here - this bug  resulted in me wanting RHEL stability), but in Ubuntu I almost always  disable a whole lot of startup entries right after installation, the  Ubuntu One service being one of them. I'm quite sure I did this also  after one of the MANY Maverick reinstalls and still had the bug appear. 

Also, some people reported in this thread that they encountered the bug on Debian which doesn't have the Ubuntu One service.


By  the way, I reported my first sighting of this bug early in December,  the thread was opened in September and many months later we're still  here without any progress. 
So I think it's obvious by now, that the  bug won't resolve itself. For this reason I still believe that the right  way to go is to somehow pressure developers to take a look at it - open  bug reports if they don't exist yet (for example for Debian, which has  the bug - unfortunately I can't report the problem, as I don't have  Debian installed) or contributing to already open ones (like the bug  report for Ubuntu: [https://bugs.launchpad.net/bugs/588155](https://bugs.launchpad.net/bugs/588155))  - to signal (loudly) that the bug isn't going away just because nobody is  looking. And really, at the moment, it seems to me that no developer is  looking into this at all!

My guess right now would be that this  problem will spill into the Natty cycle too, in which case I'm ready to  give my last remaining empty partition dedicated to a distro with one of  the new user interfaces to Fedora 15. I tested the F15 alpha image  which already uses Gnome Shell as default, the Shell was fast enough on  my netbook, so if this bug isn't resolved I will dump Ubuntu for it,  maybe not just for the Natty cycle. 
I already skipped out on  Maverick almost completely, another 6 months for Natty (or even more!  which is at this point sadly realistic) with this bug would make the  change permanent: no curiosity for Unity can keep me on board  (especially if rumors are true that it will also be installable on  Fedora at some point down the road), no more returning to Ubuntu... I  just can have my operating systems interface visually reverting all the  time!

---

### Post by azeam on 2011-03-10
> **magic75 said:**
> Had this problem for a while now, and I think I found the cause for my issues (crossing fingers). It has worked for a few days now.

My problems seems to be caused by Ubuntu One syncing. I have disabled two Ubuntu One entries in the "Startup Programs" (using swedish version) and have not had any issues since.

I noticed that there was a lot of HDD activity prior to theme reverting (gnome-settings-daemon crash), and saw that in some Ubuntu One sync log that there was a sync going on at the exact time of the crash. So I checked the bug reports for Ubuntu One and waddya know...
[https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/720305](https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/720305)

This works for me (Maverick proposed), removed Ubuntu One from startup applications and libglib doesn't crash anymore. Have tried other proposed solutions as well but that's the only thing that seems to make any difference.

---

### Post by Sarcasmo on 2011-03-10
I can also confirm that removing Ubuntu One from "Startup Applications" under "System" => "Preferences" fixes this issue on Maverick 64-bit.  :biggrin:

Thank you!

---

### Post by alex.rayu on 2011-03-10
Ubuntu One's the culprit, then.

---

### Post by BigSilly on 2011-03-10
But I don't understand how it can be when Debian users are reporting the same problems. :confused:

I seem to have another problem now, in that Compiz isn't launching the Windows manager at boot up. I've read all the fixes, and nothing works, but I suppose that's for another thread...

---

### Post by stinkeye on 2011-03-10
> **alex.rayu said:**
> Ubuntu One's the culprit, then.

Nope, doesn't do anything here.

---

### Post by leadpen on 2011-03-10
> **azeam said:**
> This works for me (Maverick proposed), removed Ubuntu One from startup applications and libglib doesn't crash anymore. Have tried other proposed solutions as well but that's the only thing that seems to make any difference.

I've disabled all startup-entries for weeks now - it changes nothing on the random behavior of this bug. It's still there.

---

### Post by Ultraviolet_1986 on 2011-03-11
Hi again, had a wicked shocker with my netbook over the past week or so - I tried to change to Kubuntu but for the life of me I couldn't stay away from Ubuntu so I changed it all back. The issue returned exactly two days after installation after everything was installed, this is the third complete re-install I have completed. And by that, I mean that I totally zero-filled my drive 3-4 times each time just to make sure that the issue wasn't a 'ghost' of a previous install.

Anyway, to cut to the chase, I've just been playing with Emerald Theme Manager and noticed that there's a bug that doesn't change your themes until you use a certain command (**emerald --replace**) and this gave me an idea:

We all know that the theme randomly changes back to what looks like 'clearlooks,' but there's Metacity and Compiz that render it. I've not had the chance to test this yet because I think I'm a day from my next revert but it is possible to restart the current window manager by using the Terminal:

**compiz --replace**
(or)
**metacity --replace**

Depending on effects, this may just give your theme a kickstart and make sure it stays that way. I REALLY hope so...

I've even went to the lengths of buying the CD bundle from the Canonical Store to see if it's just a dodgy download or not but I don't have the download limit to re-install (I gave up my apt-cache each time). When I get the chance, I'll re-install Ubuntu (again :<) but from the proper CD and see what happens.

If it IS a bad download, then I think I'll change to the 'Alternative Download' Torrent, I prefer to have the OEM install option to hand anyway :)

...by the way, if this has already been done I'm sorry - I only read the last page :)

---

### Post by azeam on 2011-03-12
> **leadpen said:**
> I've disabled all startup-entries for weeks now - it changes nothing on the random behavior of this bug. It's still there.

I re-read the thread from the beginning and perhaps we are talking about two unrelated issues. What I've been experiencing is by no means random, it crashes every single time after boot and haven't crashed once since I removed Ubuntu One from startup applications. Also it has not been crashing for weeks, more like *a* week, and I can't say for sure but I remember getting an Ubuntu One update around the same time it started. Tried to add Ubuntu One to startup applications again and it crashes right away, however the segfault I'm getting is in libglib:

```
Mar 12 10:45:53 azeam-Lenovo-G560 kernel: [ 1894.791939] show_signal_msg: 27 callbacks suppressed
Mar 12 10:45:53 azeam-Lenovo-G560 kernel: [ 1894.791946] gnome-settings-[4007]: segfault at 0 ip 003fd6f7 sp bfbeb1a4 error 4 in libglib-2.0.so.0.2600.1[39c000+cd000]
```

and not in libclipboard as I (now) understand you are getting.

---

### Post by castelinop on 2011-03-12
> **azeam said:**
> This works for me (Maverick proposed), removed Ubuntu One from startup applications and libglib doesn't crash anymore. Have tried other proposed solutions as well but that's the only thing that seems to make any difference.

Me too, I removed Ubuntu One from my Maverick system and did a couple of re-starts no problem so far but I guess Ubuntu One may not be the real problem, but until then I am happy. :p

---

### Post by electricgolem on 2011-03-15
Still no resolution?
It's really irritating.

I got RANDR errors when trying to restart the gnome daemon.
Lots of weird behaviour since the last 'update'

I hope the canonical radio silence on this is because they plan to move away from Gnome in the next release? :/

---

### Post by ubuntu-freak on 2011-03-15
It's not Ubuntu One at all, I disabled that right after intalling Maverick.

My theory is that boots and logins are too quick now, at least for Gnome. Today that GPG key thing said it hadn't been able to start when logging in, this theme bug and window decorations haven't loaded sometimes after logging in. The timing is all over the place I think. Gnome is just tripping itself up right from the start.

---

### Post by lancest on 2011-03-16
> **ubuntu-freak said:**
> 

My theory is that boots and logins are too quick now, at least for Gnome. Today that GPG key thing said it hadn't been able to start when logging in, this theme bug and window decorations haven't loaded sometimes after logging in. The timing is all over the place I think. Gnome is just tripping itself up right from the start. 

This is also what I think.  Had been seeing titlebar, indicator loading issues for a long time on Ubuntu.  Gone to 11.04 and not seeing that.

---

### Post by gofurygo on 2011-03-17
Hey guys

I had the same problem as most of you, randomly changing theme after login, fixed after log-out/login.

I added the gnome-settings-daemon to start-up but it didnt fix the bug. Then I followed rvcharis advice of deleting the .nautilus folder in the user directory... And I have to say...since then I havent been able to reproduce this odd behaviour and the bug hasnt been seen for 4 days now although Im trying to login as soon as the login prompt appears (not giving anything anytime to start in the background). So for me, so far its solved...

Cheers

EDIT: Nope, bug came back only some hours after this post. I noticed something though. I had problems to shut down my notebook after posting. It got stuck on the kill-all screen and I had to force to turn it off by pushing the on/off button a few seconds. Can this have something to do with it?

---

### Post by BigSilly on 2011-03-17
It's become really aggressive again for me over the last couple of days. A helpful chap on the Natty development forum posted this fix for me:

> **Harry33 said:**
> This is the workaround:
Add a delay (here 1 sec) before gnome-settings-daemon starts.
Change the line of the file /etc/xdg/autostart/gnome-settings-daemon.desktop:
Exec=/usr/lib/gnome-settings-daemon/gnome-settings-daemon
to
Exec=bash -c "sleep 1; /usr/lib/gnome-settings-daemon/gnome-settings-daemon"

But sadly it didn't work for me. He suggested adding different delays to the sleep variable, but again this didn't solve the issue.

---

### Post by linuxrollup on 2011-03-21
Had this bug happen to me as well but fixed it with "sudo restart gdm" and it never bothered me again. :D

---

### Post by kikashi on 2011-03-22
Since I reinstalled Ubuntu 10.10 on an SSD, I regularly see this bug. So I suspect it is indeed some kind of timing problem.

But luckily, a '[FONT="Lucida Console"]killall -9 gnome-settings-daemon; gnome-settings-daemon; nautilus -q[/FONT]' seems to take care of it until the next reboot.

---

### Post by DogMatix on 2011-03-23
I have this bug which occurs with varying frequency. In my case it always happens at start-up. Opening the appearance pane returns the theme to ubuntu panels but not nautilus.

Its not a deal breaker but I'm looking forward to a fix.

---

### Post by rvchari on 2011-03-23
> **gofurygo said:**
> Hey guys

I had the same problem as most of you, randomly changing theme after login, fixed after log-out/login.

I added the gnome-settings-daemon to start-up but it didnt fix the bug. Then I followed rvcharis advice of deleting the .nautilus folder in the user directory... And I have to say...since then I havent been able to reproduce this odd behaviour and the bug hasnt been seen for 4 days now although Im trying to login as soon as the login prompt appears (not giving anything anytime to start in the background). So for me, so far its solved...

Cheers

EDIT: Nope, bug came back only some hours after this post. I noticed something though. I had problems to shut down my notebook after posting. It got stuck on the kill-all screen and I had to force to turn it off by pushing the on/off button a few seconds. Can this have something to do with it?

the irony is i also face it once in a while and i noticed its not purely the timing issue. at times i switch on my laptop and i leave me desk. i come back after a few minutes (well after the log in prompt comes), i log in and i dont find the bug...

so its not purely the timing, something has to be seen on the desktop start up deamon picking up the correct theme @ log in or something like that.

point to ponder !!!

---

### Post by DogMatix on 2011-03-27
**A note.**

I upgraded to the development release of Ubuntu 'Natty' three days ago and since doing so I have not had this bug happen again, yet! Generally speaking I saw this bug at least every other day whilst running 'Maverick'. I'll keep you posted.

Anyone else noticed this?

---

### Post by DarkTide on 2011-03-30
Bumping the thread, because this has started happening to me in the past  two days. As soon as I open up the Appereance settings the normal theme  is applied. I have to kill and restart nautilus to have it apply it  though.I think so :)

---

### Post by BrandonC19 on 2011-03-30
It has something to do with Nautilus not being able to draw the wallpaper correctly on login, you need to open your wallpaper in an image editor and manually re-size it to your screen resolution. Happens to me all the time.

---

### Post by BigSilly on 2011-03-31
I don't see how that can be the problem. I use only the correct resolution images for my monitor all the time. :confused:

Anyway, hopefully [this means that it's finally fixed]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809"). Looks like they spotted the problem and have it sorted for Natty. I do hope this is true, as it's a pretty major issue imo. With any luck we'll see this fix released for Maverick...

---

### Post by EKRboi on 2011-04-01
Hello all this will be my first post! been a ubuntu user for a couple of years.. but never really had an issue i could not solve. Until this dang theme issue.. weird thing is that i had been running 10.10 since release without the problem. Couple weekends ago I upgraded processor from an Athlon X2 to a Phenom 1090t... loving the extra cores btw.. and picked up a samsung 64g SSD which i must say is also awesome! So i did a complete reinstall of ubuntu did some tweaking to accommodate the SSD other than that a completely vanilla system.. then ran through all updates.. everything seemed fine.. then i installed the nvidia drivers (sli system).. rebooted and it seems like no matter what i do... it reverts to the ugly grey theme (or lack of theme) everytime i reboot even if i log out first as some suggested.. when i reboot i can run gnome-settings-daemon && killall nautilus and its back to normal. I decided to try out the 11.04 so i did an update-manager -d and guess what its STILL a problem.. 

Other than some peoples signatures stating pc specs im surprised we havnt started listing pc specs of machines with the problem... im beginning to feel like its a problem with SSD's or possibly AMD processors??.. My netbook does not have this problem.. but it has a standard hard drive.. and an intel atom.. is it possible something is getting either missed or loaded prematurely? anyways im just brainstorming but i will leave my specs below

Coolermaster HAF 932
Asus M3N-HT Deluxe
Rocketfish 750watt PS (u wouldnt laugh if u knew what i paid for it as a bestbuy employee =/)
Phenom X6 1090t (Corsair H50 cooled)
2GB kingston hyper x DDR2 1066 RAM
2x XFX 9800gt 512gb
Samsung 470 series 64GB SSD
2x 2tb WD Caviar Greens

*had 6gb of ram 2 days ago.. had 2 of 2gig sticks take a crap on me  =/ with the lack of options in 1066 ddr2 memory and the price.. im just gonna have to stick it out with 2gb until i can upgrade to a ddr3 board

---

### Post by EKRboi on 2011-04-02
well 11.04 was a huge epic fail.. for me anyways.. not only did the theme issue transfer over but it was even worse. I kept losing the title bar on all windows as well.. irritating! ive grown to love ubuntu.. but i cant deal with this problem.. i reinstalled 10.10 AGAIN from DVD.. i am not going to install ANY updates and see what happens..

---

### Post by bloodorange on 2011-04-03
I'm sure it's the Ambiance and Radiance themes that are the root of these problems.  Anyway, I've had enough of this flakiness.  So, for the last few days I've been running Kubuntu.  And it's awesome!

I've tried Kubuntu and various other KDE distros over the years, but always returned to Ubuntu (Gnome).  I just "didn't get" KDE.  But now I love it.  It's so slick.  I've tried OpenSUSE 11.4 over this last week, too, but I prefer Kubuntu by a long shot.

Natty Kubuntu is looking awesome as well.

---

### Post by BigSilly on 2011-04-03
> **EKRboi said:**
> well 11.04 was a huge epic fail.. for me anyways.. not only did the theme issue transfer over but it was even worse. I kept losing the title bar on all windows as well.. irritating! ive grown to love ubuntu.. but i cant deal with this problem.. i reinstalled 10.10 AGAIN from DVD.. i am not going to install ANY updates and see what happens..

Gutted to hear that Natty users are still experiencing this. Puts a real downer on my decision to switch to it from Maverick.

I will say though that I've pretty much moved over to PCLinuxOS and KDE4 for now until Ubuntu gets sorted. I can't be doing with having to apply so many fixes at *every* boot, as I get not only the theme switching, but also the window bars disappearing and widgets not working too. I don't remember a time since I started using Linux that it's ever been so *scruffy*. :(

But we'll see. I'll keep an eye on the forum and see if people begin to report it fixed, hopefully soon. I may be tempted yet. :)

---

### Post by EKRboi on 2011-04-03
yes its very disturbing that such a huge bug keeps moving not only through development builds... but through distros as well.. I have nt used KDE in years. I know i HATED it pre Y2k.. Im really not sure where to place the blame though.. it seems like it must be a gnome issue. but at the same time im on a fresh install of 10.10 now and have upgraded and installed all my normal software EXCEPT the NVIDIA drivers and i have not had an issue.. for me it always seems to start causing a problem as soon as i install them.. and ive done it a bunch over the last couple days.. prob reinstalled 6 times... trying different combination of software and up dates.. but no matter if i install them first before updates... in the middle of updates.. or at the end thats when it starts happening. Although... GNOME3 drops in 3 days! could b the answer to our problems.. gonna float it out with the standard vid driver til then and see if the problem ever arises.

---

### Post by DarkTide on 2011-04-05
I'm running Pardus 2011 now (and loving it) but unfortunately for me  there is a bug regarding Date & Time settings not lasting after  reboot (doesn't seem to be widespread though... my usual bad luck). So  I'm actually looking at Scientific Linux. I have no problem with rpm  based distros (thanks to my Fedora experience), it uses Gnome, and the  fact that it is based on Red Hat Enterprise Linux and is created by the  guys at CERN are very good credentials

---

### Post by EKRboi on 2011-04-06
I switch over to kubuntu.. its ok... at least i dont lose my themes =P I think its visually more apealing than gnome.. but it has its quirks too! Trash bin issues.. having to hold shift while deleting files is kind of agravating. and it definatly does not load as fast as gnome. I loaded up the live fedora distro of gnome3 just to check it out.. not sure how i feel about it either... i just want a simple "start menu" it reminds me too much of the unity that ubuntu for netbooks uses.. didnt like it either.  I didnt play around with it too much but hopefully there is a way to change to a standard start menu.. what would be great if someone would take responsibility for the theme bug and fix it!

---

### Post by bloodorange on 2011-04-06
I don't think the developers realise how annoying and off-putting this bug is.

---

### Post by EKRboi on 2011-04-14
They aparantly dont realize... im forced to use KDE.. and I HATE it.. im a gamer and wine under KDE is slower by leaps and bounds vs gnome! crysis 2 for instance runs smoothly with ubuntu 10.10... its unplayable with kubuntu 10.10 and kde... what am i to do to... be forced to boot windows to game and be forced bear that crap?! it sucks! I dont want to boot into windows!

---

### Post by bloodorange on 2011-04-15
It might be worth you trying Natty.  I love it, and it's pretty stable even though it's Beta 2, and I've not had any of this theme reversion problem.

---

### Post by adityavpratap on 2011-04-15
I was facing the same issue coupled with a few minor ones like disappearing network-manager indicator in the panel. Then I tried Unity, but somehow did not like it. Gnome 3 also keeps crashing. (Yes, I know Unity and Gnome 3 together is a bad idea!) Finally I gave up on Gnome and installed Xubuntu-desktop. It seems to be working fine.

---

### Post by Kupfer on 2011-04-22
I think I just disproved the myth that the bug doesn't show in Linux Mint.

The theme reverted to gnome default on a freshly installed Mint 10 IN THE MIDDLE OF THE FRIKKEN FIRST UPDATE.

---

### Post by EKRboi on 2011-04-28
so todays the day.. 11.04 is out! anyone who was having the theme reverting issue gave it shot yet? I tried the last beta.. and not only had that issue but some others.. although i just did an upgrade i did not try a fresh install... although i am not a fan of KDE, kubuntu 10.10 is working for me without issue (other than it being much slower than gnome) for the moment.. maybe ill image my kubuntu disk and go for it when i get home this afternoon and hope for the best!

---

### Post by karmila on 2011-04-28
> **EKRboi said:**
> so todays the day.. 11.04 is out! anyone who was having the theme reverting issue gave it shot yet? I tried the last beta.. and not only had that issue but some others.. although i just did an upgrade i did not try a fresh install... although i am not a fan of KDE, kubuntu 10.10 is working for me without issue (other than it being much slower than gnome) for the moment.. maybe ill image my kubuntu disk and go for it when i get home this afternoon and hope for the best!
Yes, I have this issue.

I'm running Natty in virtualbox. At live mode it was okay, but after installed the theme always changing automatically to default gnome theme after some seconds after login. 
Even after guest-additions installed and unity can run this annoying problem still exist.

---

### Post by vagrantjoe on 2011-04-28
I was really hoping that this issue would get resolved in natty... But no... Even with unity it is the case... I suppose we need to start a new thread tittled "GNOME and UNITY revert to default theme" :-(... Is this bug so difficult to resolve? it has been there for ages.... I am starting to doubt if my decision to dump windows was a wrong thing to do...

---

### Post by karmila on 2011-04-29
> **vagrantjoe said:**
> I was really hoping that this issue would get resolved in natty... But no... Even with unity it is the case... I suppose we need to start a new thread tittled "GNOME and UNITY revert to default theme" :-(... Is this bug so difficult to resolve? it has been there for ages.... I am starting to doubt if my decision to dump windows was a wrong thing to do...

Yes, please create a new thread.
I wonder who will want to use a modern desktop (unity) with an old school ugly theme. :(

---

### Post by BigSilly on 2011-04-29
This is one of the bugs that's made me move to a new distro. I like the look of Unity, and I love Ubuntu and the Debian base. What I can't cope with is stupid bugs like this. :(

I'm really sad that it's turned up in Natty. Double :(

---

### Post by lancest on 2011-04-29
I've only seen this bug happen a few times in 11.04. 
Been using Natty for 30 days on 4 machines.
Much better situation that before.

---

### Post by BigSilly on 2011-04-29
It shouldn't exist at all, and the random nature of it is what makes it all the more annoying.

---

### Post by lancest on 2011-04-29
What is Unity sitting on top of? The old Gnome panel theme?  I've got questions about the wisdom of that.  I'm sure there would be no such loading behavior in KDE or XFCE.

---

### Post by TwoStep on 2011-04-29
i got that problem on ubuntu 11.04 running on a virtual machine

---

### Post by stinkeye on 2011-04-29
Happened once already on a Natty.

---

### Post by James_said_lol on 2011-04-29
Ok, that bug definitely has to do something with the sequence of start-up applications I guess (for example I have firefox in start-up apps with a pinned tabs and sometimes my wireless comes after firefox so the pages are not loaded). It looks really similar. That bug appeared on my machine after I installed Yakuake and some KDE updates came a few days after. So that yakuake use KDE workspace. I use it because it is faster (it is already loaded - which means its in start up with a few more processes I have noticed). The first time that I saw that bug was after I installed that KDE updates (~20 april) and change my Yakuake skin to plasma (even more KDE). So I applied the default skin -> reboot and it was fine..after the next reboot. So my bet is for the processes sequence, not gnome/kde compatibility or whatever.
As the guys said before when you run appearance it fixes the frames and almost everything but the file explorer. The funny thing is if you run "sudo nautilus" it has the modified theme while the user nautilus is with the default. 
So a simple "nautilus -q" in the start up scripts fix the problem. I haven't restarted but I'm pretty sure it will work just fine. Except may be we should add a script to open and close appearance, if it is not fine. Good luck.

---

### Post by Kupfer on 2011-04-29
I think it's not a good time to be a linux user right now. I'm running out of distro choices because of this bug:

-  Ubuntu: This theme reverting bug - pretty major in my opinion, Unity -  anyone asserting that it is at least as usable or more usable as gnome  2.x must be either joking or is deeply in denial. Unfinished product  released too early (typical Canonical), to me it's like working with one  arm tied behind my back

- Fedora: I tested the beta image and to  my surprise, Gnome 3 is even worse than Unity, especially on a netbook  it is unusable. Theme is way too big and pushes window contents out of  sight on netbooks, so I can't even complete a proper update. Pretty  amazing, considering these new desktop environments are basically  following a netbook style.
Also , how come neither of the two new  desktop shells permit copy-pasting stuff into the Alt+F2 'run a command'  window? That's pretty basic functionality (for example when following  how tos), it's mindblowing that it's not doable

- Linux Mint:  The great hope regarding a usable interface, since it won't be using  Unity nor Gnome Shell in the future. But, you guessed it, the Ubuntu  edition inherits this theme reverting bug - as I documented here  earlier. The Debian Edition is great, but not yet ready for prime time,  the rolling releases break stuff constantly (destroyed my Grub the last  time)

- Scientific Linux is fine, but it's very maintanence-heavy  for which most people won't have the time. And it is breakable too,  which I was able to do by foolishly mixing conflicting third party  repositories. 

So what remains? To me KDE - it's not perfect (I  don't like how resource heavy it is and it's too stylised for me), but  doesn't have this theme reverting and has extremely good usability. In  my experience OpenSUSE does the best implementation (Pardus and PCLOS  too, especially Pardus, but the limited number of packages makes it a  little bland) so I'm using openSUSE 11.4 now - and I'm loving it! KDE  4.6 as implemented in openSUSE is pretty fast, even on my netbook. 

But  it's pretty sad, that it has come to this: That I'm basically down to  one major distro I can use because of bugs that go unfixed for months  and general bad turns regarding Gnome and user interfaces. But at least  I'm lucky that the one remaining big distro is that good. Still, it's  sad, I was a Gnome guy all along, and now I possibly won't be in the  future.

---

### Post by BigSilly on 2011-04-30
While I agree about the bugs in Ubuntu, I don't agree about the usability of Gnome 3. I'm finding it excellent, and I'm looking forward to putting it on our netbook. I personally think it's a great time to be a Linux user!

I would say PCLOS is well worth your time as much as OpenSuse. I'm dual booting both and they're both great, though PCLOS only has 32 bit available.

---

### Post by karmila on 2011-04-30
> **James_said_lol said:**
> Ok, that bug definitely has to do something with the sequence of start-up applications I guess (for example I have firefox in start-up apps with a pinned tabs and sometimes my wireless comes after firefox so the pages are not loaded). It looks really similar. That bug appeared on my machine after I installed Yakuake and some KDE updates came a few days after. So that yakuake use KDE workspace. I use it because it is faster (it is already loaded - which means its in start up with a few more processes I have noticed). The first time that I saw that bug was after I installed that KDE updates (~20 april) and change my Yakuake skin to plasma (even more KDE). So I applied the default skin -> reboot and it was fine..after the next reboot. So my bet is for the processes sequence, not gnome/kde compatibility or whatever.
As the guys said before when you run appearance it fixes the frames and almost everything but the file explorer. The funny thing is if you run "sudo nautilus" it has the modified theme while the user nautilus is with the default. 
So a simple "nautilus -q" in the start up scripts fix the problem. I haven't restarted but I'm pretty sure it will work just fine. Except may be we should add a script to open and close appearance, if it is not fine. Good luck.

None of your workarounds work for me.

I didn't add any applications to startup yet, but I already got this bug.

Restarting nautilus do nothing for me. Even after I changed my default file manager to pcmanfm, it suffer the same bug as nautilus.

I think somehow gnome won't save any settings applied.

---

### Post by el_koraco on 2011-04-30
> **Kupfer said:**
> 
So what remains? To me KDE - it's not perfect (I  don't like how resource heavy it is and it's too stylised for me), but  doesn't have this theme reverting and has extremely good usability. In  my experience OpenSUSE does the best implementation (Pardus and PCLOS  too, especially Pardus, but the limited number of packages makes it a  little bland) so I'm using openSUSE 11.4 now - and I'm loving it! KDE  4.6 as implemented in openSUSE is pretty fast, even on my netbook. 




You could give Kubuntu Natty a try. Most paople who have been in the dev process say that it's probably the best implementation of 4.6 at the moment. You can expect Suse to be a little more stable in the short term, but Kubuntu only has two or three bugs that need to be ironed out, and they are upstream related, being worked on.

---

### Post by Krytarik on 2011-04-30
> **karmila said:**
> 
Restarting nautilus do nothing for me. Even after I changed my default file manager to pcmanfm, it suffer the same bug as nautilus.

I think somehow gnome won't save any settings applied.
Please see these recent threads with summed-up workarounds, which originated in the very thread we are currently in:
[http://ubuntuforums.org/showthread.php?t=1722179](http://ubuntuforums.org/showthread.php?t=1722179)
[http://ubuntuforums.org/showthread.php?t=1724702](http://ubuntuforums.org/showthread.php?t=1724702)

Greetings.

---

### Post by BigSilly on 2011-05-02
So, I've been on Natty a day now, and I've seen this bug once, which was straight after I installed it. My heart fell over. :(  However, since I disabled UbuntuOne in startup applications I haven't seen it again. Obviously it's early days yet, but I'm hoping this is enough to sort it, though I *think* I tried this on Maverick and it didn't work. We'll see. Otherwise Ubuntu and Unity are fantastic. :)

---

### Post by karmila on 2011-05-05
> **BigSilly said:**
> So, I've been on Natty a day now, and I've seen this bug once, which was straight after I installed it. My heart fell over. :(  However, since I disabled UbuntuOne in startup applications I haven't seen it again. Obviously it's early days yet, but I'm hoping this is enough to sort it, though I *think* I tried this on Maverick and it didn't work. We'll see. Otherwise Ubuntu and Unity are fantastic. :)

Finally I installed Natty on my PC 4 days ago. And it is fine until this morning, this bug happens to me again. I read your post and then I disabled UbuntuOne from Start Up Applications and the bug disappeared after logout and log in back :)

Unfortunately disabling UbuntuOne service at start up doesn't help on my VirtualBox installation.

> **Krytarik said:**
> Please see these recent threads with summed-up workarounds, which originated in the very thread we are currently in:
[http://ubuntuforums.org/showthread.php?t=1722179](http://ubuntuforums.org/showthread.php?t=1722179)
[http://ubuntuforums.org/showthread.php?t=1724702](http://ubuntuforums.org/showthread.php?t=1724702)

Greetings.

Thanks, I tried that on my VirtualBox installation but the bug still doesn't want to go away.

---

### Post by Krytarik on 2011-05-06
> **karmila said:**
> 
Thanks, I tried that on my VirtualBox installation but the bug still doesn't want to go away.
Did you already try a startup command like this!?:
```
sh -c "sleep 25; killall gnome-settings-daemon; gnome-settings-daemon; killall nautilus"
```

---

### Post by Kupfer on 2011-05-06
I have to say, I'm forced to revise my previous, violently skeptical position regarding Unity. I reinstalled Natty as I felt I was very unfair the first time, and I have to say, although it isn't a finished product it is quite stable and usable.

As for the bug - I'm using an Asus EeePC 1005PE and the theme reverting showed regularly - but so far did'nt show in Natty. I too disabled Ubuntu One in the startup entries - maybe that has something to do with it.

---

### Post by Krytarik on 2011-05-06
> **Kupfer said:**
> I have to say, I'm forced to revise my previous, violently skeptical position regarding Unity. I reinstalled Natty as I felt I was very unfair the first time, and I have to say, although it isn't a finished product it is quite stable and usable.

Respect! ++

---

### Post by antekone on 2011-05-10
Same situation here. Just installed Natty on VMware. My VM doesn't have acceleration turned on, so I'm using Classic version of GNOME desktop. Each time I login, after 5-10 seconds the theme is reset to default GTK+ theme. When I open up the terminal, **restart gnome-settings-daemon** and all **nautilus** instances like this:

```

kill -9 <gnome-settings-daemon's pid>
killall nautilus

```the theme gets back to normal (correct one), and I'm experiencing no crashes since then. Until next restart that is ;).

This is quite uncomfortable. Good thing I've installed Natty on a VM first, not my box ;)

---

### Post by meddyuk on 2011-05-10
I never experienced this problem on Maverick, however i upgraded to Natty last week and i experience it pretty much every log on.
 
Im running the Mac 4Lin theme with Awn dock. Sometimes i log in and that them will be present, other times i log in and i get the default theme. The Wallpaper remains the same whatever.
 
I dont think its bad enough to send me running back to windows as i love Ubuntu, but its definately annoying. Whats the point in having a preference if you are forced to have a certain theme.
 
The only workarounds ive tried is the gnome-settings-daemon in Start up manager. This doesn't work.
 
Has anyone found a bonfide fix for this yet?

---

### Post by Kupfer on 2011-05-10
Have you tried unclicking the Ubuntu One entry in Startup Programs? I had this bug all the time in Maverick but (so far) not once in Natty. All I did to prevent it to appear was unclicking the Ubuntu One startup entry.

---

### Post by meddyuk on 2011-05-11
Yep did that, i unticked Ubuntu One, Bluetooth and Printer as i dont need these to start, but i dont think that this is the issue.

---

### Post by dpc.ucore.info on 2011-05-11
This is so irritating issue. I had it since 10.10. I thought it's related to my Awesome WM setup, but now I see that more people have it and must be some race condition.

What I have noticed is that during booting/logging in time there's still gnome-setting-manager process belonging to gdm user. This one probably collides with newly started session and once it finishes, the theme goes gray. So I force gdm to kill it while still being gdb user:

```
[mutex:~]% cat /etc/gdm/PostLogin/Default
#!/bin/sh
#
# Note: this is a sample and will not be run as is.  Change the name of this
# file to <gdmconfdir>/PostLogin/Default for this script to be run.  This
# script will be run before any setup is run on behalf of the user and is
# useful if you for example need to do some setup to create a home directory
# for the user or something like that.  $HOME, $LOGIN and such will all be
# set appropriately and this script is run as root.

killall gnome-settings-daemon 1>>/tmp/log.1 2>>/tmp/log.2
killall -9 gnome-settings-daemon 1>>/tmp/log.1 2>>/tmp/log.2
[mutex:~]% ls -al !$
ls -al /etc/gdm/PostLogin/Default
-rwxr-xr-x 1 root root 561 2011-05-11 13:57 /etc/gdm/PostLogin/Default
[mutex:~]%
```

So far the problem does not reappear, while previously I had it at every login.

---

### Post by Kupfer on 2011-05-13
I just had the bug appear in Natty after logging out and back in. I have Ubuntu One disabled in the Startup Applications, so yet again a confirmation that it seemingly has nothing to do with it.

**If all signs point to GDM as the culprit, I have a question to ponder: Will the planned replacement of GDM with LightDM in Ubuntu 11.10 Oneiric Ocelot finally resolve this issue?**


@dpc.ucore.info

I would like to try out your fix but your post is not clear to me.
Should I create a file called Default in /etc/gdm/PostLogin/ with the contents you posted as is, or what should I write in the script? Furthermore, should I mark it executable and put it in the Startup Programs or should it just simply reside in /etc/gdm/PostLogin/?

Thanks for your help!

---

### Post by metallus on 2011-05-14
As you can see, the script is already executable. So copy /etc/gdm/PostLogin/Default.sample to /etc/gdm/PostLogin/Default , paste the two lines in it and restart GDM (logout and login) or reboot.

---

### Post by Kupfer on 2011-05-14
> **metallus said:**
> As you can see, the script is already executable. So copy /etc/gdm/PostLogin/Default.sample to /etc/gdm/PostLogin/Default , paste the two lines in it and restart GDM (logout and login) or reboot.

Thank You! I implemented the changes, let's see if the bug reappears...

---

### Post by kjano on 2011-05-16
this is probably the same bug that I am having with gnome 3 right now: [http://ubuntuforums.org/showthread.php?t=1725221&page=3](http://ubuntuforums.org/showthread.php?t=1725221&page=3)

---

### Post by Kupfer on 2011-05-16
> **kjano said:**
> this is probably the same bug that I am having with gnome 3 right now: [http://ubuntuforums.org/showthread.php?t=1725221&page=3](http://ubuntuforums.org/showthread.php?t=1725221&page=3)

You could try dpc.ucore.info's solution (see posts 261-264). Would be nice to see if it really does work. I only had this bug appear once since I installed Natty (had it all the time with Maverick), so I only implemented dpc.ucore.info's fix as a kind of security net. The bug did not appear since but I can't verify if this is because it's rare anyway for me these days or dpc.ucore.info really works...

We need a definitive fix for this bug.

---

### Post by kjano on 2011-05-17
I get 

> gnome-settings-daemon

** (gnome-settings-daemon:23888): WARNING **: Ignoring unknown module 'org.gnome.settings-daemon.plugins.gconf'

** (gnome-settings-daemon:23888): WARNING **: Name taken or bus went away - shutting down
Segmentation fault

---

### Post by bdudek on 2011-05-26
My 11.04 amd64 machine started doing this and I loaded lightDM and removed GDM. That fixed it for me.

---

### Post by pmorch on 2011-07-21
> **bdudek said:**
> My 11.04 amd64 machine started doing this and I loaded lightDM and removed GDM. That fixed it for me.

I just did that too on my 11.04 vmware installation and that worked flawlessly.

---

