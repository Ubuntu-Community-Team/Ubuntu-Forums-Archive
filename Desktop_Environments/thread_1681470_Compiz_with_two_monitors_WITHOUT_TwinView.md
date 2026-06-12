---
title: "Compiz with two monitors WITHOUT TwinView"
date: 2011-02-04
forum: Desktop Environments
---

### Post by UBod on 2011-02-04
Hi,

I am sorry if this has been discussed already. I tried my best to find a solution myself (and I checked all kinds of forums too). Maybe I should add that I am not an expert in configuring Linux stuff. Here is my question:

I recently installed Ubuntu 10.10 (32bit) on an HP compaq nc6400 laptop (internal display is 1280x800, graphics card is an Intel Mobile 945GM/GMS, 943/940GML Express) which I am using in three situations:

[LIST=1]
[*]In my office: external monitor (1280x1024), laptop in docking station with lid closed
[*]At home/on travel: as it is, without any external monitor
[*]When giving lectures: with projector (1024x786), lid open, same output on projector and internal display
[/LIST]
As you see, I either want one output device only or both showing the same output. Additionally, I want to run compiz. My problem is that, whenever I (1) connect an external display or (2) when I press the Fn+F4 key to change displays or (3) sometimes even when I open/close the laptop's lid, the system at some point switches to TwinView which seems not to work with compiz on my system. The effect is that compiz is deactivated. When I want to have it back, I have to open the appearance settings and change to extra visual effects again. Unfortunately, that reverts compiz to default settings and I have to adjust my compiz settings again. Please note that compiz works properly in all three situations I listed above. The problem is "only" that, at some point, it switches to TwinView.

So my question comes down to: Is there a way to tell X or compiz NEVER TO CHANGE TO TWINVIEW? I guess that would solve my problem.

Sorry for my lenghty message. Any help is gratefully appreciated!

Thanks in advance,
UBod

---

### Post by Copper Bezel on 2011-02-04
Whoa, opening CCSM while Compiz isn't running is the problem that's mucking up your settings. Stop doing that. Make a shortcut for compiz --replace on your panel, or, better, get the DisPlex appindicator for switching between Metacity and Compiz.

---

### Post by The Linux Cynic on 2011-02-04
This is besides the point.

In your first case, with the docking station and the lid closed, does your docking station have some sort of cooling fan? Laptops often run rather hot with the lid closed. You might to watch out for that, you may be reducing your machine's life.

---

### Post by UBod on 2011-02-04
Thanks a lot,[COLOR=#000000][FONT=Verdana,Arial,Tahoma] [/FONT][/COLOR]Copper Bezel, that was already a very useful tip! Though it is a workaround, it reduces my effort for restoring my desired configuration to one mouse click only - which is more than acceptable for me.

Anyway, I am curious whether there is a solution that avoids this issue completely. Let's see.

Greetings, UBod

---

### Post by UBod on 2011-02-04
> **The Linux Cynic said:**
> This is besides the point.

In your first case, with the docking station and the lid closed, does your docking station have some sort of cooling fan? Laptops often run rather hot with the lid closed. You might to watch out for that, you may be reducing your machine's life.

I never had any problems like that. The laptop fan's air outlet is on the left side of the shell and, as it seems to me, it makes absolutely no difference whether the lid is open or closed.

Greetings, UBod

---

