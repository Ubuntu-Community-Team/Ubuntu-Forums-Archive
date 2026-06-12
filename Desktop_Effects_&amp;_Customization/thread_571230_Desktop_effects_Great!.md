---
title: "Desktop effects Great!"
date: 2007-10-09
forum: Desktop Effects &amp; Customization
---

### Post by Siberius on 2007-10-09
I am a brand new Ubuntu user.  I've watched linus for many years but have never felt comfortable with it until this version of Ubuntu 7.04.  I just love it.  Really wish I could find something to replace my Adobe Creative Suite ... then I'd never go back.

One issue I've had a bit of difficulty with is the desktop effects.  When I first installed Ubuntu just over a month ago, I could drag a window to either edge of the screen andit would move to the next side of the cube.  After muching about the settings, somehow I've turned this off and cannot get it back.  i have the wobbly windows effect.. and I have set the workspaces to 4... but can'g get it to flip to another side by dragging to the edge.

I've been trying to figure it out for a month.  Can't get there.  Can anyone help?

Thanks,
Nick.

---

### Post by infornogr4phy on 2007-10-09
are you using just the standard desktop effects that come prepackaged with feisty? or are you using something else like compiz fusion etc?

---

### Post by Jouke74 on 2007-10-09
See the compiz documentation: [http://compiz.org/Workspace_Switcher_Fix](http://compiz.org/Workspace_Switcher_Fix)

And adjust the number of viewports in gconf-editor. [http://compiz.org/Gconf-Editor](http://compiz.org/Gconf-Editor)
Workspaces = 1, viewports is 4 (horizontal). 

Finally, don't use the clickable desks of the gnome desktop viewer as this results in a reset of your settings. And you will have the same problem again.

---

### Post by Siberius on 2007-10-09
Yes, it is the one that comes pre-packaged with Feisty.
Just love this OS!

> **infornogr4phy said:**
> are you using just the standard desktop effects that come prepackaged with feisty? or are you using something else like compiz fusion etc?

---

### Post by Siberius on 2007-10-09
Neither of these sites will open.  Even back to the root they won't open.

N.

> **Jouke74 said:**
> See the compiz documentation: [http://compiz.org/Workspace_Switcher_Fix](http://compiz.org/Workspace_Switcher_Fix)

And adjust the number of viewports in gconf-editor. [http://compiz.org/Gconf-Editor](http://compiz.org/Gconf-Editor)
Workspaces = 1, viewports is 4 (horizontal). 

Finally, don't use the clickable desks of the gnome desktop viewer as this results in a reset of your settings. And you will have the same problem again.

---

### Post by Siberius on 2007-10-10
I managed to figure it out.  
First I installed a restricted hardware driver for my Gforce video card.  Reboot.
Deleted the panel.  Added a new panel.  Then went to "Desktop Effect" and unticked everything.
Then tried to enable DTE.  Error... so I uninstalled the restricted driver. Rebooted.
then when to DTE again and enabled only the wobbly.  Added switcher to the panel.  configured it for 4 desktops.  Then when back to DTE and ticked the "Cube".  Now everything works perfectly again.

Just loving this OS.  Haven't had the need to boot into XP for nearly two days... HM......

Nick.

---

### Post by Stikz00 on 2007-10-12
Just yesterday I tried out VirtualBox. Emulating software for running a virtual OS. I installed Win XP on a virtual disk. So now I can easily 'run' Win XP iside of Ubuntu, and install Adobe CS3 on it. Try it out.

---

### Post by chalkie1975 on 2007-10-12
How do you install virtual box?

---

