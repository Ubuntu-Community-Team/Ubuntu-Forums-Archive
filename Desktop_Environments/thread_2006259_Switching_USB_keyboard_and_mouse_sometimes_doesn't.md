---
title: "Switching USB keyboard and mouse sometimes doesn't work"
date: 2012-06-18
forum: Desktop Environments
---

### Post by areeda on 2012-06-18
[COLOR=#000000][FONT=Verdana]My situation is 4 computers running various operating systems: Ubuntu, Scientific Linux (a Fedora derivative), Debian Squeeze, MacOS X lion, and Windows 7. All except the Mac and one Ubuntu are multiple boot and used for cross platform development and testing.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I have a manual switch box with computers on ports 1-4 and a powered USB hub with mouse, keyboard, scanner, microphone and a USB headset adapter.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]There is also an HDMI and DVI switch box but they are not part of of the problem. Together they give me a more flexible KVM switch. I can watch a long running job on Monitor #2 connected to one system while working on another using Monitor #1.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]When I boot up everything works fine. I can also switch between systems freely. However if I leave one of the Linux systems disconnected for a long while it doesn't respond when I switch back to it. I have not seen this behavior with Windows or Mac. The Mac is sometimes disconnected for days but Windows usually gets booted back into Linux when I'm done with it.[/FONT][/COLOR]  It has been this way since Ubuntu 10.04 and continues with 12.04.

[COLOR=#000000][FONT=Verdana]Now I have tried 2 different USB switch boxes and when it doesn't respond it doesn't respond even if I plug the hub, or the mouse and keyboard directly into the usb ports on the system. I don't believe it has anything to do with the KVM the OP mentioned or my switch boxes.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Searching the web I found a comment that said apowered hub per system worked with his USB KVM switch.  I suspect we're seeing some sort of USB timeout. I suppose I can get a powered hub per system but I built these machines with 6 or 10 USB 2 and 2 or 4 USB 3 ports so I really don't need them. The powered hub may however convince Linux that there is something plugged into that port and keep it alive.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Does anyone know of a reason for this or even better a fix for it?[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Thanks[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Joe[/FONT][/COLOR]

---

### Post by brickedone on 2012-09-05
Sorry no answer here but very similar problem.  Two boxes (small low-power ubuntu server and win pc), one monitor, one powered usb kvm switch.  Used to work fine no problems switching back and forth.  

Recently re-built the ubuntu box with 12.04 LTS, now whenever I switch to the ubuntu box I get limited functionality.

Screen resolves just fine, and keyboard and mouse both seem to work for a very short time, but after a few seconds I get stuck in whatever application window I happen to be in.  If it's a term window, then I'm stuck in the term and anything launched from the term.  If I'm in a browser, then I'm stuck in THAT browser window and any tabs I load in that window.

Mouse and keyboard seem to have different 'stuck' features.  I.e. I can switch to a different application window with alt+tab, but only the keyboard can interact with the new window (mouse input not recognized).  Mouse input is only recognized in the 'stuck' application window.

This problem is VERY repeatable (happens every time I switch to ubuntu from away).  I can even repeat the problem by launching a new separate window (e.g. right clicking a browser tab and telling it to move to a new window, or launching a new window from a terminal).  I get a few seconds of full functionality across the entire desktop, then I get stuck in a window again.  As you can imagine, this causes me to play a rather amusing game of hot potato.

Also, it NEVER happens if I start up the ubuntu box with the switch pointed there from the beginning, and don't switch away.  It also fixes if I log out of gnome and log back in, although that kills any application windows I have running so it kind of sucks.

Any suggestions?

---

### Post by areeda on 2012-09-05
I've learned a few things since I posted.

#1 Linux USB support sucks.
#2 USB switches bounce but seem to work better than KVM switches

I say #1 because I have this problem fairly often with Ubuntu and Scientific Linux (RedHat derivative) but haven't seen it with Windows or Macs in the same setup.  Also my Windows machine is a multiple boot with Ubuntu and SL6.

I've had better luck with extension cables and pluggin my USB hub into the different machines bypassing the switch but while this works maybe 95% of the time I still see the problem occasionally.  When it happens I can correct it by unplugging the mouse or keyboard from the powered USB hub and reconnecting.  I'm not sure if it helps but I also add a few choice curses which I won't repeat here.

I suppose the thing to do is stop complaining and dig into the USB drivers but I just don't have the time.

My setup is acceptable as is.

Joe

---

