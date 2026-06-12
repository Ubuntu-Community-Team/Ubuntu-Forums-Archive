---
title: "Login Loop problems (lightdm and gdm) - again, V15.04 - NEWBIE help please"
date: 2015-10-22
forum: Desktop Environments
---

### Post by robbrown2 on 2015-10-22
Hi All,

Please don't shoot me down, I am a nooby with Ubuntu (and haven't touched Linux for such a long time), but I have researched and researched this issue for the past 2 days, hour after hour, tried a lot of things I cant remember, and erased and re-installed 3 times trying things before posting.

So, the usual problem that has been reported a lot, is I get to the Login screen, type my password, the screen shows the coloured background with a cursor, after a few seconds, flashes to a black screen with the cursor in the top right, then back to the login screen. No errors or messages displayed. If I try the GUEST account, the exact same issue occurs (most people state they can get in using the guest account, I cant)

Firstly, my hardware: Compaq 515 notebook, AMD Athlon X2 processor, 2GB memory, HD Radeon mobility HD 3200 graphics (which I think is the issue) and 160GB HDD, 140GB available.

Software versions I have installed V14 and V15.04 32Bit several times (did not try the 64bit.. Should I). Fresh installs, nothing else installed. Also fails if I run Ubuntu direct from the DVD.

I have tried LUBUNUTU V15 erasing the HDD and installing and it actually works, but this problem with Ubuntu V14 and V15 (yes, I've tried both) is driving me crazy and would like to solve why just for personal gratification and would prefer to run the fuller Ubuntu version.

All I want this notebook to do, is to run 1 program. That's all it will be used for, running a program that controls my model trains. I could have easily put Windows 7 on it (which has been on it without any issues) and would have saved all this heartache and wasted time trying to find why I cant even get a Ubuntu desktop to display, but, I have been told the software I will be using is "native" to Linux.

What have I tried.:
1) Graphic Drivers in use are the Open Source version as I read several places the fglrx drivers do not contain support for the HD 3200 graphics chip.

2) I have looked at Logs (what I have pieced together I need to look at from the zillions of posts):

/var/log/lightdm/lightdm.log has one CRITICAL error:

```

CRITICAL: session_get_login1_session_id: assertion 'session != NULL' failed

```

/var/log/lightdm/x-o-greeter.log has a few warnings. The rest of the log shows normal stuff:

```

** (unity-settings-daemon:2333) WARNING **; Attempted to init Xsync, found version 3.1 error base 134 event base 03

then a few lines down from that

** (unity-settings-daemon:2333) WARNING **; unable to register client: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such method 'RegisterClient'


```

 /var/log/lightdm/x-o.log has a few lines, no errors or warnings.

3) Checked the Xsession.errors log file. I am getting a few errors, but not sure if they are the issue or how to fix them.  The errors are:

```

openConnection: connect: No such file or directory
cannot connect to britty at :0

upstart: upstart-event-bridge main process (1376) terminated with status 1
upstart: upstart-event-bridge main process ended, respawning

The above occurs 11 times

upstart: at-spi2-registryd main process ended, respawing

The above occurs 10 times

gnome-session (Unity) main process (1550) terminated with status 1

```

4) Checked the /var/log/Xlog.0.log. No errors apart that it cant load fglrx, but it does show it loads the Radeon 3200 driver and sets video attributes.

5) I have checked all the permissions on the .Xauthority and ICEauthority file. They are set correctly.

6) Tried GDM and it does the same thing.

7) LUBUNTU as mentioned, worked fine on the same notebook. yes, I know it uses LXDE not LightDM or GDM but isn't that still based on X11 which they do use?
I am reaching out and asking:
1) What Logs should I be looking at (in logical steps) to try and find the problem.
2) Would the Open Source Video Driver (which, looking at the logs is loading fine) actually be a problem and is there any other "open source" driver to try?
3) Are there anymore logs to look at apart from the ones mentioned above?
4) Anything else I could try...

On top of the 4 questions, sometimes when it goes to the black screen, I see a flash of a console with what looks like the loading of the session, however it disappears quickly. Is there anyway to view this console (CTRL-ALT-# doesn't show the same screen). I am sure if I know how to view the screen (or the log associated with the screen) then I might find the problem.

If you need to see any logs, then I am not sure how I can transfer them from the Ubuntu notebook to the computer I use for the this forum. Any help there (like transferring a log to a USB device) would be very much appreciated.

Thanks in advance,
Rob

---

