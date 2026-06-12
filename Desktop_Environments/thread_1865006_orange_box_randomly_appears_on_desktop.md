---
title: "orange box randomly appears on desktop"
date: 2011-10-19
forum: Desktop Environments
---

### Post by fusa on 2011-10-19
Recently an orange box, that covers either 1/2 of the left or right of my desktop appears.  I do not know what triggers this, other than moving the mouse across my desktop.  The only way to get rid of it is to restore a minimized program.  The program then restores to fill the area the orange box is in.  Even if the windows was a different size than the box before minimizing it. 
A screen shot of this is at: [img]http://img703.imageshack.us/img703/1034/screenshotat20111019151.png[/img]

---

### Post by Frogs Hair on 2011-10-19
I see this a result of pushing a active window to close to the panel . When the active window begins to overlap with the panel the box appears.

The location of the system monitor on is most likely the cause . If the that is the info panel screenlet you may be able to change the position it opens in the settings.

If it is conky the position can be changed in the .conkyrc .

---

### Post by Larkspur on 2011-10-19
I don't think it's the conky.  I'm getting this at random when I move to the edges, but I can't work out what's causing it, because I'm not dragging windows and I don't have any screenlets.  Fusa, can you tell me if you've used CompizConfig and if so, what settings you've changed?

---

### Post by Frogs Hair on 2011-10-19
I can create this effect by pushing any active window into the panel or desktop wall . If you push far enough the the application window will resize to maximum .

---

### Post by dasumner on 2011-10-19
I thought it was just me.  Out of the clear, blue sky mine started doing the exact same thing today.  The only thing that makes it go away is to switch to a different workspace.  Needless to say, it's quite annoying.  Curiously, I've noticed that it only seems to popup when the mouse gets close to the workspace switcher icon or the Dash home icon.  I guess it's worth noting that I recently went from 11.04 to 11.10.

---

### Post by Larkspur on 2011-10-19
> **Frogs Hair said:**
> I can create this effect by pushing any active window into the panel or desktop wall . If you push far enough the the application window will resize to maximum .


I understand that, but I seem to be getting this without dragging a window.

@dasumner: I've got a fresh install, so maybe you upgrading is not the cause.  Interesting you say it started happening today; I'm sure there was a compiz update yesterday.  If so, perhaps that is what is causing this.

---

### Post by dasumner on 2011-10-19
> **Larkspur said:**
> I understand that, but I seem to be getting this without dragging a window.

@dasumner: I've got a fresh install, so maybe you upgrading is not the cause.  Interesting you say it started happening today; I'm sure there was a compiz update yesterday.  If so, perhaps that is what is causing this.

Same here.  It's not dragging the window that does it.  It's simply getting the pointer near the panel/taskbar that does it.

---

### Post by Frogs Hair on 2011-10-19
I don't know what may be causing random occurrences of this behavior , but I think the OP 's problem is caused by the position of the screenlet. I used that screenlet at one time and if I remember correctly there is a position adjustment.

---

### Post by Larkspur on 2011-10-19
> **Frogs Hair said:**
> I don't know what may be causing random occurrences of this behavior , but I think the OP 's problem is caused by the position of the screenlet. I used that screenlet at one time and if I remember correctly there is a position adjustment.

Yeah, it could be, since it is, as you say, right at the edge and compiz treats screenlets as windows.

Dasumner, I think [this]("https://bugs.launchpad.net/compiz-core/+bug/875557") is our bug.  I followed the steps to reproduce, and I get the orange box every time.

---

### Post by fusa on 2011-10-19
> **Larkspur said:**
> I don't think it's the conky.  I'm getting this at random when I move to the edges, but I can't work out what's causing it, because I'm not dragging windows and I don't have any screenlets.  Fusa, can you tell me if you've used CompizConfig and if so, what settings you've changed?

No, I don't use Compiz.  I recently built a new computer and installed 11.04, then upgraded to 11.10, never installing Compiz.  Like others have said this just started recently, I think yesterday.


I just tried closing the screenlet, and all other screenlets, and closing screenlet manager.  The orange box still appears, without moving windows across the desktop.

---

### Post by dasumner on 2011-10-19
> **Larkspur said:**
> Yeah, it could be, since it is, as you say, right at the edge and compiz treats screenlets as windows.

Dasumner, I think [this]("https://bugs.launchpad.net/compiz-core/+bug/875557") is our bug.  I followed the steps to reproduce, and I get the orange box every time.

