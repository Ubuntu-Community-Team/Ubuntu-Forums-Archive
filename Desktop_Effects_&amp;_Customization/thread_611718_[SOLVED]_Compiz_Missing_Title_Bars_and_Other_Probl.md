---
title: "[SOLVED] Compiz Missing Title Bars and Other Problems"
date: 2007-11-13
forum: Desktop Effects &amp; Customization
---

### Post by oneadvent on 2007-11-13
I have read the other posts on this subject, but no solutions have worked for me.

I installed the compiz icon and then turned off the desktop effects under Appearance. I then went to the icon and choose to use Compiz. All the title bars were not only missing but I cannot select anything on the desktop, nor bring up new windows, or move the old ones.

So, I installed Emerald, and ccsm and tried every combination of window decorating that I could think of. No change. I uninstalled emerald, and tried to go back to Appearance and select one of the other 3 radio buttons, but all of them eventually revert back to disabled.

This all worked fine before. I tried to install a webcam, which did not work, and when I messed everything up by trying to add a module to the kernel I popped in the liveCD and installed on another partition, and then just moved over my home directory. Since then it has not worked. What is the deal? Is it time to do it again, maybe this time not copy everything, but just personal folders like pictures and videos?

Frustrated, Please help.

Josh

---

### Post by jimerickso on 2007-11-13
it might be time for a fresh install.

---

### Post by RTrev on 2007-11-13
> **oneadvent said:**
> I have read the other posts on this subject, but no solutions have worked for me.

I installed the compiz icon and then turned off the desktop effects under Appearance. I then went to the icon and choose to use Compiz. All the title bars were not only missing but I cannot select anything on the desktop, nor bring up new windows, or move the old ones.

So, I installed Emerald, and ccsm and tried every combination of window decorating that I could think of. No change. I uninstalled emerald, and tried to go back to Appearance and select one of the other 3 radio buttons, but all of them eventually revert back to disabled.

This all worked fine before. I tried to install a webcam, which did not work, and when I messed everything up by trying to add a module to the kernel I popped in the liveCD and installed on another partition, and then just moved over my home directory. Since then it has not worked. What is the deal? Is it time to do it again, maybe this time not copy everything, but just personal folders like pictures and videos?

Frustrated, Please help.

Josh

Just some thoughts.. doubt they're anything you haven't thought of.

I've found that if I install a basic system with Gutsy, like installing xorg, gdm,gnome-core, nothing works until I install compiz.  This is new with Gutsy, I never had that issue before.

When changing appearance, make sure all windows are closed.  I've had problems with ones which were open during the change.

Moving your entire home directory probably brought along the very settings which were messed up.  

Rather than saving /home, I always save just the config files for the apps I use.  In fact, I keep them on a different drive and just symlink to them.  Then I can do a complete fresh install, *including* /home, and simply put the symlinks back when done.

Hope some of this helps.

---

### Post by oneadvent on 2007-11-13
See the problem with fresh installs is that I have to go find my themes and set them all back up...plus the updates, and then there is the whole SE download that takes forever.

I wish there was an easier solution. Like why did it mess up to start with?

---

### Post by oneadvent on 2007-11-13
Well the new window thing did not work. You know I haven't restarted in over a week, maybe that would help.

It worked fine before the fresh install. I only had a problem with the modules that I downloaded. (which is a whole different subject.) I copied every thing in my home directory over which could be the problem, I mean maybe it isn't matching up correctly now.

---

### Post by RTrev on 2007-11-13
> **oneadvent said:**
> Well the new window thing did not work. You know I haven't restarted in over a week, maybe that would help.

It worked fine before the fresh install. I only had a problem with the modules that I downloaded. (which is a whole different subject.) I copied every thing in my home directory over which could be the problem, I mean maybe it isn't matching up correctly now.

I generally restart after most changes.  Got a nasty surprise yesterday when restarting.. had my mouse, but neither button worked.  All was fine before the restart.  Had to re-do the xorg config to fix it.  A restart would at least let you know where you stand.

How about a new install, then, one by one, copy over directories from your old /home until you find the one causing the problems?  You could keep your themes, etc., that way, unless it was .themes which is messed up.

