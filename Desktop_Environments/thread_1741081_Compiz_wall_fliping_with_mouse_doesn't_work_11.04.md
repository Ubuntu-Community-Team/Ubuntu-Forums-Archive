---
title: "Compiz wall fliping with mouse doesn't work 11.04"
date: 2011-04-27
forum: Desktop Environments
---

### Post by Dreadnaxt on 2011-04-27
Hi!
Just upgraded to 11.04, switched to classic view and reconfigured compiz (the settings dropped to default while upgrade). But the flipping between desktop walls with mouse (some_edge+mouse button) doesn't work now. Switching with keyboard or edge flipping with mouse pointer works perfect.
Has anyone same problem? How it can be fixed?

---

### Post by Krytarik on 2011-04-27
Did you already set up the bindings in "System -> Preferences -> CompizConfig Settings Manager -> Desktop Wall -> Bindings -> Move within wall"? Since they are not set up by default.

Greetings.

---

### Post by Dreadnaxt on 2011-04-28
> **Krytarik said:**
> Did you already set up the bindings in "System -> Preferences -> CompizConfig Settings Manager -> Desktop Wall -> Bindings -> Move within wall"? Since they are not set up by default.

Greetings.

Hi!

Yes, that is what I've mentioned as *reconfigure*. I've set the bindings, and even tried different combinations. None works.

---

### Post by Krytarik on 2011-04-28
I have set up custom commands (wmctrl) and bindings until reading your OP, I didn't even know before that those options are available out of the box. So, that may help. How are your workspaces set up?

---

### Post by Dreadnaxt on 2011-04-28
> **Krytarik said:**
> I have set up custom commands (wmctrl) and bindings until reading your OP
Could you please describe more detailed about this?

> **Krytarik said:**
> How are your workspaces set up?
Square 2x2.

By the way, just tested the mouse bindings with rotation cube, edge+mouse button to rotate left or right doesn't work. But cube initialization with ctr+alt+mouse_button1 combination works perfect.

---

### Post by Dreadnaxt on 2011-04-28
I've just played a bit more with rotation cube and somehow edge+mousebutton worked once. I think that there is some problem with edge detection or smth. like this.

---

### Post by Krytarik on 2011-04-28
> **Dreadnaxt said:**
> 
Square 2x2.

Ok, I have set them up the same. Then those commands may provide a sufficient temporary workaround, I really used them for a while without much difficulties.

I have a screen resolution of 1152x864.

Of course, you need the package "wmctrl" therefore, it's in the official repos.
```
[commands]
as_command3 = wmctrl -o 0,0
as_command4 = wmctrl -o 1152,0
as_command5 = wmctrl -o 0,864
as_command6 = wmctrl -o 1152,864
as_run_command3_button = <LeftEdge><TopEdge>Button1
as_run_command4_button = <RightEdge>Button1
as_run_command5_button = <BottomEdge><BottomLeftEdge>Button1
as_run_command6_button = <BottomRightEdge>Button1
```

---

### Post by Dreadnaxt on 2011-04-28
> **Krytarik said:**
> Ok, I have set them up the same. Then those commands may provide a sufficient temporary workaround, I really used them for a while without much difficulties.

I have a screen resolution of 1152x864.

Of course, you need the package "wmctrl" therefore, it's in the official repos.
```
[commands]
as_command3 = wmctrl -o 0,0
as_command4 = wmctrl -o 1152,0
as_command5 = wmctrl -o 0,864
as_command6 = wmctrl -o 1152,864
as_run_command3_button = <LeftEdge><TopEdge>Button1
as_run_command4_button = <RightEdge>Button1
as_run_command5_button = <BottomEdge><BottomLeftEdge>Button1
as_run_command6_button = <BottomRightEdge>Button1
```

Thanx for the explanation.
I've just tried this trick, but it won't help unfortunately. The problem seems to be in the edge detection.
Setting the command for example ctrl+mousebutton2 works perfect, but <LeftEdge>+mousebutton2 does nothing.

---

