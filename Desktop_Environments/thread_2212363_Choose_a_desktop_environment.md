---
title: "Choose a desktop environment?"
date: 2014-03-20
forum: Desktop Environments
---

### Post by DrPotoroo on 2014-03-20
I'm know there are lots of "which is the best desktop environment" threads out there. I've read several. However, I'm after a setup that will meet specific needs. I have tried several but realise this will take forever if I have to try everything - plus I may think I can't do something that someone else may know I can. So.... calling for help from those who know your desktop environments intimately.

I have a new surface pro (original, not version 2). So far ubuntu 13.10 seems to work pretty well "out of the box". If anyone has experience with another distribution on the surface pro, please let me know, though.

I will be running a two screen setup - surface pro display and external 32" HDTV. What I need from my desktop environment / window manager is:
[LIST=1]
[*]ability to control which screen applications open on (have achieved with compiz in the past on Ubuntu 12.04 with gnome classic)
[*]ability to easily move a window between screens (hotkey would be nice)
[*]ability to clone one screen to another while maintaining my window arrangements across two screens (have achieved this with compiz "clone output" plugin on 12.04 with gnome classic)
[*]for the second screen to show NO icons, menus, taskbars, etc. - just a background image - unless I place a window on that screen
[*]ability to prevent notifications from appearing on my external display
[/LIST]

I'd be perfectly happy with unity except that the compiz clone plugin seems to be absent in 13.10 (is there a way to add plugins?) and, most frustratingly, I CANNOT ELIMINATE THE GLOBAL MENU. I might be able to accept a workaround - like running a program that displays a full-screen picture and covers the global menu - if this could be sufficiently reliable.

---

### Post by deadflowr on 2014-03-20
The extra plugins should be part of the package compiz-plugins.
It was part of the package compiz-plugins-extra before.
```
sudo apt-get install compiz-plugins
```
That should install the clone plugin.(as well as a boat load of others)

If you feel lucky, and want to do a little testing, 14.04 has an option(easily accessible) to turn off global menus.
It's right in the Appearance section of system settings(in the section for behavior)

---

### Post by DrPotoroo on 2014-03-21
Thanks very much! Good to know I can add those compiz plugins. The option in 14.04 to turn off the global menu bar sounds promising. However, I'm wondering if I will still have the gray bar at the top of the screen anyway (with the login name, wifi icons, etc)? That is what I really don't want on my second screen.

---

### Post by deadflowr on 2014-03-21
Yes, you still get the normal icons up top, like wifi and sound if that's what you mean.
The global menus will simply be disabled.
The appearance feature disables them for all, but if you really wanted to, there is also a new section in dconf/gsettings to blacklist and whitelist global menus per application.

