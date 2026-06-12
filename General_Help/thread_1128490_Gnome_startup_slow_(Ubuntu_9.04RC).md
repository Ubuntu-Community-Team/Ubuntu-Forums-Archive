---
title: "Gnome startup slow (Ubuntu 9.04RC)"
date: 2009-04-17
forum: General Help
---

### Post by kajivarvdw on 2009-04-17
Hello,

I've just upgraded my system to the latest Ubuntu 9.04 RC. It boots really fast, but (I think) Gnome takes a very long time start. After the splash screen disappears, there's only the little cursor on a black screen, for about 30 seconds, before the desktop appears.

I had the same issues with Ubuntu 8.10. I haven't got that much applications that startup after the boot process (actually, I think I haven't added anyone manually).

But, 30 seconds after booting only to show the desktop, is much to long for an Intel Q6600 with 4GB PC6400 ram. If you want to have more information, just ask ;).

Does anybody knows what I can do to speed it up?

Thank you very much,

Kaj-Ivar

---

### Post by sam_delta on 2009-04-19
same here, 9.04 RC, boots fast, slow login, about 20-25 seconds to a full desktop

Sam

---

### Post by sderrick on 2009-04-20
I experience the same problem of painfully slow startup for gnome...

Haven't found a solution.

---

### Post by kpkeerthi on 2009-04-20
Is there an improvement when you turn off Visual effects?

---

### Post by groverblue on 2009-04-20
I'm having the same problem.  It appears to be related to authentication, because the same delay happens when the system authenticates my running of an sudo command.  Additionally, login fails for the command line (CTRL+ALT+F1).  I don't have time to look into now, but I'll post more.

One more note: I discovered that the sudo command was REALLY slow because my network adapter was not getting initialized on boot.  I had to manually run "sudo /etc/init.d/networking restart" - it took a couple minutes to authenticate my user with sudo before the script ran.

