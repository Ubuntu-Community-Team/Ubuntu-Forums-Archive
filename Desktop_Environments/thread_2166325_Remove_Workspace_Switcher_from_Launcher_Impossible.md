---
title: "Remove Workspace Switcher from Launcher: Impossible?"
date: 2013-08-08
forum: Desktop Environments
---

### Post by r_avital on 2013-08-08
Gotta love Unty and the launcher.  Even after I spend 6 weeks testing alternatives like MATE Desktop, Mint+Mate, Kubuntu, xubuntu, shmubuntu, zabbabuntu, and I finally give up, and say, "okay, unity, I surrender to your will, I'll do things your way" - still no way to get things to work as advertised.  I respect those who dedicate their lives to studying an operating system, I just want to use an operating system, and this is beyond ridiculous.

Trying to remove the Workspace Switcher from the vertical launcher in Gnome3/Unity.

Found 69,429,834 articles on the web how to do it, and ALL of them say:
System Settings > Appearance > Click on yadda yadda

But guess what? on this installation of 13.04, there is no "Appearance" in "System settings."

There. is. no. Appearance. in. System. Settings.  And at least 64,200 of them swore that they were talking about 13.04.

So now what?  Found a thread [here]("http://ubuntuforums.org/showthread.php?t=1743698&highlight=remove+workspace+switcher") on ubuntuforums about finageling the number of rows/colums, which simply reduces the number of workspaces to 1, then reboot, and the switcher should be gone.  Tried it, for grins, and the switcher is still there.

Ran unity-tweak-tool.  Found the Workspaces item, opened it - same deal, if you only have one workspace, you MIGHT get rid of the icon.  Or not.

Silly to begin with, because if you check the thread referenced above, many people will tell you, and did, on that thread, that they want multiple workspaces, but NO icon - they switch via means provided by ccsm like "Viewport Switcher" or "Rotate Desktop" and such.  So I'm not crazy.

So there's that icon on the launcher, doing absolutely nothing useful (par for the course for unity I guess) except wasting space.  Who is the genius from Mars who came up with that idea??? Same one who came up with showing "upcoming events" in the Calendar when you're NOT highlighting the event's date, but doesn't give the date of the event?  Are they subjecting candidates to the "mirror test" at Canonical's HR?

Please save your flames for your favorite political forum or the cafe.  If you can suggest a way to get rid of it, I'd love to hear it.  Thank you.

---

### Post by papibe on 2013-08-08
Hi r_avital.

In Ubuntu 13.04 (vanilla, i.e., with Unity), there is actually an 'Appearance' under 'System Settings'. It has 2 tabs. On the one called 'Behavior' there's a check box called:
```
Enable workspaces
```
If you uncheck it, the 'Desktop Switcher' icon will disappear immediately.

Does that help?
Regards.

---

### Post by SweetAurora on 2013-08-08
Papibe, But what the guy is saying is that he dosen't HAVE the appearance settings. Something is broken on his install.

---

### Post by r_avital on 2013-08-08
Papibe,

Thank you, I appreciate this.  And thank you Kitsuneinari78 as well, your conclusion is probably correct.

Frankly, I don't remember ever seeing it, and if you say it's there, I believe you.

I made a point of staying away from gnome3/unity in this install, and concentrated on gnome-fallback with and without effects, so I don't believe I've even taken any opportunity to mess around with unity at all.

I'm pretty sure I've seen unity packages in Synaptic, so I suppose I could purge it, and reinstall.  If I do that, is there a reliable source somewhere of all the components that would need to be reinstalled, so that this option shows up?

Thank you.

---

### Post by stinkeye on 2013-08-09
Run...
```
sudo apt-get **-s** install ubuntu-desktop
```

The **-s** option will simulate without actually installing anything.
May give an indication of what's missing.
Do you have the package **gnome-control-center-unity** ?

---

### Post by r_avital on 2013-08-09
Thank you, stinkeye, 

Forgive my ignorance, what is the -s option?  Couldn't find it in the help listing for apt-get.

I'll try this after I sleep some.

---

### Post by stinkeye on 2013-08-09
> **r_avital said:**
> Thank you, stinkeye, 

Forgive my ignorance, what is the -s option?  Couldn't find it in the help listing for apt-get.

I'll try this after I sleep some.

From man apt-get....
> **-s, --simulate, --just-print, --dry-run, --recon, --no-act **
 No action; perform a simulation of events that would occur but do not actually change the system. Configuration Item: APT::Get::Simulate. 

 Simulated runs performed as a user will automatically deactivate locking (Debug::NoLocking), and if the option APT::Get::Show-User-Simulation-Note is set (as it is by default) a notice will also be displayed indicating that this is only a simulation. Runs performed as root do not trigger either NoLocking or the notice - superusers should know what they are doing without further warnings from apt-get. 

 Simulated runs print out a series of lines, each representing a dpkg operation: configure (Conf), remove (Remv) or unpack (Inst). Square brackets indicate broken packages, and empty square brackets indicate breaks that are of no consequence (rare).

...or use synaptic to mark **ubuntu-desktop** for install(or reinstall). It will list the packages to be installed.
Closing synaptic will discard the marked changes.

---

### Post by Kanthala_Raghu on 2013-08-09
Your saying that you don't have Appearances tab in your settings ? That's highly impossible... either you must have broken your installation (during Upgrade) i suppose. I suggest you re-install 13.04.

---

