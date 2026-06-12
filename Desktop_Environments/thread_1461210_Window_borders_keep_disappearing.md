---
title: "Window borders keep disappearing"
date: 2010-04-23
forum: Desktop Environments
---

### Post by PCZahra on 2010-04-23
I recently upgraded the motherboard/processor on my computer (as in quadrupled the processor and octupled the ram). The new board has a built in GPU (intel) and from searching the forums, I think this is part of the problem.
Every time I boot up the computer, I need to open the Compiz icon and use it to reload the window manager before I see any title bars, borders, etc..
I've tried the .bashrc hack (metacity --replace), but that doesn't do anything. In fact, whenever I open the terminal, I need to have two tabs open in order to use it, and when I close it all the borders go away again (even when I haven't done anything).
Also, the onboard sound card (intel) doesn't work, but that's another task (I at least have a compatible card for that).

---

### Post by wojox on 2010-04-24
If your going to use metacity --replace, why don't you just disable Desktop Effects altogether?

---

### Post by PCZahra on 2010-04-25
I did that. No matter the setting, I always get no borders on startup.

---

### Post by ami7878 on 2010-04-26
I have exactly the same problem.  I didn't replace any hardware and cannot remember what i installed before this started as it only happen after restarting the computer.

For the moment, after reboot, I go into System -> Preferences -> Appearance, I select the 'Visual Effects' tab and just change the selected option.

From some reason I cannot start the terminal as long as the windows; borders are not there :confused:.

I tried to reinstall the Compiz but that didn't help either.

As I don't often reboot this is not a major issue but recently it started annoying me.

---

### Post by spayman on 2010-04-26
[COLOR=Navy][B]hey hey hey guys , i had the same problem with ubuntu 9.04 and 9.10 :)
there is a way to fix it in 9.04 but in 9.10 idk :(
all i know is that they totally fixed it in this new 10.04 lucid lynx version =)
am runnin it right now :D
windows is out the windows now .. !
well generally , i advice you to wait till the last ubuntu version releases (this weak) and download or upgrade to it
generally ubuntu karmic koala or w/e is full of bugs 
peace :)
[/B][/COLOR]

---

### Post by PCZahra on 2010-04-26
> **spayman said:**
> [COLOR=Navy][B]all i know is that they totally fixed it in this new 10.04 lucid lynx version =)
[/B][/COLOR]

I was hoping someone would say that! We'll see in two days.

---

### Post by andrea000 on 2010-04-26
This sounds like one of the compiz bugs open ccsm go to
the workarounds plug in and put a check in the legacy
full screen support and reboot this fixed mine and should
yours to.

---

### Post by PCZahra on 2010-04-28
Yeah, that didn't do it. Whatever is causing this is definitely affecting Metacity as well. It doesn't matter which window manager is selected when I log off, neither of them come back until I tell them to.

---

### Post by PCZahra on 2010-04-30
Ok, I did the upgrade, now I have Ubuntu 10.04 without window borders. :confused:

---

### Post by BillyG123 on 2010-05-02
Here's what worked for me:

1. compiz --replace
2. System > Preferences > Startup Applications > Options > Remember Currently Running Application

---

### Post by ptrinder64 on 2010-05-02
A suggestion here, if you go to Compiz have you selected the Windows Decoration option? If the answer is 'yes', go into the Compiz Windows Decoration settings and do one of the following (both have worked for me), go to the 'Command' field and type in either 

```
/usr/bin/compiz-decorator
```

and restart.

Or if you are still using Emerald type 

```
emerald --replace
```

and restart. Hopefully this will sort it as it did for me. Of course, you are going to have to make sure you have got Compiz running in the first place which if you follow Ami7878's suggestion should enable it.

Let us know if it works.

---

### Post by PCZahra on 2010-05-02
Both gave me the same result. However, when I went into the settings, each time it had changed back to ```
gtk-window-decorator --replace
```
and yet, when I click Reload Window Manager, everything appears the way it should. So I also tried Reload Window Manager after setting those two paths, and both times it disappeared, only to reappear when changed back to the gtk one.

---

### Post by PCZahra on 2010-05-02
hmm...
```
zahra@zahra-desktop:~$ compiz --replace
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
```
what do you make of this?

---

### Post by ptrinder64 on 2010-05-03
Doesn't sound too good, but after a cursory look over the bug report for the same thing ([https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/433488]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/433488")) it *sounds* pretty harmless (I am a novice though so will bow down to any greater knowledge on this).