Good old process of elimination.  Gonna be tedious, but may save you a lot of work in the future if something similar happens and you know precisely which directory is the problem.

---

### Post by oneadvent on 2007-11-13
Really I think that is the only answer. 

I will try that over the weekend. This is a work laptop too. (read: gaming) and I do not want to have it down for a day in the middle of the week.

I wish that all the compiz icon and ccsm was easy to install, but I always have to go out dependency hunting. 

Anyway, if there is no other alternative, that is what I will try.

Josh

---

### Post by RTrev on 2007-11-13
> **oneadvent said:**
> Really I think that is the only answer. 

I will try that over the weekend. This is a work laptop too. (read: gaming) and I do not want to have it down for a day in the middle of the week.

I wish that all the compiz icon and ccsm was easy to install, but I always have to go out dependency hunting. 

Anyway, if there is no other alternative, that is what I will try.

Josh

It's odd that your symptoms sound *exactly* like mine *before* I installed compiz.  I was setting up a slow and old machine, and wanted a very lean install, so did it the way I usually did.. install command line, then begin adding things.  I've done this often with Feisty, but with Gutsy I had your symptoms until I did the aptitude install compiz.  Then the window borders showed up, and so on.

It almost sounds like you disabled compiz by mistake while you were adding the button and emerald and all of that.  Maybe just try to get back to where you were.. by getting rid of emerald and doing a reinstall of compiz?

bob

---

### Post by oneadvent on 2007-11-13
> **RTrev said:**
> It's odd that your symptoms sound *exactly* like mine *before* I installed compiz.  I was setting up a slow and old machine, and wanted a very lean install, so did it the way I usually did.. install command line, then begin adding things.  I've done this often with Feisty, but with Gutsy I had your symptoms until I did the aptitude install compiz.  Then the window borders showed up, and so on.

It almost sounds like you disabled compiz by mistake while you were adding the button and emerald and all of that.  Maybe just try to get back to where you were.. by getting rid of emerald and doing a reinstall of compiz?

bob

That's a really good idea, I think I'll do that before I try reinstall. Maybe I just got a bad package or something.

---

### Post by Rupertronco on 2007-11-13
Good lord, don't reinstall, that's terrible advice. Post your xorg.conf file. What hardware are you using? My guess is that you're using nVidia, there are very simple ways to fix your window decorator, and this problem more than likely falls into a known "bug". Ccsm is very easy to install, but the fusion icon is unstable. There are a few guys writing a new fusion icon that has high hopes, but for now just get your system stable. I haven't rebooted the machine I'm currently on since I installed Gutsy on its official release day. The Gutsy version of Compiz Fusion is perfectly stable, even on a laptop. 