### Post by Krytarik on 2011-04-28
> **Dreadnaxt said:**
> 
I've just tried this trick, but it won't help unfortunately. The problem seems to be in the edge detection.
Setting the command for example ctrl+mousebutton2 works perfect, but <LeftEdge>+mousebutton2 does nothing.
Ok, then it's indeed about the edge detection in general, like you indicated earlier. I just yet checked the bug reports, nothing about those particularly. Does it work if you log in to "Ubuntu Classic"?

---

### Post by Dreadnaxt on 2011-04-28
> **Krytarik said:**
> Does it work if you log in to "Ubuntu Classic"?
Unfortunately no. All my test are done in Ubuntu Classic mode. Unity is a bit uncomfortable for me for the first time :)

---

### Post by Krytarik on 2011-04-28
> **Dreadnaxt said:**
> Unfortunately no. All my test are done in Ubuntu Classic mode. Unity is a bit uncomfortable for me for the first time
Ah, you already said that in the OP. Sorry, I'm bit distracted by today's release. The torrents are running pretty well now. Even the official announce through the mailing list is out now. I don't know what to do about your issue right now, sorry. Is your system fully updated?

---

### Post by Dreadnaxt on 2011-04-28
> **Krytarik said:**
> Ah, you already said that in the OP. Sorry, I'm bit distracted by today's release. The torrents are running pretty well now. Even the official announce through the mailing list is out now. I don't know what to do about your issue right now, sorry. Is your system fully updated?

Just tried *update-manager* and *update-manager -d*, both says system is up to date.

vi /etc/lsb-release
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

```

Btw, edge problem is the same in the Unity mode.

---

### Post by Krytarik on 2011-04-28
> **Dreadnaxt said:**
> Just tried *update-manager* and *update-manager -d*, both says system is up to date.

Either including using the "Reload" button, I assume!?

Just to be sure, the 'old' way:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by Dreadnaxt on 2011-04-28
> **Krytarik said:**
> Either including using the "Reload" button, I assume!?

Yes :)

> **Krytarik said:**
> 
Just to be sure, the 'old' way:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
```

Reading package lists... Done
~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
So, the system is truly up to date.

---

### Post by Dreadnaxt on 2011-04-28
The bug seems to be reported
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/754948](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/754948)

---

### Post by Krytarik on 2011-04-28
> **Dreadnaxt said:**
> The bug seems to be reported
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/754948](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/754948)
Seems true, I overlooked that one, again. ;-)

---

### Post by Dreadnaxt on 2011-04-28
> **Krytarik said:**
> Seems true, I overlooked that one, again. ;-)

Thanx for the help anyway!

---

### Post by oldarney on 2011-04-29
This is truelly anoying... I like the Unity interface, but its just too buggy. Edge detection is globally broken, except when the edge is being used alone, without combinations of input. Of example, DnD desktop wall detects the edge.

-- Begin rant --

For some reason the shadow of the top menu bar on unity is on top of the menu bar itself. Making the bar pure black, the buttons still work though.

Ubuntu keeps killing my custom keyboard layout every other update. I wish there was a program like ukele on mac, or msklc on windows for ubuntu.

-- End rant --

---

### Post by siretfel on 2011-05-01
I'll try Unity for today.It caused me more problems than any other Ubuntu version I've ever used,even when I first started using ubuntu back in 2006!
Have exactly the same problems as you guys above

---

### Post by oldarney on 2011-05-01
I'm actually liking unity. I replaced the edge flip on click with an expose corner.I really like the super dock, I'ts notification handling, multi window handling and visibility handling are far superior to anything else out there.

---

### Post by miesogeno on 2011-05-05
Well, I have the same problem with the edge flipping with mouse pointer (ubuntu classic).

sometimes it works, sometimes it doesn't. I thought of some conflict in compiz configuration, but I've looked it trhough and can't find anything. it's getting to be a little annoying.

---

### Post by Hreinsi on 2011-05-05
I  use only button 2 push the scrollweel move mouse Works graet

---

