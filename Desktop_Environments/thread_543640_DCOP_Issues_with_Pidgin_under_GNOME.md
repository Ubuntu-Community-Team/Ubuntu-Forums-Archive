---
title: "DCOP Issues with Pidgin under GNOME"
date: 2007-09-05
forum: Desktop Environments
---

### Post by rmx.dave on 2007-09-05
Hello, 

I have a strange error when running Pidgin recently. When Pidgin starts up, it stops responding right away and then I have to kill it. I ran Pidgin from the terminal, and I get this error message just before the program stops responding:

DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: Couldn't attach to DCOP server!

On top of that, my mouse and keyboard stop working sometimes too. 

I know that DCOP is a KDE thing, but I am running GNOME. I recently installed BasKet Notes and Amarok. Once this issue started happening, I uninstalled Amarok and Pidgin seemed to work fine for a day. Now it's back again, and I need BasKet for my classes at the university (Unless somehow it has a GNOME equivalent). But I've had KDE/Qt apps installed on my machine for quite some time, so I don't know how this is happening. 

Also, when I try running "dcop" from the shell, I get the same error messages. 

Can anyone help me to get my computer to stop reacting this way, and let me keep Basket and Pidgin installed?

Thanks,
rmx.dave

---

### Post by rmx.dave on 2007-09-05
Well I recompiled Pidgin and its still kicking the same thing. Any ideas?

---

### Post by rmx.dave on 2007-09-10
Does anyone have any advice on this? I completely removed BasKet and Amarok (even though I really liked it) because now my USB ports keep disabling in the middle of my computing session. I know this is related because whenever I'd get the DCOP Pidgin crash my USB mouse would die. I have a lot of work to do and I really would like to get this problem fixed. Anyone?

---

### Post by rmx.dave on 2007-09-10
In my frustration I just uninstalled every package that included the phrase 'kde' (actually I checked to make sure it wasn't anything I really needed) and now I am going to try it out. If my USB dies again I will be back...

---

### Post by cdean on 2008-04-28
This has crept up on me all of a sudden on Hardy amd64. The buddy list loads and connects to services, but then starts spitting out messages to the terminal.

```
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: Couldn't attach to DCOP server!
```

I have yet to find the source of the problem.

---

### Post by cdean on 2008-04-28
It's apparently related to the musictracker plugin, but the solution provided in thread [http://ubuntuforums.org/showthread.php?t=590356](http://ubuntuforums.org/showthread.php?t=590356) does not work easily (start audio player, then pidgin, disable plugin).

I had to start pidgin at the command line with ```
pidgin -n
``` and quickly disable the plugin.

Here's the related bug: [https://bugs.launchpad.net/ubuntu/+source/musictracker/+bug/199438](https://bugs.launchpad.net/ubuntu/+source/musictracker/+bug/199438)

---