I wonder if it's related to having the computer name in /etc/hosts mapped to 127.0.1.1:
[https://lists.ubuntu.com/archives/ubuntu-users/2007-August/120744.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-August/120744.html)

---

### Post by sderrick on 2009-04-20
> **kpkeerthi said:**
> Is there an improvement when you turn off Visual effects?

Yes there was marginal improvement, though there is still a black screen with pointy cursor for 5+ seconds..

The only effects I had on were animations and window decorations.  I turned off animations.  I won't turn off window decorations as that provides the min/max/close buttons on all application bars.

Scott

---

### Post by aeiah on 2009-04-20
is there anything in dmesg or the gdm logfile?

```

cat /var/log/gdm/\:0.log

```

---

### Post by kajivarvdw on 2009-04-20
Hi everybody!

Aeiah, this is my output for the command "cat /var/log/gdm/*.log".

```
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux kajivar-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 20 18:01:42 2009
(==) Using config file: "/etc/X11/xorg.conf"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
1240138017 e0fde87077bed23d805348d35d65aa5b  /etc/X11/xorg.conf
```

My sudo command's aren't slow at all, so I don't think it has something to do with a slow login...

Cheers,

Kaj-Ivar

---

### Post by sderrick on 2009-04-20
Heres my output from cat /var/log/gdm/\:0.log

scott@scotts-laptop:~$ cat /var/log/gdm/\:0.log

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux scotts-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 20 16:40:02 2009
(==) Using config file: "/etc/X11/xorg.conf"
WARNING: All config files need .conf: /etc/modprobe.d/nvidia-kernel-nkc, it will be ignored in a future release.

---

### Post by Greg T. on 2009-04-25
Seeing a similar issue as well. My hard drive light is blinking furiously during the blackout time, so it's not just pausing. Aside from that, I haven't a clue.

---

### Post by ngsupb on 2009-04-28
having the same problem with 9.04 :confused:

---

### Post by Static- on 2009-04-28
same issue, didnt have this problem with previous versions...


seems to me like its the new fancy wallpaper changer or something... 

HELP!!!!

---

### Post by Tom_T on 2009-04-30
Another me too !!

Must take 10 - 15 seconds from logging in to get a working desktop.
Quite a lot of that time the screen is black !

---

### Post by KVirtanen on 2009-05-01
+1 I'm afraid.

Ubuntu goes through the boot process in less than 25 seconds, then a black screen without a cursor for exactly one minute and then the cursor plus additional 15 seconds to start the Gnome session (I've got automatic login on). I've booted without the quiet or splash flags and there's nothing strange happening during the boot. But right after gdm (or another window manager for that matter) starts, well...

I've got a HP TC1100 1.2GHz, 1.5GB RAM, 40GB HDD and an nVidia graphics card. I've been trying to find a solution for this for days now.

I've tried disabling visual effects, the nVidia driver, changing to an older nVidia driver, fixed the usplash.conf splash screen resolution, checking my loopback devices, tried making a new user, tried starting in XFce4, renamed all the hidden Gnome settings folders on my home directory (rewriting Gnome settings), reconfiguring xorg.conf, disabled the majority of programs that start up.. nothing! Jaunty has a really fast boot time, but it seems that X.org is starting up REEEAALLY slowly. 

Logging off also takes at least a half a minute to a full minute, just a black screen and no activity or cursor.

I want to add that I am using the release version of Ubuntu 9.04, not the RC.

---

### Post by KVirtanen on 2009-05-03
Whoa, I added to the beginning of xorg.conf the lines

```

Section "ServerFlags"
Option "AutoAddDevices" "False"
EndSection
```and basically that removed the long blackout time after the boot splash screen. I read from the Xorg log that HAL had some trouble autodetecting the input devices, but as I have set them up manually in my xorg.conf, this autodetecting was unnecessary and just caused a long lag.

From nearly 1min 40secs I got down to 50 secs - from start of booting to a clean desktop :)

---

### Post by weidongche on 2009-05-14
Changing xorg.conf doesn't do it for me.  Same speed.  Who else has seen an improvement on Gnome startup speed with this change in xorg.conf?

---

### Post by nyarlathotep77 on 2009-05-15
> **groverblue said:**
> I'm having the same problem.  It appears to be related to authentication, because the same delay happens when the system authenticates my running of an sudo command.  Additionally, login fails for the command line (CTRL+ALT+F1).  I don't have time to look into now, but I'll post more.

One more note: I discovered that the sudo command was REALLY slow because my network adapter was not getting initialized on boot.  I had to manually run "sudo /etc/init.d/networking restart" - it took a couple minutes to authenticate my user with sudo before the script ran.

I wonder if it's related to having the computer name in /etc/hosts mapped to 127.0.1.1:
[https://lists.ubuntu.com/archives/ubuntu-users/2007-August/120744.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-August/120744.html)

Hi,

I've upgraded from 8.10 to 9.04 and I had this problem from the very first login to the new system.
My experience is very similar to what groverblue describes. Both startup login and sudo are very slow.

From dmesg I can't see anything interesting related to authentication.

Hope to get a clue about this asap.

Cheers.

---

### Post by nyarlathotep77 on 2009-05-17
I tried to update the kernel to version 2.6.29 as suggested [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1132087"), but it didn't solve the authentication problem.

---

### Post by groverblue on 2009-05-21
@nyarlathotep77

I just removed an invalid entry from /etc/krb5.conf and it fixed my problem.  You might want to check that out if you made any changes recently.  I discovered this by running wireshark (as root) while do an 'sudo ls' in a new terminal.  Be sure that you close out other applications in order to avoid getting too much output from wireshark.

Good luck.

---

### Post by nyarlathotep77 on 2009-05-22
> **groverblue said:**
> @nyarlathotep77

I just removed an invalid entry from /etc/krb5.conf and it fixed my problem.  You might want to check that out if you made any changes recently.  I discovered this by running wireshark (as root) while do an 'sudo ls' in a new terminal.  Be sure that you close out other applications in order to avoid getting too much output from wireshark.

Good luck.

Hi,

unfortunately I haven't got such a file called /etc/krb5.conf in my system. However, thank you very much for your feedback.

---

### Post by nyarlathotep77 on 2009-05-23
I sorted this problem out finally.
I needed to deactivate the authentication through the fingerprint reader.
For the record, my Jaunty is running on a IBM X41.
So checking out PIM configuration might be worth in order to get this fixed.

---

### Post by rapasoft on 2009-05-31
+1

i'm running jaunty on Thinkpad T40p, so i don't have fingerprint reader... any other ideas?

---

### Post by abrax on 2009-06-02
Hello:
     Sorry for my ignorance...but...how can i deactivate the fingerprint reader? i can't remember what fingerprint recognition program i am using...

thanks

---

### Post by rapasoft on 2009-06-03
i think that would be thinkfinger 

[https://wiki.ubuntu.com/ThinkFinger](https://wiki.ubuntu.com/ThinkFinger)

---

### Post by Yellow Pasque on 2009-06-03
Remove the stuff you don't need from System -> Startup Applications. The Tracker indexing program is known to cause issues.

---

### Post by dwaynemac on 2009-06-19
I'm having the same issue in my laptop: HP530

```
cat /var/log/gdm/\:0.log

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux devbox 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd)
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jun 19 12:39:11 2009
(==) Using config file: "/etc/X11/xorg.conf"
get fences failed: -1
param: 6, val: 0
get fences failed: -1
param: 6, val: 0
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
```

Might this be related?:

(in dmesg)
```

[   27.732937] [drm:i915_setparam] *ERROR* unknown parameter 4                                                                                                   
[   27.732967] [drm:i915_getparam] *ERROR* Unknown parameter 6                                                                                                   
[   29.052269] [drm:i915_getparam] *ERROR* Unknown parameter 6 

```

---

