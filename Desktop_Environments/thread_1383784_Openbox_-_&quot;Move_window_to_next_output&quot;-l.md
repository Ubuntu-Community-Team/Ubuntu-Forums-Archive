---
title: "Openbox - &quot;Move window to next output&quot;-like option?"
date: 2010-01-17
forum: Desktop Environments
---

### Post by mDuo13 on 2010-01-17
I've been using Compiz since setting up my current system a couple months ago, but I'm currently experimenting with moving to Openbox, which seems more like my kind of WM (minimalistic but very configurable). It doesn't hurt that it doesn't fight with mplayer's gl renderer on my ATI (Radeon HD 5770) card.

Here's the deal. There's one keyboard shortcut in particular I was able to set up on Compiz that is super handy on my current dual-monitor setup. In CompizConfig, it's under the "Extra WM Actions" plugin, specifically the "Move window to next output" option. (This shortcut moves the current active window to approximately the same location on the next display in my multi-monitor setup.) I haven't been able to figure out if there's a way to do something similar in any other WM. Anyone have any ideas? 

Additional information about my display: I'm using ATI's "Multi-display desktop" feature, which creates a single large display and maps it across my two monitors, which are different resolutions, aspect ratios, and at different physical heights on my desk.

---

### Post by SabreWolfy on 2010-01-23
Sorry, can't help you, but I have a question about the "Move window to next output" setting.

I have GNOME panels on one monitor only. If I move a maximized window from this main window to the second monitor, the top of the window appears a distance below the top of the screen -- as though it is leaving space for the panel. As soon as I click on the window anywhere, it jumps to the very top of the monitor where it should be. Have you experienced this?

---

### Post by mDuo13 on 2010-01-24
SabreWolfy: I have not experienced the behavior you described, to my knowledge. I did discover some weird behavior if I clicked on my desktop and then used the "Move to next window" shortcut - it would move my Nautilus desktop to the other monitor, which was at a different height, which really screwed things up! The only way I found to fix it was to restart the WM.

Meanwhile, one of the folks in the Openbox IRC channel was able to answer my question. Turns out the functionality I wanted does exist in Openbox - here's the bit I added to my rc.xml file to make it happen:

(adjust the key settings as desired, put with the other <keybind>s in <keyboard>)
```
    <keybind key="W-Menu">
      <action name="MoveResizeTo">
        <!-- move to next monitor -->
        <monitor>next</monitor>
      </action>
    </keybind>
```

---

### Post by SabreWolfy on 2010-01-24
Thanks for the info. You mentioned your reasons for trying out OpenBox in your first post, but would you mind explaining a little more? I' ve used GNOME and KDE and XFCE of course; I'm using GNOME at the moment and I can't decide if I'd like to go back to KDE or XFCE for a while -- all desktop environments have their pros and cons. I've used OpenBox briefly when I was looking at CrunchBang. Are you using OpenBox on an *Ubuntu variant? How have you installed it and why? :)

---

### Post by mDuo13 on 2010-01-24
I'm using it on Linux Mint. I just used sudo apt-get install openbox and then set that as my default session from the login screen. I added stalonetray as a system tray, too - it's in my openbox autostart as stalonetray -w -p --ignore-icon-resize.

I like Openbox because (a) it doesn't fight with mplayer's gl renderer on my ATI card the way Compiz does, (b) it's easy to customize (adding keyboard shortcuts and stuff) from simple config files, (c) it's minimalistic, with no desktop icons by default and a handy right-click menu like I've grown used to with Litestep on Windows, (d) it's fast/responsive/resource efficient.

The only feature I sometimes miss from Compiz is the one that zooms in around the mouse cursor. That loss is well worth it in exchange for everything else, though.

---

### Post by SabreWolfy on 2010-01-24
Thanks for the reply -- OpenBox sounds appealing too. Sometimes having so much choice can be something of a curse. I'm familiar with GNOME and I like it and it works; KDE is muc more visually appealing and customizable and has a great set of apps; I like the crisp, efficient, lightweight feel of XFCE; OpenBox/FluxBox looks attractive too. I guess the only was is to systematically test them all in turn for a month or two and then decide.

---

### Post by stanca on 2010-02-13
Tested many of them so far and my favourites are E17-Ecomorph and Fluxbox.;)

---

### Post by enthy on 2011-03-22
yellow everyone

i try add this

    <keybind key="W-Down">
      <action name="MoveResizeTo">
        <!-- move to next monitor -->
        <monitor>next</monitor>
      </action>
    </keybind>

in this file /home/*/.config/openbox/lxde-rc.xml
and reboot and my windows still in the same monitor ;(

i think my xorg is ok because i could see my cursor in the next monitor.

where is my mistake ;?

thank a lot
for this real solution

---

### Post by SabreWolfy on 2011-09-16
Finally got around to testing out this functionality in CrunchBang Statler OpenBox. Works perfectly :) Window-Menu key moves the active window to the other monitor :) Thanks mDuo13 :)

---

### Post by SabreWolfy on 2011-09-16
> **enthy said:**
> yellow everyone

i try add this

    <keybind key="W-Down">
      <action name="MoveResizeTo">
        <!-- move to next monitor -->
        <monitor>next</monitor>
      </action>
    </keybind>

in this file /home/*/.config/openbox/lxde-rc.xml
and reboot and my windows still in the same monitor ;(

i think my xorg is ok because i could see my cursor in the next monitor.

where is my mistake ;?

thank a lot
for this real solution

Check that nothing else is bound to W-Down earlier up in the config file? Check that you've put the code in the <keyboard> section of the file.

---

