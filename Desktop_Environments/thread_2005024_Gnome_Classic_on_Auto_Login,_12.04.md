---
title: "Gnome Classic on Auto Login, 12.04"
date: 2012-06-16
forum: Desktop Environments
---

### Post by mark bower on 2012-06-16
I **auto login** to my desktop.  In 12.04, how can I get Gnome Classic to be the default desktop, ie, appear at login.  I would like to return to what I had in 10.10(top bar had Application, Places, System).  

To get back to the classic gnome view (or what I believe may be called Gnome 2), what files do I need to change.  Please provide detail on their path, & how must they be changed?  I know how to work the terminal.  I have already downloaded as in "sudo apt-get install gnome-panel".  

I do not like Unity one bit and can hardly get it to work for me. A lot of commercialism seems to have been introduced?

---

### Post by mark bower on 2012-06-17
bump for help

---

### Post by Frogs Hair on 2012-06-17
I think this will work for 12.04, but you may want to confirm with a newer source before trying. Gnome-classic is listed last.  [http://ubuntuguide.net/ubuntu-11-10-how-to-auto-login-gnome-shell-gnome3-desktop/](http://ubuntuguide.net/ubuntu-11-10-how-to-auto-login-gnome-shell-gnome3-desktop/)

---

### Post by mark bower on 2012-06-17
No, unfortunately, the following code lines do not work for my 12.04 (you would think they would):
  sudo apt-get install gnome-session-fallback
  sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-classic

a file in the dir lightdm-set-defaults is named "gnome-terminal.desktop".  It contains:```
[Desktop Entry]
Name=Terminal
Comment=Use the command line
TryExec=gnome-terminal
Exec=gnome-terminal
Icon=utilities-terminal
Type=Application
X-GNOME-DocPath=gnome-terminal/index.html
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-terminal
X-GNOME-Bugzilla-Component=BugBuddyBugs
X-GNOME-Bugzilla-Version=3.4.1.1
Categories=GNOME;GTK;Utility;TerminalEmulator;
StartupNotify=true
OnlyShowIn=GNOME;Unity;
Keywords=Run;
Actions=New
X-Ubuntu-Gettext-Domain=gnome-terminal

[Desktop Action New]
Name=New Terminal
Exec=gnome-terminal
OnlyShowIn=Unity

```

Now it sort of looks like the line "OnlyShowIn=Unity should be something like OnlyShowIn=gnome-classic.  But I would like more advice before possibly messing things up.

---

### Post by Frogs Hair on 2012-06-17
I found anther guide for 12.04. [http://www.tejasbarot.com/2012/05/17/howto-change-default-user-session-ubuntu-12-04-lts-precise-pangolin-login-session-desktop-environment/](http://www.tejasbarot.com/2012/05/17/howto-change-default-user-session-ubuntu-12-04-lts-precise-pangolin-login-session-desktop-environment/)

---

### Post by mark bower on 2012-06-17
well, thanks hanging in with help suggestions.

no, the code lines also did not work, ie:
   /usr/lib/lightdm/lightdm-set-defaults -s gnome-fallback
   /etc/init.d/lightdm restart

the screen does go dark, but then Unity reappears.  I find it frustrating that the Canonical people set things up this way, ie, not an easy way to return to earlier desktops.  

surely i would believe that there must be a number of persons who boot via auto login and get their flavor of the gnome classic desktop?  if not using auto login, then it seems that the problem is mostly solved.

so, open for more suggestions.

---

### Post by kansasnoob on 2012-06-18
> **mark bower said:**
> well, thanks hanging in with help suggestions.

no, the code lines also did not work, ie:
   /usr/lib/lightdm/lightdm-set-defaults -s gnome-fallback
   /etc/init.d/lightdm restart

the screen does go dark, but then Unity reappears.  I find it frustrating that the Canonical people set things up this way, ie, not an easy way to return to earlier desktops.  

surely i would believe that there must be a number of persons who boot via auto login and get their flavor of the gnome classic desktop?  if not using auto login, then it seems that the problem is mostly solved.

so, open for more suggestions.

The standard Gnome classic session uses Compiz, whereas the Gnome classic (no effects) session uses Metacity. It would seem that some graphics chips have trouble running a standard classic session so just to see if that's part of the issue try logging out, then select classic (no effects) and log back in to see what things look like.

If you get a classic DE then try rebooting and see if you still get that session. If so you have it narrowed down to a conflict of sorts between your graphics chip, Compiz, and Unity. Sadly I don't know how to fix it :(

I have been making some notes about classic (no effects) here:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

If you find that you're able to run classic (no effects) but not standard classic then please post the output of:

```
lspci | grep VGA
```

That will tell us what graphics chip you have. I'd rather like to do some Googling to see if I can find an existing bug report and/or any possible work-arounds :)

---

### Post by VMC on 2012-06-18
> **mark bower said:**
> I **auto login** to my desktop.  In 12.04, how can I get Gnome Classic to be the default desktop, ie, appear at login.  I would like to return to what I had in 10.10(top bar had Application, Places, System).  

To get back to the classic gnome view (or what I believe may be called Gnome 2), what files do I need to change.  Please provide detail on their path, & how must they be changed?  I know how to work the terminal.  I have already downloaded as in "sudo apt-get install gnome-panel".  

I do not like Unity one bit and can hardly get it to work for me. A lot of commercialism seems to have been introduced?

Have a look at gnome-panel. Read about it [here]("http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed").

---

### Post by kansasnoob on 2012-06-18
> **VMC said:**
> Have a look at gnome-panel. Read about it [here]("http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed").

If you read the entire OP it says:

> I auto login to my desktop. In 12.04, how can I get Gnome Classic to be the default desktop, ie, appear at login. I would like to return to what I had in 10.10(top bar had Application, Places, System).

To get back to the classic gnome view (or what I believe may be called Gnome 2), what files do I need to change. Please provide detail on their path, & how must they be changed? I know how to work the terminal. **[COLOR="Red"]I have already downloaded as in "sudo apt-get install gnome-panel"[/COLOR]**.

I do not like Unity one bit and can hardly get it to work for me. A lot of commercialism seems to have been introduced?

I'm about 90% sure based on the info provided that it's a problem with Compiz, Unity, and the graphics chip conflicting ;)

It's generally an ATI Radeon problem, but other problems exist with "gnome-panel' + Compiz such as general panel appearance and garbled graphics.

That's also why Ubuntu considered [removing CCSM from the repos]("http://www.omgubuntu.co.uk/2012/01/should-ccsm-be-purged-from-the-ubuntu-repos") ;)

---

### Post by mark bower on 2012-06-18
Objective was to get a desktop in 12.04 that matched the desktop I like in 10.10, and do this with auto login.  My 10.10 desktop has top and bottom panels; the top panel has Applications,Places,System and icons for shutdown, sound, wifi etc.  On the bottom panel I have Trash and Forced Quit.  I have figured out how to get this desktop in 12.04, briefly as follows:

1.  Install 12.04, and during installation select the user login option, not auto login.  After installation you will be at the Unity desktop.
2.  Using the Ubu Software Center, install Gnome Shell
3.  Shutdown and reboot.  At the login screen, click on the icon in the upper right and select the option for "Gnome Classic(no effects)".
4.  Enter your passwd and press return - you will be at the Gnome Classic desktop.
5.  Change to auto login via:  Apps>Sys Tools>Sys Settings>User Accts>[unlock with passwd]>slide switch to show Automatic Login.
6.  Shutdown and reboot - the desktop will now be Gnome Classic.

Some basic tweaks.
1.  Add Trash and Forced Quit to the bottom panel by moving the cursor over the panel, then Alt-rt click, then Add and select options.
2.  Very helpful for me is to add the System Settings icon to the top panel.  This is done via Apps>Sys Tools>Sys Settings>[drag icon to top panel].

I probably should have stated that I wanted a simple desktop without regard to effects.  However, this is in part driven by fact that I have never been able to make them work.  @kansasnoob, indeed I have ATI(Radeon 9200 PRO) and nVidia(GeForce 6200) chipsets.  If I recall, nVidia did/does not support drivers for the older card.  But to be clear, I need nothing more in appearance than I now have.

Bottom line, if I can get other things working(or learn how to do them) in 12.04, I will stick with Ubuntu.  However, because of dislike for Unity(and I guess Canonical for not making it easy to revert to previous DE), I am now curious about Linux Mint and Gnome Shell Remix - ways to regain the desktop that I prefer.  Wonder if this might be a better approach than "rebuilding" the desktop in Gnome Classic?

---

### Post by mark bower on 2012-06-20
Well, I have downloaded and played a bit with Linuxmint 13 which has the Mate desktop.  I was astounded at how user friendly the Mint, Mate desktop is, can almost find everything intuitively.  So even though I have mastered what I needed in 12.04, if Canonical continues with Unity I may become a candidate for switching to Mint.  

Incidentally, I went a step further and installed Mate on 12.04(test HD), and it works nicely for how I like to maneuver on the desktop.

---

### Post by mark bower on 2012-06-21
Because of this experience, ie not liking Unity, I have done two additional things:  1) Tried LinuxMint 13 and 2) added the Mate desktop on top of the Gnome Classic installed in my 12.04.

I can see why many like LinuxMint - it is very user friendly and has an intuitive feel.  I will seriously consider using it in the future, especially if Canonical sticks with Unity.

Mate in 12.04 looks very nice, and I might just be satisfied with using it.  However, considering that LinuxMint 13 "works out of the box" and one has to install Gnome and then Mate to get something like the Mint desktop, well - -

---

