---
title: "Unity Desktop cycles through open applications"
date: 2011-09-30
forum: Desktop Environments
---

### Post by cov on 2011-09-30
Hi,

Quite often Unity will suddenly start to cycle through all the open applications.

If I have my Chrome Browser open, Gedit open, VirtualBox open, it will suddenly start to flash between all of these open applications in an uncontrolled way.

Does anyone else have this problem?

Is there a way to stop this behaviour or recover from it so that work is not lost?

I'm using Natty on a 32bit system with 4Gig on 2.6.38-11-generic-pae kernel.

---

### Post by Copper Bezel on 2011-09-30
First, do you have any idea what triggers it? Second, is it the same switcher you see when you press Alt+Tab, or another of Compiz's application switchers?

---

### Post by cov on 2011-10-01
It's similar, but different.

When pressing ALT-TAB a small window comes up with a thumbnail of the running applications. In contrast, with this the open applications cycle through with each displayed fullscreen for less than a second.

Also the Desktop background is quite prominent and is displayed as part of the cycle.

There doesn't seem to be any consistent trigger; it just suddenly goes into this mode and the only way I can recover is by restarting gdm.

I can also save the Virtualbox state by using "savestate" from a console, but this literally takes hours.

---

### Post by Copper Bezel on 2011-10-01
Weird. This definitely doesn't sound like any particular Compiz plugin gone awry, but I do think it's a Compiz problem. Rather than jumping back to GDM, what would happen if you jumped to a console and restarted Compiz? That is, hit Ctrl+Alt+F1 to get to a virtual terminal, logged in, then ran

```
export DISPLAY=:0
killall compiz
compiz --replace
```

I don't know if this will help narrow down the problem, but it's worth a shot.

---

### Post by cov on 2011-10-10
Okay,

It did it again without any apparent trigger.

Just to mention that It does seem to be something to do with Virtualbox as it's only when I'm working in Windows XP (I use a CAD programme which does not have any Linux equivalent) that the crash appears to happen.

I have copied your commands above to a script file and will execute it when next it happens.

---

### Post by Copper Bezel on 2011-10-10
Okay, cool. Let me know how it goes. With any luck, we won't have to find out, but if it happens again, we can at least isolate the problem. Thanks for mentioning that it only happens with the virtual machine running, as well.

---

