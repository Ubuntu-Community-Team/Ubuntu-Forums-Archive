---
title: "multiple times a day a X-Server crash! Problems started with screen refresh issues"
date: 2009-08-19
forum: Desktop Environments
---

### Post by hkais on 2009-08-19
Hello all,

I have big problems with my Ubuntu 9.04 32bit on my Lenovo T61
uname -a: 2.6.28-15-server #48-Ubuntu SMP Wed Jul 29 09:57:16 UTC 2009 i686 GNU/Linux
lspci|grep VGA: 01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1)

I am running on compiz.

Multiple times a day my X-Server dies (screen goes black) and tries to restart. But the X-Server isn't able any more to restart. So I have to restart the complete machine.
This is very painful, especially because I work under vmware with a Windows-Instance, which also gets killed...

I have already tried to find the issue, but I have no clue how to figure out, there the problem resides.
To the history:
I had massive problems with the default shipped nvidia drivers of ubuntu. My screen got regulary distroyed (screen refresh failed). So I went to the launchpad there I installed the latest nvidia PPA driver.
Now the screen refresh problem got eased but now my x-server dies to regularly.
Currently it is so painful, that I am playing around with the idea to switch back to a mature distribution like fedora/novell.
I hope I will get any responses, because I am using Ubuntu intensively since 6.06LTS and my first tries in 2005.

best regards

---

### Post by hkais on 2009-08-21
Really nobody here who can help?

---

### Post by bchurchill on 2009-08-21
Check /var/log/syslog and /var/log/messages and /var/log/Xorg* logs for anything that might indicate a crash.  If you see something, post it.

---

### Post by WakkiTabakki on 2009-08-21
I've precisely the same setup and had more or less the same problems. Upgrading the nvidia driver to 185.18.14 fixed the problems for me. 
I added this repo:
```

deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main
```

Check out the ubuntu-x-swat page at Launchpad here:
[https://launchpad.net/~ubuntu-x-swat]("https://launchpad.net/%7Eubuntu-x-swat")

Although X is not crashing anymore one problem persists, I cannot restart the x-server of some reason. When I log out and x tries to restart, it enters a loop - the logo is briefly shown, killed and it retries... Quite annoying.

/N

---

### Post by hkais on 2009-08-21
> **WakkiTabakki said:**
> I've precisely the same setup and had more or less the same problems. Upgrading the nvidia driver to 185.18.14 fixed the problems for me. 
I added this repo:
```

deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main
```

I have installed already the PPA-drivers in the version 185.18.14. This eased the issues with the crappy screensrefreshes. It is not fixed completely (e.g. the adobe acrobat reader is still not getting screenrefreshes)

> **WakkiTabakki said:**
> 
Although X is not crashing anymore one problem persists, I cannot restart the x-server of some reason. When I log out and x tries to restart, it enters a loop - the logo is briefly shown, killed and it retries... Quite annoying.


Now (after the PPA-update) my x-server dies regularly. And it behaves then exactly as you are telling. The X-Server tries permanently to restart until it stops and says I must use the default VGA version.

Additionally, my X-Server is pretty aweful slow if it comes back from the screenlock of the screensaver. It takes about 15 seconds to refresh the screen. In this case I have to switch one time to tty and back to get the x-server in its old speed...

---

### Post by hkais on 2009-08-21
Crash protocol:

[LIST]
[*]21.8. 21:00 CET the second x-server crash today. 
The stupid user behind the keyboard seems to have fun restarting the VMware image and getting the settings back to the place before the crash
[/LIST]

---

### Post by WakkiTabakki on 2009-08-23
Does the syslog or dmesg contain anything of interest?
When you get a crash, try to note at what time it happened. The boot up again and start the Log File Viewer (under System/Administration) and check the log entries prior to the crash. kern.log may contain stuff as well, in case somehtings causing the kernel to panic...


/N

---

### Post by hkais on 2009-08-23
> **WakkiTabakki said:**
> Does the syslog or dmesg contain anything of interest?
When you get a crash, try to note at what time it happened. The boot up again and start the Log File Viewer (under System/Administration) and check the log entries prior to the crash. kern.log may contain stuff as well, in case somehtings causing the kernel to panic...


/N

I have nearly nothing. This is my last logentry
gdm[5386]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0

---

### Post by WakkiTabakki on 2009-08-24
Find anything interesting in the logs in /var/log/gdm/ ?

You probably need to check the time/date on the files in there since the logfiles gets rotated when you reboot...

Maybe you've seen these as well, but these links deal with similar a problem:
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/152648](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/152648)
[https://bugs.launchpad.net/ubuntu/+bug/140554](https://bugs.launchpad.net/ubuntu/+bug/140554)

/N

---

### Post by hkais on 2009-08-24
I found in the gdm\:0.log.2
following
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux ntp-dp 2.6.28-15-server #49-Ubuntu SMP Tue Aug 18 19:30:06 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 24 12:21:13 2009
(==) Using config file: "/etc/X11/xorg.conf"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

Backtrace:
0: /usr/X11R6/bin/X(xorg_backtrace+0x3b) [0x813518b]
1: /usr/X11R6/bin/X(xf86SigHandler+0x55) [0x80c7be5]
2: [0xb7f2a400]
Saw signal 11.  Server aborting.
 ddxSigGiveUp: Closing log
 ddxSigGiveUp: re-raising 11

---

### Post by hkais on 2009-08-24
and in :1.log.4

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux ntp-dp 2.6.28-11-server #42-Ubuntu SMP Fri Apr 17 02:48:10 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Thu Apr 30 09:29:09 2009
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
error setting MTRR (base = 0xd5000000, size = 0x00e00000, type = 1) Invalid argument (22)
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
error setting MTRR (base = 0xd5000000, size = 0x00e00000, type = 1) Invalid argument (22)

Backtrace:
0: /usr/X11R6/bin/X(xorg_backtrace+0x3b) [0x813518b]
1: /usr/X11R6/bin/X(xf86SigHandler+0x55) [0x80c7be5]
2: [0xb7f59400]
3: /usr/lib/xorg/modules//libshadow.so(shadowRemove+0x4e) [0xb66fdeee]
4: /usr/lib/xorg/modules//libshadow.so [0xb66fe3a4]
5: /usr/X11R6/bin/X [0x80c6a07]
6: /usr/X11R6/bin/X [0x811289c]
7: /usr/X11R6/bin/X [0x811ec9c]
8: /usr/X11R6/bin/X [0x81254fc]
9: /usr/X11R6/bin/X [0x80cf45e]
10: /usr/lib/xorg/modules/drivers//vesa_drv.so [0xb688ebc2]
11: /usr/X11R6/bin/X [0x80c76db]
12: /usr/X11R6/bin/X [0x816272b]
13: /usr/X11R6/bin/X [0x80e1958]
14: /usr/X11R6/bin/X [0x80cc073]
15: /usr/X11R6/bin/X [0x814bb35]
16: /usr/X11R6/bin/X [0x817cd5c]
17: /usr/X11R6/bin/X [0x814589b]
18: /usr/X11R6/bin/X(main+0x44c) [0x807237c]
19: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7b2a775]
20: /usr/X11R6/bin/X [0x80717a1]
Saw signal 11.  Server aborting.
 ddxSigGiveUp: Closing log
 ddxSigGiveUp: re-raising 11