Same here.

---

### Post by chuckyanutsup on 2011-10-20
yep, I'm having the same problem.

---

### Post by mc4man on 2011-10-20
The 'orange box' is associated with the grid plugin in compiz, typically only when moving a window & the cursor(grab) hits an edge

Can be disabled in ccsm (compizconfig-settings-manager) or from a command

---

### Post by sieve on 2011-10-20
The orange box appears when trying to select multiple items off the desktop.  Is it possible that your mouse is overly sensitive?

---

### Post by Jimlas53 on 2011-10-20
Seeing the same thing - on 3 different machines, one upgraded, 2 fresh installs.  I don't recall seeing this before using the workspace switcher.

Doug

---

### Post by Kereltis on 2011-11-01
I'm getting the same problem on 3 different machines. Fresh installs with latest updates and no settings changed.

---

### Post by chris.olive on 2011-11-01
Yes this problem started intermittently some weeks ago but not every day, like others I had to switch desktops, and as I often work with three or four open, very annoying!
Tried putting Compiz on which got rid of everything including the side bar [why can't we place this where we wish?].
I then could not open any program until I found that by trying to open any file in "file system" and selecting 'other program' and choosing 'Ubuntu software center' remove 'compiz' then restart it all came up as before.

---

### Post by dsr007rana on 2011-12-02
> **mc4man said:**
> The 'orange box' is associated with the grid plugin in compiz, typically only when moving a window & the cursor(grab) hits an edge

Can be disabled in ccsm (compizconfig-settings-manager) or from a command

Can you please eloborate this step. How to follow these steps in Ubuntu 11.10?

---

### Post by typhoon_tip on 2011-12-02
> **dsr007rana said:**
> Can you please eloborate this step. How to follow these steps in Ubuntu 11.10?

Do these commands:
```
sudo apt-get install compizconfig-settings-manager
ccsm
```

Then look for the Grid plugin, and un-tick it (disables it), problem will go away.

---

### Post by r_mano on 2011-12-02
Another workaround is to open ccsm and then change the drag and drop option in the "Expo" module to something different fron Button1. I have put it on button2 and the problem disappeared. 

Just have to get used to use middle button to move the windows around in expo mode.

---

### Post by magnetpest2k7 on 2011-12-05
Even I am stuck with the same problem I remember a old school workaround for this problem. You will get the snap feature by doing this, but you have to snap the windows using shortcut keys and not by dragging your windows to the sides.

1. First disable the grid plugin in compiz this would remove the annoying orange window.

2. To get the snap feature enable commands in compiz and give the following commands for 0, 1 and 2 and finally go key binding in commands and set your convenient keys for command 0,1 and 2 

Command line 0
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x' `&& HALF=$(($WIDTH/2)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-1

Command line 1
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x' `&& HALF=$(($WIDTH/2)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,$HALF,0,$HALF,-1

Command line 2
wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz

---

### Post by bpmod on 2011-12-14
> **Larkspur said:**
> Dasumner, I think [this]("https://bugs.launchpad.net/compiz-core/+bug/875557") is our bug.  I followed the steps to reproduce, and I get the orange box every time.
I cannot reproduce this following the steps listed in the bug report.

But this box which used to cover the left half of the screen when it appeared, now covers the entire screen.

I cannot continue using Ubuntu/Unity/whatever if this does not get fixed.

I am not interested in 'workarounds'.

Any suggestions as to whether I should be switching from Ubuntu, this version (11.10), or just Unity?

Thanks

Brian

---

### Post by jwh400 on 2011-12-14
This is a Unity only problem as it doesn't happen in gnome. I booted into Unity for a few minutes the other day and I got this with no windows open. I got a full screen of orange by tapping the top of the screen with the pointer and a half screen of orange by tapping the right of the screen.

---

### Post by typhoon_tip on 2011-12-14
There is now a permanent fix, in Proposed repository, is a bug of Compiz plugin. I have updated and the bug is gone, without any workaround.

---

### Post by HousieMousie2 on 2012-01-01
Annoying little bugger.  Not exactly a work stoppage event, but distracting.  Glad they got a fix out.

---

### Post by Momof9Blessings on 2012-01-06
now I need to find the work around.... other than compiz....  it is associated with workspace switcher.... 

I fixed it yesterday and now can't remember what I did to fix it.... LOL

ooh I need to get that sticky note program onto my desktop.... LOL

---

