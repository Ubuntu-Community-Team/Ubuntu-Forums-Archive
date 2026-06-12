---
title: "Menus in lucid (gnome) dissapear"
date: 2010-05-04
forum: Desktop Environments
---

### Post by ipatfrmww on 2010-05-04
I recently did a fresh install of Lucid on an HP Pavilion dv6 Notebook PC laptop.
At least once a day the main menu and context menus(desktop) in gnome stop working (They will not drop down/ appear). This includes all menus in gtk apps but not menus in not gtk apps such as firefox.

I have an autohide panel at the top of the screen for my main menu, shotly after the menus stop working (but never at the same time), the panel wont unhide and the workspace swtcher applet stops working, this corresponds to when the buttons on the panel I can still see (at the bottom) stop working.

When the workspace switcher applet goes, so to does the ability to switch using hotkeys (ctr alt left/right)

Suspending then resuming the laptop usually fixes these problem. Sometimes however 2 suspends are needed to fully fix the menus.
It is possible for the context menu on the desktop to be working after a suspend, but not the main menu (but not always). A second suspend/ resume fixes this.

I also noticed that this happened one of the times I booted a lucid release candidate live CD on my machine.

I'm not sure but this may have something to do with the fact that I installed using a release candidate live CD instead of the proper release. (i have done all the updates)

---

### Post by ipatfrmww on 2010-05-13
I recently cleared the cache's of anything relating to gnome with Ubuntu tweak.
Since doing so a lot of the problems I mentioned have stopped happening or reduced in severity.

Now the summary of things that happen are that the menus in gtk apps won't drop down, and neither will the main menu or the context menu on the desktop(i.e.: all gtk based menus). And also gtk apps don't seem to respond to inputs of any kind.

Strangely buttons depress when clicked on, and panel buttons usually work, but everything else seems to be stuffed entirely (including non panel buttons I think). Notably menus wont drop down.
Attached is an example of what the main menu looks like when this happens.

Unlike before this problem can quickly be fixed by dropping back to command line, with ctrl-alt-F1, then resuming gdm (it used to take a suspend or a logout to fix it).

Now that I have workspace switching in compiz turned on I don't have problems switching workspaces. This points to the fact that this problem is isolated to gdm.
Also I have found that the workspace switching applet usually works (since I cleared the cache).

I'm not sure why this problem is happening, like I said a similar thing happened once while I was using the live CD, so I think it may be hardware specific (no idea how that is connected at all). I get the feeling however that it may be that gnome is progressively corrupting some internal cache or config file of its. I get this feeling because the problems kept increasing in severity over the course of a week, until I cleared the cache's. Now the problems are only those described above. (other problems included frequent full gdm hangs, and a couple of X crashes)

Now that I know more about it I want to post a bug report on this.
Somewhere where people who know about gnome will see it. Can anybody please tell me where the best place to do that would be (I'm a noob). [-o<

---

### Post by ipatfrmww on 2010-05-26
I figured out what was causing it.
As I mentioned before I have an HP Pavilion dv6 Notebook PC (product # : VW492PA#ABG). This has for its mouse pad a little button and light to turn the mouse pad on and off(see attached pictures)
Usually I don't use the mouse pad since I have an external mouse. As such i have taken to turning it off and leaving it off so that I don't bump it (it stays off after a restart). Since installing lucid a while back I have noticed that after turning the mouse pad off and then on again it no longer functions. Logging on then back off fixes this.

Anyway, a few days ago I decided that I would stop pressing the button ever and just leave it on all the time. A day ago I realised that I hadn't been having the problems with gnome that I have been describing above.

So I tried button, sure enough gnome locks up. But here's the thing, this will only ever happen once per session(I investigated). So if i go through the moves:
-turn pad off
- click up on main panel
- do a ctrl-alt-F1, then Ctrl-Alt-F7, all is well
  No matter what I do gnome is fine.
  Every second time I turn off the mouse pad then back on it works.
      So if I turn the mouse pad off then on it wont work. If i do it again it works, again it wont work etc.
      So the mouse pad works every 4th time i press the button, but the light toggles each time I press it.

-Then I log off, log back on, mouse pad works. Press the button , gnome is fine,
- turn it back on, mouse pad is stuffed, gnome is fine. 
-Then I turn the computer off, back on
-press the mouse off button
-gnome locks up ,
- turn it back on
       now the panel won't drop back down(from auto hide) and all i.o. fails on the bottom panel, so no workspace switcher.
- do a ctrl-alt-F1, then Ctrl-Alt-F7
-now I cant stuff up gnome no matter what I do

This problem seems to be directly linked to the working of the mouse pad in lucid. This is odd since it worked fine in Karmic. I will as such make a post in the hardware section now, and also post a bug on launchpad.

---

### Post by ipatfrmww on 2010-05-26
Pictures

---

### Post by ipatfrmww on 2010-10-06
Eventually i got around to posting a bug report for this.
Here it is in case anybody is wondering: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/655613](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/655613)

---

