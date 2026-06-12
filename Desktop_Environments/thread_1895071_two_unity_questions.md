---
title: "two unity questions"
date: 2011-12-14
forum: Desktop Environments
---

### Post by linux.girl on 2011-12-14
Hello everyone,

I have two questions about unity:

1 - Is it possible to add a show desktop button? Or do I have to content myself with using ctrl+alt+d?

2 - Is there a way to avoid combining similar open windows under one icon in the launcher? I like the way it looks, but it is not very user friendly because I simply could not find a way to switch to the other open windows other than using alt+tab - and its starting to give me a headache to have to go through every window till I get to the correct one. For example, if I have 5 terminals open, I have to go with alt+tab one by one till I get to the one I want? Doesnt sound very logical to me :(

Any suggestions?

Million thanks as usual, to this great supportive community!

linux.girl

---

### Post by nilarimogard on 2011-12-14
1. There are two ways: a [Show Desktop icon for Unity Launcher]("http://www.webupd8.org/2011/04/show-desktop-icon-for-ubuntu-unity.html") or a [Show Desktop Indicator]("http://www.webupd8.org/2011/10/show-desktop-indicator-for-ubuntu-quick.html").
1. That's not possible for now. But try: Super + W

---

### Post by linux.girl on 2011-12-14
Thanks! What is the Super key? I dont see it in my keyboard?

And the W is capital?

---

### Post by stinkeye on 2011-12-14
Super is the windows key.

To use the Super+w shortcut, the scale plugin needs to be enabled in ccsm.
Super+w shortcut brings up a picker for all windows.

Also if you have grouped windows on the launcher,
the first click on the icon will bring the group into focus and a
secondary click will bring up the scale window picker for that group.

---

### Post by linux.girl on 2011-12-15
Thanks a lot for the explanation! I imagine I can install the scale plugin from the software center?

I just dont know what ccsm is?

---

### Post by stinkeye on 2011-12-15
> **linux.girl said:**
> Thanks a lot for the explanation! I imagine I can install the scale plugin from the software center?

I just dont know what ccsm is?
The scale plugin is included in the default compiz install.
CCSM is **compizconfig-settings-manager** used for changing settings
when using Unity 3d (the "ubuntu" session) which uses compiz as the window manager.
Doesn't work with unity 2d (the "ubuntu 2d" session) as metacity is the window manager.

to install...
```
sudo apt-get install compizconfig-settings-manager
```

To run, type **ccsm** in the dash.

---

### Post by linux.girl on 2011-12-16
Hi stinkeye,

I did everything you said, just wanted to make sure it is working as it should:

When I punch super + w, it divides the screen in four and in the upper left space it shows all the windows i have open.

Is this how its supposed to work?

Thanks,

linux.girl

---

### Post by jimmydean886-2 on 2011-12-16
Be careful if you decide to eventually fool with CompizConfig. It can be somewhat tricky and if you click the wrong thing, you may loose Unity. If a dialog pops up after you click something that asks to resolve conflicts or override an existing setting, BE WARY. 

Other than that, it's a great utility. If you have a new computer, (less than 2-3 years old) then I suggest trying "wobbly windows"

I don't know one person who hasn't gotten a kick out of that!

---

### Post by linux.girl on 2011-12-16
Thanks for the tips - I am actually not looking fool around with this add-on - although it this look great and seems cool to play around with, I really only need to find a way to comfortably move through open windows, especially the ones that are grouped on unity launcher. 

The way I described before is the way that is supposed to work? i.e., that if I press super + w then I get to the screen split in 4 and in the upper left space I see all open and grouped windows? it is better than alt+ tab, but still not ideal.

I hope they fix this issue of grouped stuff on precise pangolin...

Thanks!

linux.girl

PS: now you got me scared hehehe, if I do press a wrong button and lose unity...any way i can get it back?? or it is no go back mistake??

---

### Post by MG&amp;TL on 2011-12-16
> **linux.girl said:**
> Thanks for the tips - I am actually not looking fool around with this add-on - although it this look great and seems cool to play around with, I really only need to find a way to comfortably move through open windows, especially the ones that are grouped on unity launcher. 

The way I described before is the way that is supposed to work? i.e., that if I press super + w then I get to the screen split in 4 and in the upper left space I see all open and grouped windows? it is better than alt+ tab, but still not ideal.

I hope they fix this issue of grouped stuff on precise pangolin...

Thanks!

linux.girl

PS: now you got me scared hehehe, if I do press a wrong button and lose unity...any way i can get it back?? or it is no go back mistake??

It's easy enough to recover , just not a process that's....desirable, shall we say. :D

If you have five terminals open, in Oneiric anyway, there is only one terminal icon shown in the Alt-Tab switcher, if you press the down arrow, it shows all of the terminals.

If you want a more traditional switcher, and a hardware-accelerated computer (if it's running Unity, then it is), open CCSM again, down at the bottom(under "window management" or something) there are several "switcher options"-enable one of those, then use Super-TAB, to switch. I like ring switcher, but you might like shift switcher. Or one of the many other ones...

Good to see someone liking Unity for once. :)

---

### Post by stinkeye on 2011-12-16
> **linux.girl said:**
> 
The way I described before is the way that is supposed to work? i.e., that if I press super + w then I get to the screen split in 4 and in the upper left space I see all open and grouped windows? it is better than alt+ tab, but still not ideal.


What your describing sounds like unity 2d.Doesn't use compiz so changing settings in ccsm has no affect.
It works a bit differently in 2d.
You should still have the secondary click for grouped windows though.
In the terminal...
```
echo $DESKTOP_SESSION
```

For me with default keybindings... 
Super+s shows the desktops using the expo plugin...pic1
Super+w shows open windows using the scale plugin...pic2

---

### Post by flyingfisch on 2011-12-16
Is there a way to get the super+w shortcut to work in Unity 2D?

> **MG&TL said:**
> 
...
Good to see someone liking Unity for once. :smile:
I love Unity.

---

### Post by linux.girl on 2011-12-17
> **MG&TL said:**
> It's easy enough to recover , just not a process that's....desirable, shall we say. :D

If you have five terminals open, in Oneiric anyway, there is only one terminal icon shown in the Alt-Tab switcher, if you press the down arrow, it shows all of the terminals.

If you want a more traditional switcher, and a hardware-accelerated computer (if it's running Unity, then it is), open CCSM again, down at the bottom(under "window management" or something) there are several "switcher options"-enable one of those, then use Super-TAB, to switch. I like ring switcher, but you might like shift switcher. Or one of the many other ones...

Good to see someone liking Unity for once. :)

> **stinkeye said:**
> What your describing sounds like unity 2d.Doesn't use compiz so changing settings in ccsm has no affect.
It works a bit differently in 2d.
You should still have the secondary click for grouped windows though.
In the terminal...
```
echo $DESKTOP_SESSION
```For me with default keybindings... 
Super+s shows the desktops using the expo plugin...pic1
Super+w shows open windows using the scale plugin...pic2

Hi and thanks again for the detailed answers - and yes, I indeed do love unity. I think they should change that issue of switching between open/grouped windows on Precise Pangolin, but other than that, it is neat :-)

