---
title: "Compiz is broken and completely unusable"
date: 2012-07-18
forum: Desktop Environments
---

### Post by Destructo47 on 2012-07-18
Up until about a week ago, this computer was running fine. I had completely removed *gags* Unity and gnome-screensaver, and was running gnome-shell with gnome 3 and compiz. Everything was dandy, but that all changed when the fire nation attacked (sorry, I couldn't resist).

In all seriousness, something must've gotten screwed up. The only system file I modified was gnome-shell.css in an effort to get my custom panel image to show under certain applets (like the hplip systray and notification applets). I successfully removed the black bar undertone, but that didn't help me much. For the past few days, Compiz has crashed randomly while I was in the middle of doing something. If I try to enable it again, my screen comes up garbled and scrambled. Not only that, but I have no window controls, and opening or closing anything results in an even more corrupted screen. Luckily, opening a terminal with Ctrl+Alt+t seems to stop it until I close something.

Ubuntu 12.04 Precise Pangolin (32-bit)
Ati Radeon 9250 Pro (using "radeon" driver)
Compiz is the latest version as of 7/18/12 15:20 EST
Metacity works without problems, but no compositing

Just recently, I did a partial upgrade after 'sudo apt-get install -f'. Now, Compiz doesn't start at login (I have 'compiz --replace &' set as a startup app), and I get the same problems as before. Compiz runs, but certain actions garble the screen. I have tried issuing a few TTY commands like the compiz unset command, but it did absolutely nothing.

A side note: before all of this happened, I would get random text and graphical corruption (nothing affecting the whole screen, but window titles and such).

I'm unsure on how to file bug reports (if this is one), but I do know where they are reported. Has anyone had these problems and been able to fix them, aside from a clean install?

---

### Post by Version Dependency on 2012-07-18
First, are you sure you running Compiz in Gnome Shell?  Unless something changed recently, Compiz and Gnome Shell don't mix well and is not supported.   Gnome Shell is tightly integrated with Mutter.

---

### Post by Destructo47 on 2012-07-19
Yes. I was running Compiz under Gnome Shell and it was working (almost) flawlessly, until the events of this past week. I'd had that setup for quite a while now.

I have another different but still relevant issue now as well; I switched out my Acer AL1916W for a 19" Insignia TV so I could watch TV from my desk. Before, I had the AL1916W and an Acer X191W in dual setup (vertical stack because of my video card's texture limit). On the Insignia TV (called 'BBY' in display settings), I can set the display resolution to 1440x900, but it only will show a 4:3 resolution (1200x900 by the looks of it). I tried switching the resolution for it, but I only ended up getting the garbled display mentioned earlier. Opening a Terminal with Ctrl+Alt+T didn't save me this time, however, and I was forced to do a hard shutdown.

Please note that the TV will only be there temporarily, and that the real issue is still the mangled screen.

---

### Post by Version Dependency on 2012-07-19
> **Destructo47 said:**
> Yes. I was running Compiz under Gnome Shell and it was working (almost) flawlessly, until the events of this past week. I'd had that setup for quite a while now.

Well, I don't know how you got Compiz working in Gnome Shell.  Gnome Shell was built with the Mutter window manager and they are very tightly integrated...so tightly integrated that I'm pretty sure it's not supposed to be possible to use any other window manager (similar to how Unity is built into Compiz so you must use Compiz).   I just logged into Gnome Shell on my machine to see if this has changed and a compiz --replace crashes the Shell.  I had to drop into the command line to get out of it.  Metacity --replace resulted in the same thing.

---

### Post by thatguruguy on 2012-07-19
> **Version Dependency said:**
> Well, I don't know how you got Compiz working in Gnome Shell.  Gnome Shell was built with the Mutter window manager and they are very tightly integrated...so tightly integrated that I'm pretty sure it's not supposed to be possible to use any other window manager (similar to how Unity is built into Compiz so you must use Compiz).

This.  You can read more directly from the Gnome devs [here]("https://live.gnome.org/GNOME3Myths#I_can.27t_use_Compiz_with_GNOME_Shell.21").

---

### Post by Destructo47 on 2012-07-20
Well, I somehow managed to get it working for at least a couple months. I'm 100% sure that I was using gnome-shell, firstly, because I installed it, and secondly, I was able to modify gnome-shell.css and see results after modifying the panel section and restarting gnome-panel. I'm 100% sure that I was using Compiz because I didn't get the error message from Docky telling me that it needs desktop compositing, and I was able to acitivate visual FX like wobbly windows, semitransparent windows, and painting fire on the screen.

So what should I do at this point? I mean, obviously this is an unprecedented issue, but it worked without problems for a while. So why is it just now starting to @&%$ up on me? :confused: My guess is that it had something to do with my partial upgrade, but I did that because of this issue.

Maybe there's a better approach to this. Does Mutter allow for compositing? That's really all I'm asking for, so that Docky doesn't look like a fat panel at the bottom of my screen, and I can have semitransparent windows. I don't need all of the other effects that Compiz has, but I do want the opacity effects, as well as the window blur. If I could get compositing out of Mutter, I would be fine with removing Compiz. Is Mutter integrated with gnome-shell, or is it just another package/dependency?

---

### Post by thatguruguy on 2012-07-20
> **Destructo47 said:**
>  Does Mutter allow for compositing? That's really all I'm asking for, so that Docky doesn't look like a fat panel at the bottom of my screen, and I can have semitransparent windows. I don't need all of the other effects that Compiz has, but I do want the opacity effects, as well as the window blur. If I could get compositing out of Mutter, I would be fine with removing Compiz. Is Mutter integrated with gnome-shell, or is it just another package/dependency?

Mutter is the compositing window manager for Gnome Shell, so by definition it does compositing.

---

### Post by Version Dependency on 2012-07-20
Mutter is a compositing window manager.  If you want to run Gnome Shell, you really are going to have to use Mutter.  Nothing else is supported so even if you get another window manager to work with it for awhile, it likely won't work forever since the Gnome team is pushing out updates regularly.

---

### Post by Destructo47 on 2012-07-21
Alright, so how would one go about activating Mutter, or is it forced to run alongside gnome shell? I don't want to end up having to reinstall my whole system, so a clear explanation would be greatly appreciated. Does the --replace command work for Mutter, or do I need to just remove Compiz and type some obscure command in console mode?

---

### Post by Version Dependency on 2012-07-21
It's probably best to start by simply purging and then reinstall gnome-shell.

```

sudo apt-get purge gnome-shell
sudo apt-get install gnome-shell

```

See how that goes first.  Hopefully, you will get a default Gnome Shell session.

---

### Post by Destructo47 on 2012-07-21
That works, but I ended up having no window controls, so I had to run 'mutter --replace &' to get them back, since Mutter apparently didn't start on its own. I now have to have that command as a startup application, since the 'nohup' command doesn't work for some reason (closing the terminal still kills the process).

However, Mutter doesn't seem to be applying my chosen theme to anything. It seems as though it doesn't like the Zukitwo theme, and instead uses the "Simple" theme. I checked in "Advanced Settings", but I am unable to change my theme or window theme. I can click on the drop-down menu, but the highlighted theme doesn't change, and clicking on a different theme does nothing but close the list. I should also mention that I've experienced a noticable performance drop while trying to change these themes.

---

