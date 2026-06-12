---
title: "Compiz enabled by default?"
date: 2009-11-14
forum: Desktop Environments
---

### Post by prkos on 2009-11-14
I had compiz working perfectly after installing Karmic. 

Recently I had to use Remote desktop viewing and it wouldn't change screens when Compiz was on. So I went to Preferences > Appearance > Visual effects and clicked None to turn Compiz off so sharing worked. 

But now after every restart I get Metacity instead of compiz, I installed Fusion Icon and it says that Compiz and Emerald are active but it only turns on when I Reload Window Manager. 

How can I get that old behavior where compiz and emerald would turn up by default? 

I can now use Fusion Icon when remote viewing is needed so I guess this will solve the mess when turning Visual effects off.

---

### Post by Kilz on 2009-11-14
Simple, go back to  Preferences > Appearance > Visual effects and select effects instead of none.

---

### Post by prkos on 2009-11-14
I just tried it and now Compiz effects don't work (Cube, application switcher...) 

I remember before when everything was fine nothing was ticked in the Visual effects.

Edit: I tried to reload the window manager but it logged me out (X crash?) 

when I logged back in I reloaded the window manager (cause I get Metacity even though in Fustion Icon it say Compiz). But when I go to Compiz settings manager I see several of the options have been disabled, I guess that's what Visual effects did. 

These are the disabled effects: Opacity, Brightness and Saturation, Desktop Cube, Rotate cube, 3D windows, Window previews. Sounds like my Compiz preferences were reset to default. 

It's all working now but I just need a way to make those settings "default" so I don't need to relaod the manager after each reboot.

---

### Post by Perturbed Penguin on 2009-11-17
When he had you select one of the 'enabled' options under visual effects that reset all of your compiz settings to their defaults for that selection... you will unfortunately have to redo all your customizations. I am currently having this same issue, metacity is loaded at boot but I want compiz to be loaded by default. A quick fix is to add 'compiz --replace' as a new startup program under 'startup applications' or to simply run that same command using alt+f2 after you are booted up. I would like to find something more natural than this though and i know it can be done somehow. I'll let you know if/when I find more info.

---

### Post by Perturbed Penguin on 2009-11-19
Disclaimer:
I am absolutely certain there is an easier and less lengthy process to reset Compiz as the default window manager, nevertheless the following is exactly what I did to fix my system and it ought to work fine for you... just an fyi I am running 9.10 Karmic but this should still work on any Ubuntu system and likely other similar distros as well. Also if it seems I am babying you too much please forgive me I simply tried to write it so that anyone could follow the steps. Hope it helps! ;)

Fix:
Ok, so here is what I did to fix this issue. First off you will want to go to the compiz settings manager.('ccsm' is the command if you want to open it through 'alt+f2') Go to the 'preferences' tab on the bottom left, WITHOUT hitting any of the other buttons, click on export and save your configuration file somewhere. Now you will want to hit 'alt+f2' to open the 'run application' dialog - type 'metacity --replace' in this command box and press enter. This will switch you to the metacity window manager so that you can do the next step without worrying about things freaking out... just in case. Now you will want to uninstall 'compiz' and 'compiz fusion icon' from your system - you can do this by going into the 'Ubuntu software center' or 'add/remove' and searching for compiz. At least in the software center you should now have something like four packages... uninstall both 'compiz' and 'compiz fusion icon'.(you don't need to worry about removing the settings manager - leave it be) Now right click on your desktop to go to 'change desktop background' or 'appearance settings', click on the 'visual effects' tab. Select 'normal' or 'extra'. This should re-setup compiz as the default window manager. 

Cleanup:
At this point go ahead and reinstall both 'compiz' and 'compiz fusion icon' through the software center or whatever other means you prefer. Reopen the compiz settings manager and restore your previous settings from your saved file by clicking 'import', you will likely have to select the tab at the bottom right of this 'open file' dialog which says 'Profiles (*.profile)' and instead select 'all files'. Now if previously you took my quick-fix and added a 'compiz --replace' startup app go and remove that, it will no longer be needed. You should now be able to reboot and have compiz start up as your window manager by default!

Again, I hope this helped!! If anyone has any questions feel free to ask.

---

### Post by Rasheeke on 2009-11-19
I'd like to say that Perturbed Penguin's fix works great.  I've been having to open compiz and turning it on every time I started the computer, now it happens by default

Also fixed some other issues I was having with the rotate cube and viewport switcher I was having.  Out of nowhere no compiz effects were working that involved the mouse hovering over the desktop but worked fine overtop any other window.

Not only is that fixed but now compiz is the default.  This is great news.

Thanks Perturbed Penguin.

---

### Post by Perturbed Penguin on 2009-11-20
Great! Good to hear that someone else tested it and came up with the same results! ;)

---

### Post by prkos on 2009-11-26
Thank you! It worked for me too!! I followed your steps exactly :)

---

### Post by Dave M G on 2009-12-06
Solution worked for me as well.

I had the exact same problem with Remote Desktop causing Compiz to malfunction, exactly as described in the original post.

