---
title: "XServer seems to crash"
date: 2011-01-21
forum: Desktop Environments
---

### Post by someusername on 2011-01-21
Hi,

After some indeterminate amount of time I experience a sudden termination of all my processes, killing of the desktop environment - gnome - and a revert to the log in screen.

I'm using the proprietary ATi drivers for "1 GB GDDR5 for ATI FirePro M7820". The machine is a dell M6500 with 8GB of memory, with a resolution of 1920x1200 on two screens. The second screen is connected through VGA. Both are turned on at the same time. The default of ubuntu are otherwise running, nothing customized. I assume this means I'm using compiz.

```
$ uname -a
Linux catamorphism 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010
```

Some logs that might help from ~/.xsession_errors:

```
###!!! ABORT: X_CloseDevice: XI_BadDevice (invalid Device parameter); 11 requests ago: file nsX11ErrorHandler.cpp, line 182
_XError+0x000000F4 [/usr/lib/libX11.so.6 +0x00043E24]
UNKNOWN [/usr/lib/libX11.so.6 +0x0004A30C]
_XReply+0x00000140 [/usr/lib/libX11.so.6 +0x0004A9B0]
XSync+0x00000063 [/usr/lib/libX11.so.6 +0x0003E333]
XCloseDisplay+0x00000080 [/usr/lib/libX11.so.6 +0x0001CE50]
UNKNOWN [/usr/lib/libgdk-x11-2.0.so.0 +0x000509E6]
g_object_unref+0x00000174 [/usr/lib/libgobject-2.0.so.0 +0x00010A24]
UNKNOWN [/usr/lib/firefox-3.6.13/libxul.so +0x004CE648]
XRE_main+0x000034FD [/usr/lib/firefox-3.6.13/libxul.so +0x004D3060]
UNKNOWN [/usr/lib/firefox-3.6.13/firefox-bin +0x00001FA1]
__libc_start_main+0x000000FE [/lib/libc.so.6 +0x0001ED8E]
UNKNOWN [/usr/lib/firefox-3.6.13/firefox-bin +0x00001C89]

snip

(nautilus:1954): Eel-WARNING **: "unique eel_ref_str" hash table still has 3 elements at quit time (keys above)

(nautilus:1954): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 15 elements at quit time
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gtk-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-panel: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
evolution-alarm-notify: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
The application 'crashreporter' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 29626 requests (29625 known processed) with 0 events remaining.

```

---

### Post by someusername on 2011-01-25
bump

---

### Post by someusername on 2011-01-28
bmp

---

### Post by Krytarik on 2011-01-28
How did you install the driver?

Am I guessing right that you are running Maverick 10.10?

Do you have desktop effects, meaning Compiz is running?

If so, try running Metacity instead, in a terminal or Alt+F2:
```
metacity --replace
```
What theme do you use?

---

### Post by someusername on 2011-01-29
Hi,

Yes, that's correct. 10.10. And yes, compiz is running. Drivers: I clicked the bubble that ubuntu presented to me "This .. will run better if you install the drivers for your graphics card. Click here to do that".

Metacity: The problem with doing this is that I'm not proving that I have solved the problem. I would much rather perform some action that allows me to prove that it's fixed so that I don't have to stand in front a client in the future with red cheeks saying 'oops! An hour's worth of work just got lost because Xorg crashed, I'm sorry, but hey, I'll just send you half that time worth of invoice'.

 Just moving on to another desktop manager presented two problems: 1) experience degradation -- I don't want to degrade my desktop experience, or I wouldn't choose Ubuntu, I'd choose ArchLinux, 2) I can't be certain it's fixed.

Hence; if I can enable verbose logging to a known location of the hard-drive such that all log-outs and log-ins as well as stack-traces are logged, that would be a good step along the way. Then I'd like to know in some way that the bug is fixed.

What about the log errors I've presented?

I don't know what theme. The default, dark purple-orange-white-black theme that ubuntu gives by default.

I wouldn't mind installing the ubuntu development tools and re-compiling some C in order to solve my problem, if that's what it takes and I get a good description as how to do it exactly.

---

### Post by Krytarik on 2011-01-29
Hey, I'm trying to help you here. I made the proposal regarding Metacity, and asked about your theme because all the error messages point to the GUI, meaning applets in the panels, window-decoration and buttons.

And instead of ranting that you can't be sure that your issue is fixed, because it only arises after an indeterminate amount of time, and that don't want to "downgrade" your system, you could have just tried my suggestion to help to narrow down the issue.

Relevant logs regarding your issue are "~/.xsession-errors" and "/var/log/Xorg.0.log", respectively "/var/log/Xorg.0.log.old".

---

### Post by someusername on 2011-02-01
I know you are trying to help and I'm very grateful. I'm not ranting, or at least not trying to rant. Sorry if it seems that way.

However, the issue happens so far in between that downgrading wouldn't really help me narrow it down, which is my point. At least I don't see how it would -- would you care to educate me? Surely I would still have the same problem, but with lesser software?

I could narrow it down if I could remove the error messages one by one by fixing my system... But I don't know how to accomplish this.

---

### Post by Krytarik on 2011-02-01
Since there is apparently quite a long time between the occurances of the error, it will be hard to determine if the issue is fixed, as you said.

I did a web search on the matter with some of the terms logged into your .xsession-errors, and it seems very probable that the error originates from some kind of a bug in the running video driver.

You may try to upgrade to the latest driver packages build by Ubuntu-X-Swat. They build them from more recent proprietary drivers, than the packages in the official repo are build of, at least for Lucid/Maverick.
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```After you've done this, feel free to have some time to see if the error re-occurs.
Do you remember if you have done anything right before the error occured the last times, that you otherwise don't do?

---

### Post by hamed319 on 2011-02-04
Hi All,
I have a problem with the start up of LINUX. After starting up (when you should be asked for a password to start a session),before the session, a blue and gray screen appears:System Configuration.
I use the Alt+F6 to start a console and then I type the startx and it bring me to the session. 
what should I do?
Best

---