According to the report some of the issues on GLX 1.3 were fixed in Karmic.

One more thing to try on the other compiz issue (i.e. it resetting back to glx), if you go to **Applications > System Tools > Configuration Editor**, and then click on **Apps > Metacity > General** is the 'compositing_manager' manager box ticked? If so unselect it and then try repeating the earlier steps.

---

### Post by PCZahra on 2010-05-03
It was on. I turned it off. No change. I've even installed Emerald, to see what happens. The Compiz icon now looks like this:

Settings Manager
Emerald Theme Manager*
Reload Window Manager
Select Window Manager
-> +Compiz
-> _Metacity
Compiz Options
-> _Loose binding
-> _Indirect Rendering
Select Window Decorator
-> +GTK Window Decorator
-> _Emerald*
Quit

(*newly added)

"gtk-window-decorator --replace" is still being set on login.
"emerald --replace" works as expected in terminal
"/usr/bin/compiz-decorator --replace" works in terminal, but says "Starting gtk-window-decorator" anyway.

Drivers are found, as the visual effects work just fine, once the window manager is started, but it still requires "Reload Window Manager" or "Select Window Manager->something" (or running from the terminal) or one of the visual effects settings changed before borders appear.

Without this step, changing "Select Window Decorator" does nothing, but afterwards it works as expected.

If running from the terminal I close the terminal window, border disappear and reload automatically.

I'm going to double-check everything now and then try a full reboot again.

---

### Post by PCZahra on 2010-05-03
What about log files? Are there any logs I could be looking at to find out what's happening? I put `compiz --replace` into startup applications to relieve the frustration for now, but I have a feeling it's going to come back and bite me again at some point.

---

### Post by _0R10N on 2010-05-03
I had the exactly same problem with compiz. The workaround that I chose is to add the following command as a startup application.
```
/usr/bin/compiz --replace
```
I never tried metacity, so you must replace compiz for metacity, in the previous command.
This should work for you!.

---

### Post by yhrn on 2010-05-04
> **PCZahra said:**
> It was on. I turned it off. No change. I've even installed Emerald, to see what happens. The Compiz icon now looks like this:

Settings Manager
Emerald Theme Manager*
Reload Window Manager
Select Window Manager
-> +Compiz
-> _Metacity
Compiz Options
-> _Loose binding
-> _Indirect Rendering
Select Window Decorator
-> +GTK Window Decorator
-> _Emerald*
Quit

(*newly added)

"gtk-window-decorator --replace" is still being set on login.
"emerald --replace" works as expected in terminal
"/usr/bin/compiz-decorator --replace" works in terminal, but says "Starting gtk-window-decorator" anyway.

Drivers are found, as the visual effects work just fine, once the window manager is started, but it still requires "Reload Window Manager" or "Select Window Manager->something" (or running from the terminal) or one of the visual effects settings changed before borders appear.

Without this step, changing "Select Window Decorator" does nothing, but afterwards it works as expected.

If running from the terminal I close the terminal window, border disappear and reload automatically.

I'm going to double-check everything now and then try a full reboot again.

Getting exactly the same behavior. Adding "compiz --reload" or "gtk-window-decorator --reload" as startup applications has no effect for me.  Did you find any solution?

---

### Post by PCZahra on 2010-05-05
no, just that workaround for now. I've given up. maybe a clean install will be more successful, but I can't be bothered.

---

### Post by rabideau on 2010-05-06
I would add my voice to those with this problem.

Any help is appreciated.  Hopefully we'll get a fix soon.

---

### Post by TheCat on 2010-05-06
I have the same problem.  Upgraded from Karmic to Lucid.  Not using metacity.

---

### Post by G_u_s on 2010-05-06
Same problem here, see: [http://ubuntuforums.org/showthread.php?t=1468647](http://ubuntuforums.org/showthread.php?t=1468647)

I'll try a few of the solutions in this thread but i'm pessimistic.

EDIT: as expected, nothing worked, and I'm still experiencing the same problems (described here and in my own thread).

---

### Post by rabideau on 2010-05-06
**_revised_:  after another update to Ubuntu... this hack stopped working for me.**-- however the command entered in terminal mode does the trick.  

The following hack seems to work for me.  I know it just masks the problem and is not a fix.  Hopefully we'll get a fix soon.

Here's my hack:

[LIST]
[*]Open System>>Preferences>>Startup Applications
[*]Select the ADD button to enter ADD Startup Application
[LIST]
[*]In the Name field enter a value that will sort to the end-- I use zzz-fix windows decoration
[*]In the command line enter:  /usr/bin/compiz --replace
[*]then save
[/LIST]
 
[/LIST]
Log out and log back in.  With any luck your system should have Windows decorations if you are running compiz with a metacity theme.

Be certain your theme is not using decprecated code!

...mark

---

### Post by rabideau on 2010-05-07
How many folks with this problem are running Avant Windows Navigator.  When I remove AWN from my auto start everything seems to work.  When I add it back windows decorations are missing.

Just a thought.

Maybe a smart person can figure out what we need to do if this is the problem.):P

