---
title: "Ubuntu 9.04 randomly logging me out"
date: 2009-05-05
forum: General Help
---

### Post by svivian on 2009-05-05
Every so often I get randomly logged out of Ubuntu in the middle of doing something, for no apparent reason.

Originally I thought it was due to a compiz effect (viewing windows while resizing instead of just having a rectangle), but I turned that off and it still happens. Last time I was just typing in Kate.

Any ideas what could be causing this?

---

### Post by giancast on 2009-05-05
This is not a solution just a confirmation of the problem. It happened to me five times in a row to me yesterday. I traced it to Compiz. Whenever Compiz is running and I try to view a DVD (using VLC) it will kick me out to the login screen when I try to resize the VLC window. I did it as I said five times and five times it logged me out. I turned Compiz off and everything works fine. My bet is Compiz. Why? Hopefully somebody with more experience can figure it out.

---

### Post by McMurdo on 2009-05-05
This is happening to me, too. Inspiron 1501.
Seems to be related to using Compiz, also.
See also, this hours older thread on the same issue: [http://ubuntuforums.org/showthread.php?t=1149833]("http://ubuntuforums.org/showthread.php?t=1149833")

---

### Post by 11hawkinst on 2009-06-13
So, is this still happening to you guys... or has it stopped? If it has... how did you get it to stop logging off?

---

### Post by imbjr on 2009-06-13
I wonder: is this a forced logout or the X server restarting?

---

### Post by Slim Odds on 2009-06-13
> **imbjr said:**
> I wonder: is this a forced logout or the X server restarting?

Exactly, check your log files.....

---

### Post by McMurdo on 2009-06-15
I believe that this is a logout, because my apps do crash (like next time I open Firefox it says it had closed unexpectedly). However, I would surely be willing to check a log. What file should I look at?

Also, I haven't had it happend for a while. I believe it is related to compiz or compositing. I've cut down on crazy Compiz usage, and it seems to be taking it OK. But, for instance, messing with Gnome Do/Docky interface did do it.

---

### Post by McMurdo on 2009-06-15
Arg, double post. Is there no deleting posts on Ubuntu Forums or am I just too new?

---

### Post by 11hawkinst on 2009-06-15
Okay, so for me it looks like I had a problem with Emerald Theme Manager. Every time I ran it, it would log me out within a matter of minutes. I haven't run it since and have had no problems.

Anybody else getting the same thing?

---

### Post by Slim Odds on 2009-06-16
> **11hawkinst said:**
> Okay, so for me it looks like I had a problem with Emerald Theme Manager. Every time I ran it, it would log me out within a matter of minutes. I haven't run it since and have had no problems.

Anybody else getting the same thing?

I think that Emerald looks very cool. Only problem; it crashes my system. Since I went back to Metacity, no issues.

Mine was not a "GUI shutdown", it was a hard freeze (usually a kernel panic).

---

### Post by imbjr on 2009-06-16
> **McMurdo said:**
> I believe that this is a logout, because my apps do crash (like next time I open Firefox it says it had closed unexpectedly).

I think a reset of the x server will do the same, it's not a graceful pulling of the rug from underneath Firefox.

---

### Post by McMurdo on 2009-06-19
> **imbjr said:**
> I think a reset of the x server will do the same, it's not a graceful pulling of the rug from underneath Firefox.

So the X server restart would put you back at GDM, though? If so, is there a way to change that?

---

### Post by imbjr on 2009-06-19
> **McMurdo said:**
> So the X server restart would put you back at GDM, though? If so, is there a way to change that?

Unless you have automatic login I don't think so, and Firefox would still complain that it had not been terminated correctly.

---

### Post by dbasham1 on 2009-06-25
Partial Solution.
I had same problems - freezing and getting logged out. This was from an install of 9.04 CD. Not finding a solution, I installed 8.04 from CD, did a network upgrade to 8.10, then another network upgrade to 9.04. This solved the problem. System works better than ever. In retrospect, I suppose I should have done the network upgrade to begin with. Was it the 9.04 download or the CD I burned? Dunno.

---

### Post by imbjr on 2009-06-25
> **dbasham1 said:**
> Partial Solution.
I had same problems - freezing and getting logged out. This was from an install of 9.04 CD. Not finding a solution, I installed 8.04 from CD, did a network upgrade to 8.10, then another network upgrade to 9.04. This solved the problem. System works better than ever. In retrospect, I suppose I should have done the network upgrade to begin with. Was it the 9.04 download or the CD I burned? Dunno.

Did you try a validity check on the CD? you can run one when you boot from it?

---

### Post by McMurdo on 2009-06-25
> **imbjr said:**
> Unless you have automatic login I don't think so, and Firefox would still complain that it had not been terminated correctly.

So, can I get a clarification here? 

I don't have automatic login setup. So if the X server suddenly reset, is it conceivable that I would be logged out because of that? Or no?

BTW, does ctrl+alt+backspace work to restart the X server for you? I can't recall that I've had it work in Ubuntu.

> **imbjr said:**
> Did you try a validity check on the CD? you can run one when you boot from it?

Incidentally, I have checked my CD. It's fine.

---

### Post by imbjr on 2009-06-26
> **McMurdo said:**
> So, can I get a clarification here? 

I don't have automatic login setup. So if the X server suddenly reset, is it conceivable that I would be logged out because of that? Or no?

BTW, does ctrl+alt+backspace work to restart the X server for you? I can't recall that I've had it work in Ubuntu.

Incidentally, I have checked my CD. It's fine.

If the X server dies, so does the login, that's why GDM (for Gnome sessions) comes up and asks for login details.

Ctrl+Alt+Backspace only works for me because I modded /etc/X11/xorg.conf with:

```

Section "ServerFlags"
        Option          "DontZap"               "false"
EndSection

```

Otherwise, the default is not to allow that action. The developers for 9.04 decided that this was to be the way from now on since it appears some ppl were triggering the reset accidentally.

---

### Post by glscat on 2009-07-05
Ya, I'm having the same problem. I have compiz visual effects turned off. I was wander if this might be an NVidia driver problem shutting down X ?? It's only happened a couple times since my install mid June. I am up to date on all packages.

---

### Post by McMurdo on 2009-07-05
Ah, thanks for the clarification, imbjr.

BTW, since glscat mentioned he has an Nvidia card, I'll mention I have an ATI. Interesting that it's happening on both. Maybe there is an X issue... or just as or more likely, I don't know what I'm talking about.

---

### Post by glscat on 2009-07-05
that's good info McMurdo, all data points are useful. I can take the vendor specific video drivers out of question.__

---

### Post by triften on 2009-07-13
In the past couple of weeks, my wife and I started experiencing the random logouts. I've had two in the past hour.

We are both running nVidia cards. Mine was a network upgrade from 8.10 and hers was a fresh install from a 9.04 CD.

My Xorg.0.log.old shows:
```
Backtrace:
0: /usr/X11R6/bin/X(xorg_backtrace+0x3b) [0x813518b]
1: /usr/X11R6/bin/X(xf86SigHandler+0x55) [0x80c7be5]
2: [0xb8065400]
Saw signal 11.  Server aborting.
```

---

### Post by https on 2009-07-16
i'm experiencing the same x crashes. it happens randomly in a row. signal 11 crashes (segment faults) 

[LIST]
[*] network upgrade 8.04 to 9.04, with all current updates installed.
[*]compiz off, Intel® G45 Express Chipset
[*]Linux bic 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux
[/LIST]
/var/log/Xorg.0.log.old :
```
(**) Logitech USB Receiver: (accel) set acceleration profile 0

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x813518b]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80c7be5]
2: [0xb7f0e400]
3: /usr/bin/X(BlockHandler+0x94) [0x8091204]
4: /usr/bin/X(WaitForSomething+0x124) [0x8132974]
5: /usr/bin/X(Dispatch+0x7e) [0x808d2be]
6: /usr/bin/X(main+0x3bd) [0x80722ed]
7: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ad6775]
8: /usr/bin/X [0x80717a1]
**Saw signal 11.  Server aborting.**
(II) Dell Dell USB Keyboard: Close
```

---

### Post by Laeys on 2009-08-15
I am having a similar problem: three random log outs today.  Are there any fixes?

---

### Post by svivian on 2009-08-17
> I am having a similar problem: three random log outs today. Are there any fixes?
I originally didn't think it was Compiz, but I've been running for months with most of the effects turned off and I haven't experienced this issue at all. I kept getting logged out when resizing videos in VLC and the option to view windows while resizing, but ironically with the effects disabled this is the default behaviour and I javen't had any crashes. :S

I suggest disabling a few Compiz effects and seeing if it helps. Or do it the other way: disable everything first, then enable one-by-one every few days. If you happen to find the one(s) that's causing problems for you, don't forget to let us know!

---

### Post by Laeys on 2009-08-17
I have my visual effects settings set to none, so it couldn't be compiz, right?  It's still happening so maybe I have a different problem.

---

### Post by hkais on 2009-08-31
> **Laeys said:**
> I have my visual effects settings set to none, so it couldn't be compiz, right?  It's still happening so maybe I have a different problem.

Hello Laeys,

I have the identical problem. I have more detailed infos. I am currently aggregating all possible bugs to the bug #412113 to get more attention at the problem. I think the developers do not believe, that this is really a problem....

Therefore I ask you all to switch to the following topic:

[http://art.ubuntuforums.org/showthread.php?p=7864215](http://art.ubuntuforums.org/showthread.php?p=7864215)

And to report your bug at launchpad at
[https://bugs.launchpad.net/ubuntu/+bug/412113](https://bugs.launchpad.net/ubuntu/+bug/412113)
Please provide the backtrace of /var/log/gdm (one of the files should contain it)

---

### Post by hkais on 2009-09-02
sorry proper URL is:

[https://bugs.launchpad.net/ubuntu/+bug/412113](https://bugs.launchpad.net/ubuntu/+bug/412113)

---