---

### Post by WakkiTabakki on 2009-08-25
This turning into a case of the blind leading the deaf... Sorry...

But as a last (possibly futile) effort, since I have the the same laptop and have no random crashes, here's what I have installed:
- Ubuntu 64bit, Kernel 2.6.28-15-generic
- Nvidia driver 185.18.14
- xserver-xorg 1:7.4~5ubuntu18 (with xserver version 1.6.0-0ubuntu14)
(- compiz 1:0.8.2-0~ubuntu8.1)

Btw, do you run Compiz? In that case, have you tried using Metacity instead?
(By setting System->Preferences->Appearence->Visual Effects to 'None')

/N

---

### Post by hkais on 2009-08-25
Hi WakkiTabakki,

many thanks for your help!

> **WakkiTabakki said:**
> This turning into a case of the blind leading the deaf... Sorry...
Sorry I am a non native speaker. Do you mean, I hava am a noob in this case? If so, yes. I have many years of experiences in linux-servers, but the desktop isn't my special knowledge...

> **WakkiTabakki said:**
> 
But as a last (possibly futile) effort, since I have the the same laptop and have no random crashes, here's what I have installed:
- Ubuntu 64bit, Kernel 2.6.28-15-generic
- Nvidia driver 185.18.14
- xserver-xorg 1:7.4~5ubuntu18 (with xserver version 1.6.0-0ubuntu14)
(- compiz 1:0.8.2-0~ubuntu8.1)

I am running 
Ubuntu 32bit
2.6.28-15-server Kernel
NVidia dirver 185.18.14
xserver-xorg 1:7.4~5ubuntu18
xserver-xorg-core 2:1.6.0-0ubuntu14
compiz 1:0.8.2-0ubuntu8.1

> **WakkiTabakki said:**
> 
Btw, do you run Compiz? In that case, have you tried using Metacity instead?
(By setting System->Preferences->Appearence->Visual Effects to 'None')

/N

I have now deactivated again the compiz. I tried it before but with no success. I will report again if my metacity dies.

In the meanwhile i have activated apport. Maybe it helps

---

### Post by WakkiTabakki on 2009-08-25
> **hkais said:**
> Hi WakkiTabakki,

 Sorry I am a non native speaker. Do you mean, I hava am a noob in this case? If so, yes. I have many years of experiences in linux-servers, but the desktop isn't my special knowledge...


