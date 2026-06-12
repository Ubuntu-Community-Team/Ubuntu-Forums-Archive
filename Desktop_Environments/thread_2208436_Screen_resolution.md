---
title: "Screen resolution"
date: 2014-02-28
forum: Desktop Environments
---

### Post by microfox on 2014-02-28
Hi

I'm sort of new here.

I just installed Lubuntu 13.10 on my Macbook Air using Parallels Desktop.  One thing I find really annoying is every time I start Lubuntu, the screen resolution is set at 1920X1200 and I have to reset it to a level my old eyes can see anything. I have tried to save my settings but to no avail. 

One more question where in Lubuntu can I find a list of the Wifi hotspot available when I'm in a public area ?

Thanks for reading this and for any help someone can provide.

---

### Post by Dreamer Fithp Apprentice on 2014-02-28
Not precisely what you asked, but maybe of interest:
You know you can set font sizes, icon sizes, panel width and so on seperately, right? It is a little more trouble than just reducing your resolution but it does give you a more fine grained control and it doesn't come at the expense of degrading photo quality and so on. There is more than one place to do these things, and I'm working from memory here because I've switched to plain Openbox on Saucy and don't have Lubuntu ATM. I think from the menu - Preferences, Appearance. Or it might be System, Prefs, Appearance. Something like that. Keep exploring the dialogues and tabs. There are at least 3 main places to set fonts and lots of minor and ap-specific places as well. Another way to start would be to enter "lxappearance" in either a teminal emulator or a run box. To adjust the panel, right click on it and select (if I remember correctly) "properties".  When I use a panel, I like to run the width up to 50 or so and run the icon size up to match.  Whoever designed that gui decided that size 20 fonts is the most you should be allowed. Well, a bronx cheer to him/her/them. It's purely arbitrary. Find the text file that actually controls the panel (I think it's in /home/username/.config/ somewhere - look around and you'll find it) and you can enter higher values. With a wide enough panel it's no problem. All this is more trouble, but in the end it's a better result.

If you still want to do the resolution instead, I think you could put an xrandr (or maybe it's lxrandr) statement in the startup file that runs when the Lubuntu DE starts up. I forget what that's called in Lubuntu. Mine is ~/.config/openbox/autostart.sh. Lubuntu's is probably something like ~/.config/lubuntu/autostart.sh at a guess or they may just use the openbox one. Lubuntu has Openbox under it but they add a mare's nest of config files, menu xmls and the like, that in some cases supplement the openbox ones and in some cases replace them (when you boot into Lubuntu that is - the plain Openbox DE is still there if you want to choose it at the login screen). But knowing what to look for it should be easier to find. On the xrandr command (it IS just "xrandr", I just looked) this is an example:```
xrandr -s 960x600
```What numbers will work for your video card and monitor (more the monitor I believe) I don't know. Try "man xrandr". I wouldn't be surprised if it had a query function to tell you the allowed values.

---

### Post by daniel121 on 2014-02-28
if you left click on the wifi symbol in the bottom right you should have a pop up menu that shows the available hotspots.

---

### Post by microfox on 2014-03-01
Thanks for your answers.

While I used to be very handy in Windows and am now very familiar with everything about OSX, I am not very handy with Linux. That's the main reason I have installed and uninstalled different distros, over the last 12 years. 

I have tried that randr command but the 1280x720 sreen resolution that works for me in OSX, is not available in Lubuntu.

Also, the wifi symbol indicates that I have an Ethernet connection which of course, is not true at home and when I'm in a public area.

I have read quite a bit about this, the last few hours and I beieve that the problem may lie with the fact that Ican not install Parralleks Desktop tools as it is not available under the virtual machine menu.

I have searched the Parallels Desktop support and forums and whatever answers I found, did not solve my problem.

I tried to install Lubuntu on a very old laptop that I don't really want to use anymore and everything went fine.

---

### Post by Dreamer Fithp Apprentice on 2014-03-02
> **microfox said:**
>  . . . I have tried that randr command but the 1280x720 sreen resolution that works for me in OSX, is not available in Lubuntu.If you are talking about the same hardware booted in OSX vs. booted in Lubuntu that would make me STRONGLY suspect that you need to try some different drivers for your graphics card (or for the on-the-mobo-graphics-hardware if that is the case). The last few times I installed a 'buntu I used the mini.iso to install a basic tty system and built up selectively from that, so I'm not sure how the standard install goes now, but it used to be that you got a graphics driver that was righteously open-source and copy-left but unfortunately didn't work very well. The drivers that DO work well are propietary and you have to "opt-in" so to speak. And the difference is not always subtle and not always limited to the kind of apps you would think of as unusually demanding of the video card. For me, switching from the default one (I forget the name) to nvidia-current (propietary but still in the repository) made a HUGE difference in the legibility of my tty font.

 > **microfox said:**
> I beieve that the problem may lie with the fact that Ican not install Parralleks Desktop tools as it is not available under the virtual machine menu.I don't understand that. I thought we were talking about a regular install to a metal-and-silicon. If that is not the case, I'm not sure if anything I said applies.

---

