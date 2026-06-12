---
title: "start xfce from console and mouse doesn't work"
date: 2008-07-09
forum: Desktop Environments
---

### Post by leopardsanderson on 2008-07-09
Hi, first a couple of words and then the problem,
I was tweaking my Ubuntu installation in order to get with GRUB two options: one with fast startup, few modules, thin graphic interface and a normal one, with all the modules loaded and the best graphics.
To do this: runlevel 3-5 are all the same, I tweaked one (RL4) to startup with the least modules possible, and I tweaked GRUB to add an option starting with a specific runlevel (RL4). When RL4 starts it starts only console, without graphics. This is useful to me as I can do some jobs without having to wait too much for a complete system startup.
NOW THE PROBLEM:
Once prompted for textual login if I want to turn to a desktop I enter
```
startxfce4
```
to run the quick xfce desktop manager.
It works, but:
1- I get an error message "HAL couldn't start" or similar
2- the mouse doesn't work! The keyboard works (USB one), the mouse is USB too, but also the touchpad is not working (is a laptop).
On first try I reset all the modules on so that RL4 boots up with the same modules as RL2 (default one), because I thought that HAL is one of them and there could be a problem with the modules (but I never turned it off anyway). This didn't change anything, so I'm wondering how the whole desktop manager architecture works: it is necessary to do any other command before starting a session? Who should control the mouse and peripherals?
If necessary I'll try to be clearer, thanks in advance.

---

### Post by mali2297 on 2008-07-09
Have you tried starting hal before xfce?
```

sudo /etc/init.d/hal start

```

---

### Post by leopardsanderson on 2008-07-10
I've tried to, but says "ensure that dbus is turned on". I tried to 
```
dbus-launch
```
and also
```
dbus-daemon
```
but I don't what did I do with these.
Anyway restarting hal did say the same thing.
I also tried to "stop" and "restart" which did work, but then starting xfce nothing changed.
Do I miss some theory about starting a session manager?
I'll try to mess more and see what happens, but everything looks so ununderstandable... I should be a canonical programmer to know what's going on there... :(
Thanks anyway!
Hope somebody raise up with other solutions!

---

### Post by mali2297 on 2008-07-10
> **leopardsanderson said:**
> I've tried to, but says "ensure that dbus is turned on". I tried to 
```
dbus-launch
```
and also
```
dbus-daemon
```
but I don't what did I do with these.


Try
```
sudo /etc/init.d/dbus start
```

---