### Post by grahammechanical on 2013-08-09
If I remember correctly from my days of testing Raring Ringtail during its development cycle having the workspace switcher in the launcher is not enabled by default. I did many installs of Raring and I have done several installs of Saucy Salamander and I have yet to see workspace switcher enabled by default. 

I have also noticed that installing alternative desktops does more than bring in a desktop. It seems to bring in half the distribution, bringing in utilities and applications as well. And also changing Grub configuration files. It may be time for a fresh install to clear everything out and start with uncomplicated configuration files. Whether that is Ubuntu/Unity, Fedora or some other distribution is your choice.

Regards.

---

### Post by r_avital on 2013-08-09
stinkeye, Kanthala_Raghu, grahammechanical,

Thank you all for your helpful suggestions.  I believe it is definitely possible that some components are broken.  BUT -- when I was installing alternate desktops and such, I took care to keep them on separate systems:

1. I have a spare box that I use for testing.
2. I used Clonezilla to remove one and install another (say, remove ubuntu-raring and install xubuntu-raring, kubuntu-raring and such).
3. The only instance where different desktops were on the same system simultaneously, was when I had (as I do now) gnome3/unity, gnome-fallback, and gnome-fallback No Effects on the same box, which as far as I know, is supported, correct?

At any rate, I took stineye's advice and reinstalled ubuntu-desktop, which happened smoothly without incidents.  Still no "Appearance" after rebooting cold.

Another headache is that every time I log out/in or reboot, I have to open a terminal and issue "unity --reset-icons" for the launcher to even show up.  So any non-default icons/launchers in the vertical bar on the left that I set up (Thunderbird, remmina, etc) are gone.

True, reinstalling from scratch would probably, or definitely, resolve many problems.  But that's so Windows, isn't it?  If I'm going to go through that trouble, I'll do it with something more stable like Mint or xubuntu.

In any case, thank you all so much for your help!

---

### Post by stinkeye on 2013-08-09
I've seen your unity appearance problem in other posts.
I have Gnome, gnome-fallback and xfce DE's installed and unity is very stable.

Have you used the gnome3 ppa?
If so, may want to re-enable and purge.

PS I found you can remove the Workspace Switcher in dconf-editor while still using multiple desktops.
In **com.canonical.Unity.Launcher favorites**
you can remove the **'unity://expo-icon'** entry.
Note each entry is enclosed in single quotes followed by a comma and then a space.
The icon disappears immediately on the change.

---

### Post by r_avital on 2013-08-09
Okay, stinkeye, this might be a game-changer for me.  Because not only did it work, it also means I can use this as a way to add permanent elements to the launcher.  At least I hope so.

Marking this thread solved (speaking of which, thanks for keeping the most useful signature on the forums:) )

Thanks!

---

### Post by stinkeye on 2013-08-09
> **r_avital said:**
> Okay, stinkeye, this might be a game-changer for me.  Because not only did it work, it also means I can use this as a way to add permanent elements to the launcher.  At least I hope so.

Marking this thread solved (speaking of which, thanks for keeping the most useful signature on the forums:) )

Thanks!

Ok, good.

You may find the gsettings command useful.
Once the launcher is set up how you like you can save the current setting.
eg
```
gsettings **get** com.canonical.Unity.Launcher favorites
```
> [COLOR="#008000"]glen@Raring:~$[/COLOR] **gsettings get com.canonical.Unity.Launcher favorites**
['application://gnome-terminal.desktop', 'application://nemo.desktop', 'unity://running-apps', 'unity://devices', 'application://opera-browser.desktop', 'application://gedit.desktop', 'application://gnote.desktop', 'application://smplayer.desktop', 'application://gpodder.desktop', 'application://shutter.desktop', 'application://FFgenie.desktop', 'application://ConkyTimer.desktop', 'application://keepassx.desktop', 'application://Synaptic.desktop', 'application://gnome-system-monitor.desktop', 'application://Conky-Control.desktop', 'application://My Links.desktop']

You can save that output in a bash script to implement this launcher setting when needed.
Use the output from the **gsettings get** command, enclosed in double quotes with the **gsettings set** command.
eg
```
#!/bin/bash

gsettings **set** com.canonical.Unity.Launcher favorites **[COLOR="#FF0000"]"[/COLOR]**['application://gnome-terminal.desktop', 'application://nemo.desktop', 'application://opera-browser.desktop', 'application://gedit.desktop', 'application://gnote.desktop', 'application://smplayer.desktop', 'application://gpodder.desktop', 'application://shutter.desktop', 'application://FFgenie.desktop', 'application://ConkyTimer.desktop', 'application://keepassx.desktop', 'application://Synaptic.desktop', 'application://gnome-system-monitor.desktop', 'application://Conky-Control.desktop', 'application://My Links.desktop', 'unity://running-apps', 'unity://devices']**[COLOR="#FF0000"]"[/COLOR]**
```


To reset the launcher to default use....
```
gsettings **reset** com.canonical.Unity.Launcher favorites
```

---

### Post by r_avital on 2013-08-10
Wow, that's a bonus.  Thanks for the very useful info.

Saving this thread for future reference.  xubuntu is still crashing for me with compiz (I know, compiz is a losing proposition).  Giving Mint+MATE a last try, as that is all gnome2 code.  If that doesn't work, I'll reinstall Raring from scratch, and try to live with unity/Gnome3, as much as I dislike it.

Thanks again!

---