So from what you are saying, you think I am actually running unity 2d? How can I know if i have 2d or 3d? And what is the difference between them? If indeed I have 2d, then I should follow what you said on the second post (second quote)? 

A million thanks for taking the time to explain all that stuff to me!

linux.girl

---

### Post by MG&amp;TL on 2011-12-17
> **linux.girl said:**
> Hi and thanks again for the detailed answers - and yes, I indeed do love unity. I think they should change that issue of switching between open/grouped windows on Precise Pangolin, but other than that, it is neat :-)

So from what you are saying, you think I am actually running unity 2d? How can I know if i have 2d or 3d? And what is the difference between them? If indeed I have 2d, then I should follow what you said on the second post (second quote)? 

A million thanks for taking the time to explain all that stuff to me!

linux.girl

No problem, it's nice to have someone grateful. :)


Press Ctrl-Alt-T, and a purple box should appear, looking something like this:

```
linuxgirl@linuxgirlcomputer:~$_
```


Then very carefully type:

```
echo $DESKTOP_SESSION
```

into the box, and press the return key. If it returns a blank, you've typed it wrong! :)

if it says:

```
ubuntu
```

then congratulations, you're running Unity3d. :D

otherwise, it'll say:

```
ubuntu-2d
```

which is self-explanatory.

If you are running 3d, go ahead and try all of the stuff others are saying.

If not, it's not a bad thing (for example, if your hardware won't run Unity), but most of the shortcuts here won't work. If you think you can run Unity, (roughly 1GB RAM, a reasonable CPU, and a graphics chipset of some variety, you can see these in "system info" in the Unity menu), you probably need to enable a driver or something-post back if this is the case.

Good luck!

---

### Post by linux.girl on 2011-12-17
Thanks again :-)

I have two computers - one is a VM, one is a Desktop. The Desktop is 3D (I did the echo test) and the VM is 2D :-)

I will try all the shortcuts mentioned on the desktop and see how it works.

Regarding the 2D for the VM - will any shortcut work? Or none at all? 

And BTW, i noticed an interesting thing in the VM (dont know if I'll be able to explain, but will try :D): When I am on a regular PC and I click on the desktop, then I can see on the top of the screen the menu bar (just like when you click on firefox, or thunderbird, or anywhere in the file system - you get the black menu bar above with all the options). When I am on a VM, then I dont get the menu bar when I click on the desktop. I get it for all other windows, but not for the desktop. Did anyone notice that?

Will keep you update on how the shortcut exploration goes :D :D

thanks again,

linux.girl

---