Make sure you use the purge flag when you remove compiz. Also check your home directory for the compiz folder (it's in the .config folder). Ditch that too. 

Re-install compiz and emerald and we'll get them both working AND decorating windows, along with whatever else you need.

---

### Post by oneadvent on 2007-11-13
> **Rupertronco said:**
> Good lord, don't reinstall, that's terrible advice. Post your xorg.conf file. What hardware are you using? My guess is that you're using nVidia, there are very simple ways to fix your window decorator, and this problem more than likely falls into a known "bug". Ccsm is very easy to install, but the fusion icon is unstable. There are a few guys writing a new fusion icon that has high hopes, but for now just get your system stable. I haven't rebooted the machine I'm currently on since I installed Gutsy on its official release day. The Gutsy version of Compiz Fusion is perfectly stable, even on a laptop. 

Make sure you use the purge flag when you remove compiz. Also check your home directory for the compiz folder (it's in the .config folder). Ditch that too. 

Re-install compiz and emerald and we'll get them both working AND decorating windows, along with whatever else you need.

Ok, I am good with just about anything to avoid the LONG process of reinstalling...lets see here is my xorg.conf file:
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
```

Oh, and I am not using Nvidia, I am using ATI. What is really weird is that it worked before I messed everything up.....(that sounds familiar.) I will remove and reinstall compiz immediately.

Thanks for the help

---

### Post by Rupertronco on 2007-11-13
You're not using ATi according to your xorg.conf, it says you have an integrated intel video card, which will work just fine. 

I need some specifications on your machine, what are you using? If you're unsure type the following command: ```
lspci | grep 'VGA'
```


Is there a chance your motherboard has both an integrated video and you added a card?

---

### Post by oneadvent on 2007-11-13
```
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```

Naw, your prob right. It is a laptop, and I think that I got my wifes laptop mixed with mine. she has an ati card.

no additions, all factory.

I did the reinstall, after the complete removal with the folders and everything.

---

### Post by oneadvent on 2007-11-13
Ok, a little different now. it seems to have everything working except the title bars.

I am downloading an emerald theme right now.

---

### Post by Rupertronco on 2007-11-13
Also download the ccsm. ```
sudo apt-get install compizconfig-settings-manager
```



This is good news, intel cards almost always play nice with compiz fusion.

---

### Post by Rupertronco on 2007-11-13
Now when you say title bar, is something wrong specifically with the title bar or is the whole window border missing?

---

### Post by Rupertronco on 2007-11-13
Before you activate emerald type this in a terminal and tell me what happens ```
gtk-window-decorator --replace
```

---

### Post by oneadvent on 2007-11-13
ok, I got called into work, so i am going to have to do that when I get home. I did try it with emerald, and i was still without the title bar or borders.

I will do it tonight and post a reply. (I work until 10pm Central time.)

Thanks for helping out thus far.

Josh

---

### Post by Rupertronco on 2007-11-13
Cool, I should be around.

---

### Post by oneadvent on 2007-11-13
Ok, I did that, but it did not do anything, it did not spit out anything or anything...um...here is what it said...:

```
jwelch@jwelch-laptop:~$ gtk-window-decorator --replace
                

```
but that doesn't really help....

---

### Post by rundee_f on 2007-11-13
have try to type **emerald** or **gtk-window-decorator** on Command line in Window Decoration of your CompizConfig??

---

### Post by oneadvent on 2007-11-13
Um...actually in the process of checking the above post, I noticed that window decorator was not even checked. I checked it and now it works. 

Humph..I think resetting everything is what did it.

---

### Post by rundee_f on 2007-11-13
does it solve ur problems with window border?

---

### Post by oneadvent on 2007-11-14
Yes the problem is solved.

It was solved by doing  a complete removal of compiz and deleting the configuration files in the home directory, reinstalling compiz, and check marking  window decorations in ccsm.

I will mark thread as solved.

Thanks everyone for your help!

---

### Post by rasker on 2007-11-14
There is a less drastic method to resolve this. I did it in Fedora 8 but I think it applies to Ubuntu as well.

The problem is in the gconf config. Look for the file <home>/.gconf/apps/gnome-session/rh/%gconf.xml and change the window manager setting to from compiz to metacity. If compiz window manager doesn't start it does not fall back to something else so you get no window manager and hence no title bar or borders.

that file exists in Fedora and might not in Ubuntu. If so then you will have to look for a file with 'window manager' in it somewhere in gnome-session.

R

---

### Post by oneadvent on 2007-11-14
That is a good work around, but the solution that we found above allowed me to use compiz.

However, for those not looking to use Compiz, and only Metacity, that may be an alternative to get it up and running.

Luckly my fusion-icon let me go to metacity whenever.

---

### Post by caryleslie on 2007-11-15
I was having the same problem with window title bars disappearing at what seemed like random times.  The fix I used was to go into System>Preferences>Advanced Desktop Effects Settings then scrolled down to effects and for some reason "Window Decoration" was now unchecked.  After checking the box my title bar came back.  It may seem like a simple fix and may not completely fix the underlying problem, but at least the title bar is back.  I hope your problem is as easy.

---

### Post by RTrev on 2007-11-15
> **caryleslie said:**
> I was having the same problem with window title bars disappearing at what seemed like random times.  The fix I used was to go into System>Preferences>Advanced Desktop Effects Settings then scrolled down to effects and for some reason "Window Decoration" was now unchecked.  After checking the box my title bar came back.  It may seem like a simple fix and may not completely fix the underlying problem, but at least the title bar is back.  I hope your problem is as easy.

My own settings kept changing also, and I could never figure out under what conditions.  I went back to Metacity and heaved a huge sigh of relief.  YMMV.

Bob

---

### Post by oneadvent on 2007-11-15
Well the last step to my solution is to check that window decorations box. I think that the main problem was just left over settings from before. 

I have not had my settings revert, and since I got it fixed, I havent turned it off except for gaming. It has thus far done great. 

Josh

---

### Post by EdGato on 2008-04-30
Hey, guys. Thanks for the tips... but I think I still have a long way to go in order to get Compiz working as expected on my PC.

Anyway, I'm using Xubuntu, and had the missing borders and title bars, and immovable windows, and non-functional Alt-Tab key combo problem since I attempted to use Compiz. Took me hours on this forum and this page to try out the advice given here, but still no luck. So I played around with the system. And finally got the windows working the way I'm used to again.

This is only for reverting to the original XFCE through the GUI, in case anyone happens to run into the same problem:
[LIST=1]
[*]Click Applications -> System -> Synaptic Package Manager
[*]Search for fusion-icon
[*]Once you've installed it, Click Applications -> System -> Compiz Fusion Icon
[*]Right-click the Compiz Fusion Icon on the top-right corner of the screen and select your Window Manager from there (assuming your XFCE configuration is the default - otherwise, look around the screen for the icon).
[/LIST]

Hope this helps someone.Still very much a noob - maybe someone can update this thread with the command-line version... :)

I'm off to try running Compiz Again... hehehe

---

### Post by dirtblack on 2008-05-01
Weirdly enough I'm having the same problem, Missing title bars. Mine is a bit diff but with same results.  Emerald doesn't work so I have to use the terminal and use "emerald --replace". At that point the new theme pops up and everything is grand.  But....... the terminal shows it's confirguring or something to that effect, I close the terminal and BAM.  My title bars are gone! Can anyone shed some light on this?

---

### Post by linfidel on 2008-05-01
> **dirtblack said:**
> Weirdly enough I'm having the same problem, Missing title bars. Mine is a bit diff but with same results.  Emerald doesn't work so I have to use the terminal and use "emerald --replace". At that point the new theme pops up and everything is grand.  But....... the terminal shows it's confirguring or something to that effect, I close the terminal and BAM.  My title bars are gone! Can anyone shed some light on this?
When you run a program from the terminal, the program becomes a child of the terminal process.  In theory, the terminal should not close while the program is running, or it should close it's child process.

Try running the same command from the run menu (usually Alt-F2, I think).  Don't check the "run in terminal" checkbox.  Let me know if that works for you.

[edit]
I just went through installing compiz for xubuntu, and had the same problem.  To fix it, I found that I needed to run "sudo compiz --replace".  You can do it in a terminal to try it out - add an ampersand at the very end to allow it to run in the background (sudo compiz --replace&).  That worked for me, and ran emerald.  It left me with the red title bar, which can be customized with the emerald theme manager in the settings menu, if installed.

I was then unable to move my windows until I enabled the move window plugin in the uncategorized section of CompizConfig Settings Manager.  There's also a resize window plugin in the Window Management section.

I have everything working now, including the cube rotation (had to modify a setting in General options, Desktop Size, Horizontal Virtual Size.

Hope this helps.

---

### Post by dirtblack on 2008-05-01
I tried running "emerald --replace" in the run application, didn't do anything. I then did what you edited  "sudo compiz --replace&"  then brought up emerald and emerald wasn't working.  I can actually make a cube and move my windows fine. Any other ideas?

---

### Post by linfidel on 2008-05-02
> **dirtblack said:**
> I tried running "emerald --replace" in the run application, didn't do anything. I then did what you edited  "sudo compiz --replace&"  then brought up emerald and emerald wasn't working.  I can actually make a cube and move my windows fine. Any other ideas?I think I spoke too soon.  I had Compiz working well, and it ran Emerald, so I assumed I would be able to customize the windows.  However, I, too, found that it didn't work.  I suspect maybe it uses the gnome library stuff I didn't install.  Since doing that would be halfway undoing the advantages of Xubuntu for speed, etc, I decided it was not important.  

So, I keep it for when I want to do something fast, and I have compiz installed on my full Ubuntu partition.  My system defaults to Ubuntu unless I choose Xubuntu.

---

