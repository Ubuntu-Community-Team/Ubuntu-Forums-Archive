---
title: "after KDE XFCE and XPDE instalation i can not get my login screen ??"
date: 2007-07-26
forum: Desktop Environments
---

### Post by Aamir Aziz on 2007-07-26
i've installed the KDE XFCE and XPDE in ubuntu 7.04 i did not restart my computer at that time than after 6 hours i logged into KDE and loged out than what happened, i can not see the login screen just i can see only black screen and it looks that something is loading. i wait for 3 hours but nothing happened i restart my computer many times and also pressed ctrl-Alt-Backspace. after the sixth attempt i got blue screen with message
the message was:

[B]Display server has been shut down about 6 times in last 90 seconds. it is likely that something bad is going on
waiting for 2 minutes before trying agaion on display.[/B]


i wrote the error mesage on paper and pressed again ctrl-Alt-Backspace. than i got the new message written on black screen i.e.
[B]
not staring k display manager
it is not the default display manager.
[/B]

then i did.

<ctrl>+<alt>+<f1> for cli.

i reconfigured the x server by using
Code:

sudo dpkg-reconfigure xserver-xorg


than after restarting i got another error i.e.



[B]failed to start xserver(your graphical interface)
it is likely that it is not setup correctly.
would you like to view the xservert output to diagnose 
the problem ?
[/B]
when i select yes. it shows message:

**the xserver is now disabled. Restart the GDM when it is configured correctly.**

what is xserver??? and how can i use the GUI ???

---

### Post by 65 mustang on 2007-07-26
Your problem could be in two places. [LIST=1]
[*]Xserver (the program that displays fancy x graphics to the screen)
[*]display manager (gdm, or kdm) (its a graphical logon)
[/LIST]

First try to see if the Xserver is working correctly.  Lets display a simple test screen
```

Configuration of X11 is a multi-step process. The first step is to build an initial configuration file. As the super user, simply run:

# Xorg -configure

This will generate an X11 configuration skeleton file in the /root directory called xorg.conf.new (whether you su(1) or do a direct login affects the inherited supervisor $HOME directory variable). The X11 program will attempt to probe the graphics hardware on the system and write a configuration file to load the proper drivers for the detected hardware on the target system.

The next step is to test the existing configuration to verify that Xorg can work with the graphics hardware on the target system. To perform this task, type:

# Xorg -config xorg.conf.new

If a black and grey grid and an X mouse cursor appear, the configuration was successful. To exit the test, just press Ctrl+Alt+Backspace simultaneously.
```

In this guide:
[http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/x-config.html](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/x-config.html)

---

