---
title: "upgrade to natty has borked my desktop"
date: 2011-05-22
forum: Desktop Environments
---

### Post by sherbey on 2011-05-22
Hi, 
I'm was running 64bit maverick on an intel i3 clarkdale desktop; pretty much vanilla with the compiz spinning cube desktop displaying on my 720p HDMI telly. On 'upgrading' to natty my pc refused to display anything on the telly but can still be connected to via ssh. Assuming unity was the culprit I installed gnome and deleted unity; after plugging in a VGA monitor I finallly got an output onto a display device, then managed to configure the HDMI telly as a secondary display. Gnome is just a backdrop with no panels at all; I managed to get panels by ctrl-alt-T and typing 'gnome-panel &'; but this was only a temporary fix. If I try to run a terminal now it locks X and I can only restart via the ssh session.  

Currently all I have if I boot is the gnome backdrop. The pc auto logs on (as it did under maverick) so alternate logon screens can't be accessed as pretty much all I can do is run stuff via an ssh shell on my other pc.

What I'd like to do is have my desktop how it was before natty trashed it. Preferably without unity or its very irritating scroll bar widgets. Any helpful advice gratefully received.

Cheers   :(

---

### Post by TBerk on 2011-05-22
I'm not sure our experiences are the same but today (running 11.04, clean install since it's release) I found my desktop enviroment all screwed up; 

- Can't get any more than 640x480 resolution.
- Monitor undetectable, in terms of what it is and what it's capabilities are (it's the small Dell 15" at the moment).
- Able to toggle back and forth using Nvidia driver, no change.
- 'Safe Mode' booting and Low Rez mode allow actually the 1024x768 video enviroment I'm used to.

If I recall my system crashed yesterday abd I had to hard boot, thats when all this might have taken place.

As a control I was able to boot a LIVE CD 9.10 rc CD and run it as expected (hi-rez video, etc).

What I'm scouring around for right now is a way to nuke the preference file/folder for Unity and/or Gnome and rebuild.

---

### Post by Larkspur on 2011-05-22
> **TBerk said:**
> I'm not sure our experiences are the same but today (running 11.04, clean install since it's release) I found my desktop enviroment all screwed up; 

- Can't get any more than 640x480 resolution.
- Monitor undetectable, in terms of what it is and what it's capabilities are (it's the small Dell 15" at the moment).
- Able to toggle back and forth using Nvidia driver, no change.
- 'Safe Mode' booting and Low Rez mode allow actually the 1024x768 video enviroment I'm used to.

If I recall my system crashed yesterday abd I had to hard boot, thats when all this might have taken place.

As a control I was able to boot a LIVE CD 9.10 rc CD and run it as expected (hi-rez video, etc).

What I'm scouring around for right now is a way to nuke the preference file/folder for Unity and/or Gnome and rebuild.

Try opening Monitors and seeing if you can change the resolution from the drop down menu.  If it doesn't work first time, try clicking "dectect monitors" until it does.  This is a problem I've found in both 10.04 and 11.04, it doesn't happen often, but I don't know what causes it.

---

### Post by Copper Bezel on 2011-05-23
sherbey, there are a number of possible problems, here. One is that Compiz in Natty (not Unity specifically) has some graphics card support issues that Maverick didn't. Another is the process you used to switch - what do you mean that you removed Unity and installed Gnome? Gnome is already installed, and you shouldn't have to change any software to switch back and forth; which one you run is a choice at the login screen, in the Session menu that appears below the login window after you select your name.

To avoid this problem of not being able to log out without the panel, load Keyboard Preferences, select Layouts, and set the keystroke to kill the xserver in the Options for your current layout.

I'm not certain what's going on with the Gnome Panel not appearing at startup, but I'm not going to give any suggestions that could cause further breaking until I know what session you're running and how you got there.

The overlay scrollbars aren't a part of Unity, and you can deactivate them rather easily - check the link in my sig.

---

### Post by sherbey on 2011-05-23
The graphics card in use is the integrated Clarkdale intel one; I know this wasn't supported pre- 10.10
 
I used synaptic over a ssh -X session to remove unity and install gnome; I guess these are metapackages (I don't have access to the computer at this point); on my laptop (atom/ion based) nothing worked properly with unity installed - logging in using gnome resulted in no window decoration, hence the lack of desire to mess about with unity (unity itself didn't play nice on the laptop anyway)
 
As I said, locally I can't do anything - all I've got is a screen backdrop. CTRL-ALT-T pops the beginnnings of a terminal window up then locks X totally. I can shutdown the computer remotely using the ssh session, and looking in the Xorg.0.log there is a line about inifinite loops near the end.
 
Is it worth nuking the gnome configuration area ~/.gconf? Will gnome rebuild this at next boot with some hopefully sensible defaults?
 
Is there a way of inhibiting the autologon remotely via the ssh session?

---

### Post by Copper Bezel on 2011-05-23
A better method than erasing .gconf would be to run 

```
gconftool-2 --recursive-unset /
```

I think. The results should be the same either way, default configuration on your next boot. I'd install ubuntu-desktop as well, as I think removing Unity would have removed it and we can make certain you're not missing anything important. Along with ubuntu-desktop, gnome is indeed a metapackage (I don't have either installed.)

I've never used an SSH x-session, but if you can, run gdmsetup and make certain that the Classic desktop is selected as the default.

---

### Post by sherbey on 2011-05-24
thanks for the assistance Copper Bezel, I now have natty working on a VGA monitor. If I connect to the HDMI telly only I get no display (but I do get sound over HDMI); if I boot using the VGA monitor then connect the HDMI telly the display flips to HDMI and works fine. Apart from an insistence that the only HD resolution available is 720p60.

It all used to work under maverick :(

Is there any way of forcing the intel IGP to 720p50 at boot? xorg.conf gets overwritten at boot

---

### Post by sherbey on 2011-05-28
There seems to be quite a few HDMI related issues with natty after a bit of googling. Nothing will get the pc to boot to a working display on HDMI without the intermediate state of ONLY having a VGA monitor connected at boot, then connecting the HDMI device. I've added by tuppenceworth to [bug #758794]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/758794"). 
This featurette has pretty much rendered this computer useless to me for the moment as its a HTPC and therefore its display is my telly over HDMI; theres very little WAF in having an old monitor on the floor near the telly and grovelling about with leads at the back of the computer just to get the thing to do anything.

---

### Post by sherbey on 2011-06-06
As an update, the update to natty reset the defaults for the VNC server; it would appear that X is actually starting even though there is no display. I was assuming that the lack of a VNC server == no X which is not valid.

---