Edit: This is a good thread of what's new in 14.04
[http://ubuntuforums.org/showthread.php?t=2184706](http://ubuntuforums.org/showthread.php?t=2184706)

enjoy.

---

### Post by DrPotoroo on 2014-03-21
Thanks for the link. I see from that that I can remove my username from the menu bar strip - that is a slight improvement. My problem is that I use the second screen as a kind of "electronic whiteboard" with clients and the ribbon and icons at the top really spoil the look. I it is hard to appreciate what I mean without describing in detail how I use it. But it is a bit like how if the windows xp start bar didn't go away when you did a powerpoint presentation it would make the presentation look unprofessional.

---

### Post by DrPotoroo on 2014-03-27
Turns out I can still achieve a "gnome classic" look by installing the gnome session flashback package:
```
sudo apt-get install gnome-session-flashback
```
Compiz works with the clone plugins and I get no menu bar on my external display. Perfect.

---

### Post by silex89 on 2014-03-28
When I was running Arch Linux, I learnt a lot about building your own desktop experience based upon the use of a Standalone Window Manager, the main advantages this has are that you can run exactly the services and apps that you need very transparently and this will also help you to reduce possible resource hogs of other programs that you don't really need or use. Sometimes it's tricky and even dangereous, but overall a very enriching and positive experience.

Give it a try with Compiz, I know there's a bunch of articles and tutorials about building a customized session based on that WM that will fit your specific needs, then you can move on to some other window managers that are more lightweight if you're so inclined.

Best of luck! :D

---

### Post by frank18 on 2014-03-29
> **DrPotoroo said:**
> Turns out I can still achieve a "gnome classic" look by installing the gnome session flashback package:
```
sudo apt-get install gnome-session-flashback
```
Compiz works with the clone plugins and I get no menu bar on my external display. Perfect.


gnome-session-flashback  (Metacity) it's what i'm running in Ubuntu 14.04 beta1 and i'm happy with it, i would run Unity if they solve the problem with the Minimize button function that it's available but it's not supported and does not work right.

---

### Post by deadflowr on 2014-03-30
> **frank18 said:**
> gnome-session-flashback  (Metacity) it's what i'm running in Ubuntu 14.04 beta1 and i'm happy with it, i would run Unity if they solve the problem with the Minimize button function that it's available but it's not supported and does not work right.

Don't know what you mean, but the new minimize button that was included with trusty works as advertised.
It is only marked as unsupported because nothing else will ever be done with it.
And there is no need to do anything else with it.

---

### Post by frank18 on 2014-03-30
> **deadflowr said:**
> Don't know what you mean, but the new minimize button that was included with trusty works as advertised.
It is only marked as unsupported because nothing else will ever be done with it.
And there is no need to do anything else with it.

Thanks for your reply: how does it suppose to work? i ticked that function but it started to work funny like freezing,
the minimize button suppose to work like in Gnome Classic, bring the Page to the task-bar is'nt it?

Also there is this link that one has to add papas to get that function

[http://www.omgubuntu.co.uk/2014/03/enable-minimise-click-unity-7-ubuntu-14-04](http://www.omgubuntu.co.uk/2014/03/enable-minimise-click-unity-7-ubuntu-14-04)

---

### Post by deadflowr on 2014-03-30
> **frank18 said:**
> Thanks for your reply: how does it suppose to work? i ticked that function but it started to work funny like freezing,
the minimize button suppose to work like in Gnome Classic, bring the Page to the task-bar is'nt it?

Also there is this link that one has to add papas to get that function

[http://www.omgubuntu.co.uk/2014/03/enable-minimise-click-unity-7-ubuntu-14-04](http://www.omgubuntu.co.uk/2014/03/enable-minimise-click-unity-7-ubuntu-14-04)

Well, it only minimizes when you only one window for the app running open.
Any more than one and it does the usual window spread, where it shows all the windows for the app and you choose which one to draw the focus.
If that makes sense.

As far as a taskbar goes, think of the launcher as an imbedded taskbar.
Open apps in the launcher have a clearly marked arrow next to them indicating they are running.
The case is , as it has been for a long time(not sure if always, but close) that if an app is running it will show an arrow.
An arrow on the left means it is running. And an arrow and the right means it is the windows with focus on the desktop.
So, while you might have multiple arrows on the left side, which would mean multiple windows open, you will only ever have one arrow on the right side.
So I guess when you think of it like that, perhaps you can consider it somewhat of a taskbar. Though not built in the same tradition.
Again, if that makes sense.


As for the ppa, that is for older versions.
I do find it funny that it's a ppa and not just a .deb package.
Since they clearly aren't going to maintain it.
My advice for anyone who decides to add it to a system, like precise, would be to disable the ppa after it is installed.
(Better advice would be to upgrade to trusty and save yourself the added unnecessary need to fiddle with the system more than you should.)

Dear me, I'm not sure I answered any question.
Sorry.

I think I got lost somewhere.

---

### Post by frank18 on 2014-03-31
Thanks deflwr for you detailed explanation,that's why i love Ubuntu cause is the best in every way,i've tried many other distros but nothing beats Ubuntu by it's support and software.

---