---

### Post by yhrn on 2010-05-07
> **rabideau said:**
> **_revised_:  after another update to Ubuntu... this hack stopped working for me.**-- however the command entered in terminal mode does the trick.  

The following hack seems to work for me.  I know it just masks the problem and is not a fix.  Hopefully we'll get a fix soon.

Here's my hack:

[LIST]
[*]Open System>>Preferences>>Startup Applications
[*]Select the ADD button to enter ADD Startup Application
[LIST]
[*]In the Name field enter a value that will sort to the end-- I use zzz-fix windows decoration
[*]In the command line enter:  /usr/bin/compiz --replace
[*]then save
[/LIST]
 
[/LIST]
Log out and log back in.  With any luck your system should have Windows decorations if you are running compiz with a metacity theme.

Be certain your theme is not using decprecated code!

...mark
The weird thing is that this **started** to work for me after the latest update to Ubuntu (yesterday it had no effect). I'm using Compiz and the Ambiance theme on a system upgraded from Karmic (Hardy was the original installation version). And it doesn't seem to matter what I name the startup entry, as long as /usr/bin/compiz --replace is executed as a startup application I'm fine.
> **rabideau said:**
> How many folks with this problem are running Avant Windows Navigator.  When I remove AWN from my auto start everything seems to work.  When I add it back windows decorations are missing.

Just a thought.

Maybe a smart person can figure out what we need to do if this is the problem.):P
I'm not using AWN (never even installed it).

---

### Post by daboochmeister on 2010-05-08
Just another voice and experience ... I had to remove compiz (sudo aptitude remove compiz), and add /usr/bin/metacity --replace as a startup command.  That fixed it for me -- but of course, I have no compiz life-is-good-ness.

I also set the default Window Manager to metacity in gconf-edit, but I don't believe that had any effect.

I have an older machine, Dell GX270 with integrated Intel graphics that shares main memory -- maybe that's the root issue ...

---

### Post by mgmiller on 2010-05-08
If you are trying commands like metacity --replace in terminal, they will fail as soon as you close the terminal.

You need to hit alt/F2 to bring up the "Run Application" dialog and enter the command there.  That way it should "stick".

---

### Post by win2456 on 2010-05-12
Used to have emerald for the longest time but really like the new lift that ubuntu got.

After upgrading to Lucid, removed emerald:
```
sudo apt-get remove emerald* --purge
```

When I restarted, ran into the same trouble as everyone here.  The window decorations were gone.  Here is what fixed my problem and this survived after several reboots and hard shutdowns:

```
Menu -> System -> Preferences -> CompizConfig Settings Manager
```

Check the Windows Decorator, click on it and go down to the option that reads "Command".  Mine had:
```
emerald --replace
```
and I replaced it with:
```
gtk-window-decorator --replace
```

Viola! That worked for me.  Hope this helps you guys out.

FYI, I believe compizconfig settings manager can be installed if you don't find it in the menu:
```
sudo apt-get install compizconfig-settings-manager
```

Cheers!

---

### Post by G_u_s on 2010-05-12
Thank you for your help.

Unfortunately, I had already removed/purged emerald, and replaced the command as you described. It didn't help, problem still unsolved...