Oh, sorry. What I meant was rather that *I* was the noob in trying to help with something I don't really know much about...
BTW, that was a literal translation of a Swedish expression, so it may make absolutely no sense in English :D

Good luck!
/N

---

### Post by WakkiTabakki on 2009-08-26
Just noticed on my Karmic test machine that there is a new nvidia driver out (185.18.36), which fixes "a crash on some mobile gpu:s". Ofcourse, I don't know if it applies to you, but could be worth a try?

This PPA has it
[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

/N

---

### Post by hkais on 2009-08-29
> **WakkiTabakki said:**
> Just noticed on my Karmic test machine that there is a new nvidia driver out (185.18.36), which fixes "a crash on some mobile gpu:s". Ofcourse, I don't know if it applies to you, but could be worth a try?

This PPA has it
[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)
/N

**1st try**
I deactivated compiz so only metacity was running:
xinit:  connection to X server lost.

waiting for X server to shut down 
Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x813518b]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80c7be5]
2: [0xb7f90400]
3: /usr/lib/xorg/modules//libshadow.so(shadowRemove+0x4e) [0xb66daeee]
4: /usr/lib/xorg/modules//libshadow.so [0xb66db3a4]
5: /usr/bin/X [0x80c6a07]
6: /usr/bin/X [0x811289c]
7: /usr/bin/X [0x811ec9c]
8: /usr/bin/X [0x81254fc]
9: /usr/bin/X [0x80cf45e]
10: /usr/lib/xorg/modules/drivers//vesa_drv.so [0xb685ebc2]
11: /usr/bin/X [0x80c76db]
12: /usr/bin/X [0x816272b]
13: /usr/bin/X [0x80e1958]
14: /usr/bin/X [0x80cc073]
15: /usr/bin/X [0x814bb35]
16: /usr/bin/X [0x817cd5c]
17: /usr/bin/X [0x814589b]
18: /usr/bin/X(main+0x44c) [0x807237c]
19: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7b5d775]
20: /usr/bin/X [0x80717a1]
Saw signal 11.  Server aborting.
 ddxSigGiveUp: Closing log
 ddxSigGiveUp: re-raising 11

xinit:  unexpected signal 15.


**2nd try**
Now I installed the 185.18.36 driver.
Backtrace:
0: /usr/X11R6/bin/X(xorg_backtrace+0x3b) [0x813518b]
1: /usr/X11R6/bin/X(xf86SigHandler+0x55) [0x80c7be5]
2: [0xb7f67400]
Saw signal 11.  Server aborting.
 ddxSigGiveUp: Closing log
 ddxSigGiveUp: re-raising 11


I had never such an unstable system like the ubuntu 9.04....

---

### Post by bchurchill on 2009-08-29
I've never gotten the nVidia proprietary drivers to work.  On Arch Linux there are some open source experimental nVidia drivers which work fine for me on a GeForce 9600M...  You might be able to find the source for those and compile them.

EDIT:  here's a link.  [http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/)

---

### Post by hkais on 2009-08-31
I am aggregating the crashes in launchpad under:
[https://bugs.launchpad.net/ubuntu/+s...dm/+bug/412113](https://bugs.launchpad.net/ubuntu/+s...dm/+bug/412113)

If anybody else has this problems too, please provide your issues also there.

---

### Post by hkais on 2009-09-02
sorry proper URL is:
[https://bugs.launchpad.net/ubuntu/+bug/412113](https://bugs.launchpad.net/ubuntu/+bug/412113)

---

### Post by hkais on 2009-09-02
> **bchurchill said:**
> I've never gotten the nVidia proprietary drivers to work.  On Arch Linux there are some open source experimental nVidia drivers which work fine for me on a GeForce 9600M...  You might be able to find the source for those and compile them.

EDIT:  here's a link.  [http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/)

Hello bchurchill,

how stable are the drivers? The proprietary drivers worked for me pretty fine. Since 8.10 I have much problems with them...

---

### Post by daflame on 2009-09-16
I on the other hand have an ATI graphics card and am using OSS drivers and X crashes for me quite frequently too.

---

### Post by badook on 2009-09-21
Somehow nvidia drivers and wireless drivers are in conflict on my system, using nvidia 8600gt, Atheros AR5001X+, asus p5k/epu, intel q6600.
I found these two solutions to be working:
1. Install madwifi drivers (a little buggy on my system because often the connection speed dropped to max 20/30kb and requered me to use modprobe)
2. Install nvidia beta drivers 190.*, here's a howto: [http://webupd8.blogspot.com/2009/08/how-to-install-nvidia-190xx-drivers-in.html]("http://webupd8.blogspot.com/2009/08/how-to-install-nvidia-190xx-drivers-in.html")

I hope it can be useful for you too!

---

