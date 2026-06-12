---
title: "how to configure resize window with alt drag"
date: 2009-06-11
forum: Desktop Environments
---

### Post by vayira on 2009-06-11
Hi I'm getting used to gnome after a few years of KDE. 

I'd like to configure the alt-middlebutton-drag method of resizing windows so that I can do it with alt-rightbutton-drag. (I use a two button ergonomic mouse that doesn't have a middle-button) 

Where can I configure this in gnome? 

I read somewhere that you can do it in CCSM, so I installed it, but the option is not available there. 

I'm using Jaunty 

Thanks for any help.

---

### Post by zadehas on 2009-06-11
Start CompizConfig Settings Manager

Go to "Window Management"
Click "Resize Window"
Go to "Initiate Window Resize" with a mouse symbol and choose <Alt> Button3
I'm not sure about the button though, you can try until you get it right

---

### Post by vayira on 2009-06-11
Thanks for that. The only thing is it doesn't work! I get this message...

[I][INDENT]The new value for the button binding for the action Initiate Window Resize in plugin Resize Window conflicts with the action Window Menu of the General Options plugin.
Do you wish to disable Window Menu in the General Options plugin?[/INDENT][/I]

If I try any of the the 3 options that follow, apparently compiz accepts it, but nothing changes & when I go back to CompizConfig Settings Manager everything has gone back to the defaults.

Also, if I try changing the key from alt to ctrl, it modifies the settings for moving the window instead of resizing so there is something very buggy there. All those special effects, but something so basic doesn't work! I have now tried editing all of the settings related to moving, resizing & draging the windows - all I get is defaults or disabled despite the options which are supposedly there.

---

### Post by zadehas on 2009-06-12
Well, to be honest, I use the Super (Windows Logo) key for this action, it seems somewhat more handy.

Here's a screenshot of my Resize Window section:

---

### Post by vayira on 2009-06-12
> **zadehas said:**
> Well, to be honest, I use the Super (Windows Logo) key for this action, it seems somewhat more handy.

I don't mind which key it is, but I'd like to be able to use the right hand mouse button (3) as my ergonomic mouse doesn't have a middle button. Gnome/compiz just keeps putting everything back to the the default mouse buttons. I can change the key no prob. This looks like a bug to me. 

The menu that pops up with the right button by default is no use to me. I've never used it, whereas I resize all the time.

---

### Post by zadehas on 2009-06-13
I see now what you mean.
I don't have a solution for using button3, but for me this setting:

<Alt>Button2

will work by pressing Alt and both mouse buttons, which I think is just as good.

---

### Post by vayira on 2009-06-13
> **zadehas said:**
> 
<Alt>Button2
will work by pressing Alt and both mouse buttons, which I think is just as good.

It is not possible to push both buttons at the same time on my ergonomic mouse because it is a single rocker switch which works as left or right click. It is very comfortable to use as I have the beginings of repetitive strain & normal mice make my wrist very painful. 

I'm going to take another look at KDE to see if 4 is usable yet. Gnome seems to be very limited in terms of configuration.

---

### Post by AbtZ on 2009-07-06
Back when I was still running Arch Linux on this computer changing from alt+middle click to alt+left click throuch ccsm was not a problem, so it seems like it is Ubuntu specific.

Have you filed a bug report?

---

### Post by z0th on 2009-07-16
hi guys...

any follow up to this?

im using fluxbox -- and after a fresh reinstall of 9.04, the LClick+alt to resize and RClick+ctrl to move windows is gone. 

i was always under the impression that this was a function of xorg itself, and not the wm. (the function is also in several other wm's)

---

### Post by z0th on 2009-07-30
thought i would just post the solution i found to my problem. its in the keys file. i guess at some point, they decided to make the dragging and wheel actions customizable as well. 

from ~/.fluxbox/keys

```
# alt + left/right click to move/resize a window
OnWindow Mod1 Mouse1 :MacroCmd {Raise} {Focus} {StartMoving}
OnWindow Mod1 Mouse3 :MacroCmd {Raise} {Focus} {StartResizing NearestCorner}

# scroll on the desktop to change workspaces
OnDesktop Mouse5 :PrevWorkspace
OnDesktop Mouse4 :NextWorkspace

# scroll on the toolbar to change workspaces
OnToolbar Mouse5 :PrevWorkspace
OnToolbar Mouse4 :NextWorkspace
```

---

### Post by Mincus on 2009-10-30
Bit of a necro, but I thought it worth adding my experiences in this area.

Having right/middle click switched on GNOME is something that's pushed me to XFCE with Xubuntu for a long time, I want resize on my right button, personal preference, so haing stuck with plain Ubuntu with a 9.10 install, went wandering through the config to set this up.

There is an option in metacity's gconf for "resize_with_right_button", I couldn't get this to work. This turns out that I'm using Compiz and this option doesn't transfer across (unsure whether this is a compiz or GNOME issue). Presumably this will work if you've all effects off though.

Next is ccsm. The instructions from zadehas in post 2 will work, but first you have to untick "Enable integration into the desktop environment" located in "Preferences".
Otherwise you get the behaviour described by vayira where ccsm immediately sets the option back to the GNOME default.

Hope that helps anyone else who comes across this thread with similar problems. :)

---

### Post by AbtZ on 2009-11-11
Thanks, Mincus,that works.

Since gconf-editor now has the option of switching it seems to solely be a Compiz problem.

---

### Post by yoasif on 2009-12-31
AbtZ, did you ever file this as a bug? I am seeing this issue in Lucid, and would appreciate it if you filed the bug - I will be happy to confirm it.

---

### Post by AbtZ on 2010-01-01
Yes I did. Here's the link:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/495135](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/495135)

I actually think it should be easy to fix the issue, but there are no replies as of yet.

---

### Post by hariks0 on 2010-01-02
Try getting a new 3 or 5 button mouse.

---

### Post by AbtZ on 2010-01-02
How has this got anything to do with the mouse I'm using?

With the two mice I have and, more importantly, the trackpads of my two laptops it doesn't work properly.

---

### Post by ghoulsblade on 2010-07-23
necro again since it's still broken by default in a fresh ubuntu 10.04 install : 

alt+rightclick window-resize (important since this is kde default behaviour, so needed for kde->gnome switchers) :

ccsm/compiz config options don't show any effect and are reset the next time ccsm is started ? go to Preferences, and if gconf is selected as a back-end, then make sure that the checkbox "Enable integration into the desktop environment" is UNCHECKED.
(found in [https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/146736](https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/146736) )

the option itself : install ccsm/compizconfig : in general:general options disable the window menu under key bindings. in window management: scale/resize window: change the key from alt+middle mouse to alt+right mouse.
in

---

### Post by lukanova on 2011-03-30
oh ubuntuforums, thank you for this wisdom. it's been about two or three years of frustration. i'm not coming from KDE, but more from fluxbox or legacy X11 environment if you wish and have been very frustrated being forced to use alt+button2 for window-resize, because in compiz or gnome it was not possible to disable alt+button3 for Window Menu and setup alt+button3 for window resize.

going to CompizConfig Settings Manager > Preferences and unticking "Enable integration into the desktop environment", suddenly made my life brighter.

Thanks. Looks like this was fixed in Maverick.

---

### Post by Jetro on 2012-11-03
> **lukanova said:**
> 
going to CompizConfig Settings Manager > Preferences and unticking "Enable integration into the desktop environment", suddenly made my life brighter.

Thanks. Looks like this was fixed in Maverick.
Long overdue, but thanks! This suddenly appeared in Ubuntu 12.10, and this fixed it immediately.

---