---

### Post by Dave M G on 2009-12-08
Unfortunately I spoke too soon.

I thought the solution posted by Peturbued Penguin had worked, but after another reboot, the problem is back.

Compiz does not load automatically, although if I look in the Compiz Fusion Icon, it is already set to be the window manager. If I reload the window manager, then Compiz is enabled.

However, the performance is noticeably slower.

Compiz worked fine for many months on Karmic, and has only died recently after using Remote Desktop.

I know Remote Desktop is the likely catalyst because I have always had to turn of Compiz before enabling Remote Desktop, which I use quite often. After coming out of using Remote Desktop, I turn Compiz back on, the performance is slow, so I reboot, and then everything is fine.

But this one time a few days ago, I rebooted, and Compiz was not on. And since then it has been problematic.

Right now, after having tried the fixes here in this thread, the status is that Compiz does not automatically start on boot up, and some of the effects are not taking hold. For example, I have my windows set to "burn" when closed, but they are not doing so.

Any help to get Compiz back to rational and reliable behaviour would be much appreciated.

---

### Post by Perturbed Penguin on 2009-12-11
hmmm... that sounds like a predicament, lol. Have you re-tried the steps I posted earlier just to be certain nothing was missed? I suppose you could try my first post and add the 'compiz --replace' command to the startup app list. It is a less clean way of fixing the problem but I see no reason why that wouldn't work... but then I also am not sure why the other fix didn't work for you either. Why don't you take a look at this link and see if this bug is related in any way shape or form(I am thinking it may be related to the initial issue you were having):

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126)

---

### Post by Dave M G on 2009-12-11
Perturbed Penguin,

Thanks for replying.

I just went through your steps one more time to be sure I was doing them all, and I am still stuck with Compiz not starting when I reboot.

I have to type the following code into a terminal window after every reboot to get compiz to start:
```
compiz --replace & emerald --replace &
```

A couple of things have changed:

If I try to put the above code into the list of startup applications, it is not there after rebooting.

The default window manager after rebooting is always Metacity, but even it doesn't load. My windows don't have any decoration at all. If I check the settings in fusion icon in the Gnome Panel, it says the window manager is Metacity, and I have to reload it to get it to start.

Any ideas?

---

### Post by Perturbed Penguin on 2009-12-13
Hmm, well one idea I have is that perhaps you can add two separate entries to the startup app list instead of concatenating them, for example:
Entry 1: compiz --replace
Entry 2: emerald --replace

If this does not work maybe you could look into completely removing all compiz and emerald folders/files and reinstalling them. This is essentially what I was attempting to do with my posted fix but there are certainly ways of being more thorough in the removal process than what I did. This thread may help in this regard...
[http://ubuntuforums.org/showthread.php?t=601310](http://ubuntuforums.org/showthread.php?t=601310)

...if not then search around for where compiz and emerald files are located and look into removing these before reinstalling compiz and emerald. If you go this route I would recommend switching to metacity and removing compiz and emerald first before playing around/deleting any such remaining files.

Another idea is perhaps there is some sort of x.org file somewhere that you could edit in order to have it boot the proper window manager? Not AT ALL sure about this last idea but it is an idea to fall back on if nothing else seems to do the trick.

Not sure what else to recommend other than a fresh install which is obviously the very last resort and something you are not likely very keen on doing for good reason.

Let me know how things go, esp. if you find that the problem is something completely different from what I have put you on track for. Good luck! ;)

---

### Post by Perturbed Penguin on 2009-12-18
Any luck so far?

---

### Post by Dave M G on 2009-12-18
Thanks for following up.

1. I completely uninstalled and reinstalled all Compiz, Emerald, and Nvidia drivers. Basically rebuilt the whole graphics system from the ground up.

2. I looked in /etc/X11/xorg.conf, but there are no settings related to window manager settings there.

3. Every time I try and add Compiz and/or Emerald to the sessions, they disappear next time I reboot.

The current status is that every time I reboot, I still need to start Compiz manually.

---

### Post by Perturbed Penguin on 2009-12-18
Ok I may have found something useful, take a look at this thread, post #4 specifically:

[http://ubuntuforums.org/showthread.php?t=1138713&highlight=gnome-wm](http://ubuntuforums.org/showthread.php?t=1138713&highlight=gnome-wm)

Also this link seems to give some very useful info on this topic as well - stuff that probably won't help you fix your problem but some stuff I was not even aware of:

[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

### Post by Dave M G on 2009-12-20
Perturbed Penguin,

Thanks for finding that thread!

In my case, I found that the specific editing of the applications directory, as recommended in post #4, did not work.

However, this command brought my system back to rationality:

```
rm -rf .local/share/applications
```

Now the system launches Compiz and Emerald on startup.

I don't know what motivates you to be so helpful, but I appreciate your efforts in finding solutions!

Thanks!

---

### Post by Perturbed Penguin on 2009-12-21
Wonderful! Glad you got things fixed! Merry Christmas, Hanukkah, Kwanzaa or whatever else you may celebrate! Cheers. ;)

---