I'm surprised something of this importance doesn't receive more coverage (or maybe I don't know how to browse bug reports).

---

### Post by mgmiller on 2010-05-12
I just looked at mine.  After my upgrade to 10.04, I also had no windows decorations, but when I looked at System > Preferences > Appearance > Visual Effects, it had been set to "None".  When I checked "Normal", it checked my video drivers and installed the nvidia driver which for some reason was not upgraded along with the rest of the system.  Problem solved.

When I looked in the CCSM as per the post above, I see that the window decoration command is different.  Mine reads:

```
/usr/bin/compiz-decorator
```You might want to try it that way.

You may have to toggle the "Enable Window Decoration" check box after you change the command to make the new command work.

---

### Post by iposner on 2010-05-13
I'm running a fresh install of 10.04 - and I've still got the problem. Initially after login, I can see the Window borders, but within a few seconds of use, all the borders disappear.

Note this computer uses an integrated intel video chipset.

Running metacity --replace restores the borders.

We should not have to hack our installations to get such basic functionality working. If such a problem occurred on Windows, Microsoft would get cained.

Until quality control is improved, Ubuntu will remain the choice of enthusiasts only.

---

### Post by mgmiller on 2010-05-13
> I'm running a fresh install of 10.04 - and I've still got the problem.  Initially after login, I can see the Window borders, but within a few  seconds of use, all the borders disappear.

Note this computer uses an integrated intel video chipset.

Running metacity --replace restores the borders.

Intel chipsets (you didn't mention which one you have) normally work extremely well since 9.10.  By running the command, metacity --replace, you are changing the window border effects to "none" for this session only.  Somewhere, the system is still trying to do something else.  The effect you are describing happens when the video chipset is not capable of compiz for some reason, but is trying to run it anyway.

Try looking at System > Preferences > Appearance and on the Effects tab, make sure "None" is selected.

Failing that, go to System > Preferences > Startup Applications and Click the Add button and place your metacity --replace command in there, that way it should execute on every startup.

Obviously, these steps disable compiz, but you don't seem to be upset about that.

The only other thing I can think of right now is to enter the command:
```
metacity --replace
```
in the run dialog box you get when hitting Alt.+F2, rather then in a terminal.  Commands issued in the run dialog box are more persistent then those issued from a terminal, as when you close a terminal, you also end the process started from it.

Finally, you should report this as a bug.  As I said at the beginning of this post, Intel graphics chipsets work incredibly well now.  I Have a Lenovo T400 notebook with intel graphics that was an absolute joy with 9.10 and has gotten even better after upgrading to 10.04.

---

### Post by strangeusername on 2010-05-17
Same problem here. When I log-in, I don't have any window-decorator. I need to go to Preferences\Appearance\Visual Effects and enable from there.

After trying everything suggested here, I eventually managed to fix this. I'll describe how I got there in the hope that it helps people troubleshoot. It might not be the cleanest way of doing it but it works for me!

Once logged-in, don't enable the window decorator yet, and open a terminal. Type this:

ps -ef | awk '{print $7}' | sort > ~/before.txt

This will print a list of running processes, sort it and write it to a file in your home directory.

Enable your window decorator. Then run following.

ps -ef | awk '{print $7}' | sort > ~/after.txt
cd ~/
diff -wby before.txt after.txt > difference.txt
cat difference.txt

Amongst others, mine had /usr/bin/compiz.real and /usr/bin/gtk-window-decorator.

Logout and log back in again

open a terminal and run
nohup /usr/bin/compiz.real &

The nohup ensures that the process isn't attached to the terminal. So if you close the terminal, the process continues running.

Do you get your window decorations back? I did!!!

So I added /usr/bin/compiz.real to my start-up apps in Preferences\Startup Applications

That's it. Hoped it helps and even if it doesn't, these commands might give you some background on what process is required to resolve the problem.

---

### Post by SnappyU on 2010-05-19
[QUOTE=PCZahra] In fact, whenever I open the terminal, I need to have two tabs open in order to use it, and when I close it all the borders go away again (even when I haven't done anything).[/QUOTE]

when you call "metacity --replace" in the terminal, you may want to put an ampersand behind so that it runs in a separate process and not within the terminal.  "metacity --replace &"

Just in case ... :)

---

### Post by ktechman on 2010-05-20
Here is how I (Solved) my issue with window decorations disappearing:

First I went to System > Preferences > Startup Applications > Add then typed 'compiz --replace' Add then Add 'emerald --replace' Add then I named them both with a Z.... (Don't know if it made a difference) then restarted  several times enabled all of the plug-ins I love cube 3d windows etc etc... and restarted more several times and I get window decorations every time and no regression with "Desktop Effects" (losing everything before) I only had to do this on one desktop with similar video cards both Nvidia. 

Ktechman

---

### Post by quantumboy85 on 2010-05-22
I'm observing the same problem. I installed 10.04 last night and I can't get Compiz to run, here's what I get when I try

```

joseph@amethyst:~$ compiz --replace
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
Couldn't find a perfect decorator match; trying all decorators
Found no decorator to start
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
joseph@amethyst:~$ Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x5601fa7 (joseph@ame)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

```

Compiz worked flawlessly on 9.10. Furthermore, whenever I login, I don't have any window decorators, I've got to change, or attempt to change window managers to get decorators. So I've added "metacity --replace" to my Startup Applications.

Compiz has never worked, Metacity worked a bit and then window decorators stopped showing up. I installed a few programs, a couple of KDE applications...not sure if that has any effect.

I've got an Eee PC 1005HAB, here's my video information

```

joseph@amethyst:~$ lshw -C video
WARNING: you should run this program as super-user.
  *-display:0             
       description: VGA compatible controller
       product: Mobile 945GME Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:f7e00000-f7e7ffff ioport:dc00(size=8) memory:d0000000-dfffffff(prefetchable) memory:f7dc0000-f7dfffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f7e80000-f7efffff


```

---

### Post by Maju on 2010-06-05
> **mgmiller said:**
> If you are trying commands like metacity --replace in terminal, they will fail as soon as you close the terminal.

You need to hit alt/F2 to bring up the "Run Application" dialog and enter the command there.  That way it should "stick".

Great! Seems that it solves my problems. Compiz's out, Metacity is in! Thanks. :guitar:

---

### Post by faflu on 2010-06-07
For me putting ```
compiz --replace
``` into autostart programs did the job. But I think it shouldn't be like that. I'm using Nvidia driver and Ubuntu 10.04.

---

### Post by drascus on 2010-06-18
faflu: yup confirmed that totally works. I don't really care wether or not it's right just that it works. thanks! Hopefully this has just been broken by an update and a later one will fix it. please people keep posting especially if someone finds a better solution.

---

### Post by captain_conrad on 2010-06-18
> **andrea000 said:**
> This sounds like one of the compiz bugs open ccsm go to
the workarounds plug in and put a check in the legacy
full screen support and reboot this fixed mine and should
yours to.



> **BillyG123 said:**
> Here's what worked for me:

1. compiz --replace
2. System > Preferences > Startup Applications > Options > Remember Currently Running Application


I don´t know which one of these is the one that actually made it work, but I did both and then restarted, and **PROBLEM SOLVED!!!**

:mrgreen: \\:D/   WOOHOO!!! THANK YOU!!! \\:D/ :mrgreen:

(I did try some suggested things that dit not work for me ,they might work for you, [_here´s_]("http://ubuntuforums.org/showthread.php?t=1499117") the link to my thread)

):P

---

### Post by Blacksheep01 on 2010-09-04
> **ktechman said:**
> Here is how I (Solved) my issue with window decorations disappearing:

First I went to System > Preferences > Startup Applications > Add then typed 'compiz --replace' Add then Add 'emerald --replace' Add then I named them both with a Z.... (Don't know if it made a difference) then restarted  several times enabled all of the plug-ins I love cube 3d windows etc etc... and restarted more several times and I get window decorations every time and no regression with "Desktop Effects" (losing everything before) I only had to do this on one desktop with similar video cards both Nvidia. 

Ktechman

Thanks, looks like this tip solved my periodic problem of the menus disappearing!

---

### Post by borth92 on 2010-09-04
add fusion-icon to the startup applications...when it starts it restarts compiz which causes the borders to appear

---

### Post by gbestrada on 2010-09-05
on the control center verify if you have installed **ARANDR **if so that might be causing the problem

---

### Post by ivanz on 2010-09-29
I has this problem recently, after installing 10.04 and then importing compiz profile from my old pc (Ubuntu 9.10) - looks like old profile is not compatible with new compiz, especially it seems that way how compiz-decorator is started has changed.  I've solved it, here are few notes, that might help:
Windows decoration are managed by compiz-decorator process, which is started by compiz itself.
If you have problems, not seeing windows decorations (eg. title, buttons, border) check:
ps -ef|grep compiz - you should see two processes - compiz and compiz-decorator.
If compiz-decorator is not running, try to start it from terminal.  If then decorations appear, the problem is that compiz does not start compiz decorator automaticaly.
If you mangled with compiz settings, try to restore then to default in CCSM (CompizConfig Settings Manager) set profile to Default (in Preferences), if this will not help  try to click Reset to Default.  If still problems persists, check the Window Decoration Plugin (In Effects category) - Command field has to be /usr/bin/compiz-decorator.
If nothing above help, you can still add compiz-decorator to gnome start apps, the effect in end is the same.

---

