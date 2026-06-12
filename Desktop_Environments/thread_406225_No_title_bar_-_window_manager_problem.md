---
title: "No title bar - window manager problem"
date: 2007-04-10
forum: Desktop Environments
---

### Post by rudlavibizon on 2007-04-10
I have a strange problem: when i login to my default session there are no title bars on windows, i cannot resize them and there are no multiple desktops. However when I login with failsafe gnome everything is fine. How do i make a new default session from failsafe or fix the existing one? :confused: 

PS. This happened after todays feisty updates and I don't remember changing anything my self (although i didn't restart my computer for 2-3 days and could have forgotten). I checked history in synaptic and there were gnome and metacity updates.

---

### Post by mac.ryan on 2007-04-10
I'm still on Edgy and moreover I am using Beryl, yet my impression is that you might miss the window decorator.

What does it happen if you start your window decorator manually?
(If I am not mistaken, the command could be)

```
gnome-window-decorator
```

...but I am going by pure memory, so I could be wrong on it...

---

### Post by rudlavibizon on 2007-04-10
No, nothing happens.

---

### Post by rudlavibizon on 2007-04-10
Also when i try to open preferences>windows  i get this


"Cannot start the preferences application for your window manager

Window manager "unknown" has not registered a configuration tool"

---

### Post by rudlavibizon on 2007-04-10
Sorry for bumping this tread, but i'm posting this as i try to fix this. I just typed metacity in terminal and got it to work (titlebars are back) and i get this: 

```
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
```

---

### Post by josephus on 2007-04-10
it sounds like your window manager is not being loaded up.  from a terminal try loading up metacity and see what happens.

---

### Post by rudlavibizon on 2007-04-10
Just did that check the previous post.

---

### Post by josephus on 2007-04-10
are you running other window managers besides metacity?

---

### Post by rudlavibizon on 2007-04-10
I have murrine installed, but i'm not sure that's a window manager. 8-[

---

### Post by josephus on 2007-04-10
no. i was thinking on the lines of beryl or compiz  -- i'm not sure if it makes any difference.

maybe you can check your xsession log to see what errors are popping up.

---

### Post by josephus on 2007-04-10
in ~/.gnome or ~/.gnome2 i think there is a session file.  rename it to session.old and logout and login again.

without that file, the session defaults to the default session.  since you said that your failsafe session works then i think this will solve your problem.

---

### Post by rudlavibizon on 2007-04-10
I have compiz installed, i think it comes by default in feisty. But i think it's not turned on since i have an ATI card. I'll try renaming that file.

---

### Post by rudlavibizon on 2007-04-10
Thanks that worked (renaming that file). :)

---

### Post by gremeth on 2007-04-14
If you have an NVIDIA card, you will need to add a line to your xorg.conf.  Check [here]("http://forum.beryl-project.org/viewtopic.php?f=35&t=1631") for more in-depth instructions.

You might also want to make sure you have the beryl-manager package installed.  It runs in the system tray of kde/gnome/etc and allows you to choose window decorator and window manager.  Good luck!

---

### Post by dmcmahonpo3 on 2007-04-14
Hi

Had a similar problem, didn't need beryl to fix it, renaming session file did not fix, so I did this:

1) In the broken gnome session, used terminal to start metacity so I could actually do things.

2) Manually configured the session manager to launch metacity when I start a gnome session as follows:

System -> preferences -> sessions -> startup programs -> new 

navigate to and select /usr/bin/metacity

click "ok" and close it

This may not be the "best" fix, and it will be a pain if I have to apply it to other people's sessions too, but it seems to have done the trick.

Denis

---

### Post by joeashcraft on 2007-04-15
I had this problem after I installed Beryl (I'm running Edgy).
All I had to do to fix it was right click the red diamond and select "Reload Window Decorator".

---

### Post by Bruegger on 2007-04-15
Josephus...u r the man!!!....been struggling with this problem in my dapper install since the past week.

renaming the session  file solved the prob for me.

thanks a ton!!

cheers!

---

### Post by jonom on 2007-04-19
Worked for me too Josephus - thanks!

---

### Post by cmonspike on 2007-04-20
> **gremeth said:**
> If you have an NVIDIA card, you will need to add a line to your xorg.conf.  Check [here]("http://forum.beryl-project.org/viewtopic.php?f=35&t=1631") for more in-depth instructions.

You might also want to make sure you have the beryl-manager package installed.  It runs in the system tray of kde/gnome/etc and allows you to choose window decorator and window manager.  Good luck!

After upgrading from edgy 6.10 to Feisty 7.04 I was faced with this problem and this proved to be the solution. Starting metacity worked only temporarily whereas this is a permanent fix. Needless to say, the upgrade completely destroyed my xorg.conf and I had to redo it from scratch only to be faced with this problem. Now all is well. Thanks to everyone for their help. !

---

### Post by laurens on 2007-04-21
I had the same problem but a totally different solution. Turns out, that my decoration plugin was disabled.

Yeah, I know it sounds stupid. I fired up gset-compiz, and there was no check before 'decoration'. Checking that solved my problem. Weird, I know, probably not caused by my recent upgrade to feisty, but you never know.

---

### Post by endfx on 2007-04-23
Ok, so after doing all of the above, nothing seemed to solve my problem. Basically all the effects worked but I had no window borders or title bars.

This is how I fixed it:

To fix compiz:
sudo apt-get install gnome-compiz-manager

then from the command line run:
compiz-tray-icon

Now you'll get a compiz icon in your tray (by the clock). If your problem isn't fixed yet, then right click the compiz icon and uncheck the "GL desktop"  and then check it again.


To fix beryl:
sudo apt-get install beryl-manager

then from the command line run:
beryl-manager

Now you'll have a red diamond looking icon in your tray (by the clock). If your problem isn't fixed yet, then
right click and select "reload window manager"



I should mention that the nvidia card post from the above did help out and made the effects work better.

Now to make these changes permanent, goto System -> sessions -> startup and add either beryl-manager or compiz-tray-icon.

I guess for some of us, when beryl and/or compiz was installed, the respective manager wasn't installed by default.

Hope this helps someone.

---

### Post by wsandner on 2007-04-23
Deleting the .gnome2/session did not work for me.  Neither did installing gnome-compiz-manager.  However, I found that my ~/.gnomerc file had an unwanted line: 

WINDOW_MANAGER=~/.gnome-compiz-manager/openbox.  

See: [https://bugs.launchpad.net/ubuntu/+source/gnome-compiz-manager/+bug/103246](https://bugs.launchpad.net/ubuntu/+source/gnome-compiz-manager/+bug/103246)) for details.

I deleted my ~/.gnomerc file per suggestion on the launchpad bug report and fixed my window manager troubles.

---

### Post by boteeka on 2007-04-23
Indeed that was the problem.

I had this issue too, since I upgraded from Edgy using apt-get. First I tought that something is blocking beryl-manager to start, so I tryed to disable autostarting things in the session manager with no luck. I had beryl installed in Edgy too, and it worked flawlessly. Back then I started it with the session mager, starting beryl-manager. After the upgrade I wouldn't start just after a couple of minutes. But if I started it manually from a terminal it stared instantly.

After all of that hassle, with your solution it is quite logical why it didn't started.

Now it starts instantly, for a second the basic metacity window decorator than suddenly it switches over to emerald.

Thanks for your help! :)

---

### Post by rpercy on 2007-04-24
> **wsandner said:**
> 
See: [https://bugs.launchpad.net/ubuntu/+source/gnome-compiz-manager/+bug/103246](https://bugs.launchpad.net/ubuntu/+source/gnome-compiz-manager/+bug/103246)) for details.

I deleted my ~/.gnomerc file per suggestion on the launchpad bug report and fixed my window manager troubles.

Sweet.  That worked for my Feisty / ATI setup too.

---

### Post by c@rc@ss on 2007-04-27
This is how I fixed it.

System-->Preferences-->Desktop Effects

Click on Enable effects.

Wait
crl-alt-BkSp

I think that it is a bug that when you click on enable effects it actually disables it.

---

### Post by Underfire on 2007-04-29
I'm new to Linux & Ubuntu was my first choice after reading about many options.  I ran Edgy Eft/Beryl for about a month and recently upgraded to Feisty.  I, too, am having trouble with Beryl and windows management.  If I manage windows with Metacity I have no problem.  If I switch it to Compiz I have a drop shadow and a completely transparent, but functioning title bar.  If I switch to Beryl the windows I have open flash repeatedly for 5 seconds and then quit leaving me with no title bar at all.  Also, none of the animation effects work at all.  I'm willing to post whatever it takes to make this work.  It's driving me nuts.  Thanks in advance for any help.  I have done everything mentioned by this forum, excluding the ~/.gnomerc fix because I can't find that file at all.

---

### Post by josephus on 2007-04-29
gnomerc  is  configuration file that runs at the beginning of a gnome session, and for some people it was telling the session to run compiz when they didn't want to.  this has nothing to do with your problem.

> If I switch it to Compiz I have a drop shadow and a completely transparent, but functioning title bar

Have you tried using the compiz-tray-icon to change the preferences.  There is an option to change the transparency of the title bar and can be made to be completely transparent.
> 
If I switch to Beryl the windows I have open flash repeatedly for 5 seconds and then quit leaving me with no title bar at all. Also, none of the animation effects work at all. I'm willing to post whatever it takes to make this work.

Try loading up the beryl-manager and use that to try to reload/change the window decorator.  As well go into the preferences and see if which animations are loaded up.

---

### Post by Blaxter on 2007-04-29
> **wsandner said:**
> Deleting the .gnome2/session did not work for me.  Neither did installing gnome-compiz-manager.  However, I found that my ~/.gnomerc file had an unwanted line: 

WINDOW_MANAGER=~/.gnome-compiz-manager/openbox.  

See: [https://bugs.launchpad.net/ubuntu/+source/gnome-compiz-manager/+bug/103246](https://bugs.launchpad.net/ubuntu/+source/gnome-compiz-manager/+bug/103246)) for details.

I deleted my ~/.gnomerc file per suggestion on the launchpad bug report and fixed my window manager troubles.

thanks a lot, works for me!, u're my hero :D

---

### Post by blazko on 2007-04-29
Dear all,

Adding thexorg.conf worked for my nVidia - now I have window decorations and shadowed menues!
However, I face another issue: I have two screens on dedicated graphic cards:

- nVidia 6200 as primary card (shows boot), in X used as secondary screen
- nVidia 6600 LE as secondary card, in X used as main display

I combined both display in one X serverlayout section. When using desktop effects however, my secondary screen keeps blank - I can only see the mouse pointer when moving it to that screen.

Also, switching to another workspace causes a blank window on the main screen (wallpaper keeps but icons disappear and sometimes panel crashes).

Has someone similar experiences? Btw. I am using Xinerama. Btw2: switching display devices is not an option because I use that computer as a Video Disk Recorder (VDR).


Thanks and regards,
Timo

---

### Post by Underfire on 2007-04-30
Thanks for the help josephus, but those didn't work.  I tried running beryl with the terminal open and got this response...

** (beryl-manager:6293): CRITICAL **: can't execute beryl-xgl: Success
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Log level 32: could not find XKB extension.

---

### Post by josephus on 2007-04-30
underfire: what graphics card and driver are you using?

---

### Post by Underfire on 2007-05-01
I'm using a GeForce 6800 128MB and I'm also using the latest nvidia drivers (version 1.0-9755, I believe).

---

### Post by mayamaniac on 2007-05-01
I tried most of the suggestions here on this thread, and nothing seem to make the title bad to appear. What is the problem exactly and why isn't it working in feisty?

And where's the ~/.gnome session file that everyone's talking about? I can't find it.

---

### Post by josephus on 2007-05-01
underfire:  looks like you are trying to run beryl with xgl.  

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

---

### Post by josephus on 2007-05-01
mayamaniac:   which window manager are you running/trying to run?

---

### Post by mayamaniac on 2007-05-01
> **josephus said:**
> mayamaniac:   which window manager are you running/trying to run?
its compiz I think or whatever that came with feisty when you enable Desktop effects.

---

### Post by josephus on 2007-05-01
if you run compiz from terminal what message do you get?

---

### Post by mayamaniac on 2007-05-01
> **josephus said:**
> if you run compiz from terminal what message do you get?
I get this:
> 
mayamaniac@feisty:~$ compiz --replace
/usr/bin/compiz.real: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
inotify_add_watch: No such file or directory

---

### Post by josephus on 2007-05-01
i saw this post with a guy with the same error message (post 15/16)

[http://ubuntuforums.org/showthread.php?p=2534936](http://ubuntuforums.org/showthread.php?p=2534936)

see if his solution helps.

---

### Post by mayamaniac on 2007-05-01
> **josephus said:**
> i saw this post with a guy with the same error message (post 15/16)

[http://ubuntuforums.org/showthread.php?p=2534936](http://ubuntuforums.org/showthread.php?p=2534936)

see if his solution helps.
SUCCESS! :) The title bar is back.

I set the color depth to 24 bit in xorg.conf and compiz works now. Thanks Josephus!:KS

---

### Post by Underfire on 2007-05-01
Once again you save the day josephus!  Downgrading the version of beryl worked.  I guess that's the stable version Feisty should have come with.  Thank you for your help and patience!

---

### Post by Southeast First on 2007-08-27
I hate to bump an old thread but I'd rather do that than post a new one. I recently downloaded the latest Gutsy upgrade which caused my X to screw up, then fixed it by removing xserver-xorg-video-ati. Then when I logged back in I had this problem. Running metacity in the terminal brought them back, but I receive the following error despite everything seeming fine:

Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2800003 (Update Man)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2800003 (Update Man)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

---

### Post by Raklau on 2007-09-10
I'm havening the same problem as most of you that have posted, I'm running Ubuntu 7.04 32bit version cause I couldn't get the 64 bit version to install.
My system: Dell Dimension AMD 64 bit with Nvidia 6000 on board running dual boot with Win XP.

At any rate I have the latest versions of beryl, emerald and compiz, the problem I'm running in to is if I run beryl with emerald as the window decorator I have no title bar's making me have to switch to GTK.

If I run Compiz with emerald I have no cube effects but emerald works just fine .

What I would like is to be able to run Beryl and Emerald with no issues.

Also when I start up after shutting my pc down I have no wallpaper lol.

I've been messing with Linux  for all of 3 day's but I have to say even with the small problems I've run in to such as above I'm enjoying Linux and if I can figure out how to get my pc games to work in Ubuntu I'll be ditching winblows all together.:lolflag:

---

### Post by alejaaandro on 2008-02-04
> **josephus said:**
> in ~/.gnome or ~/.gnome2 i think there is a session file.  rename it to session.old and logout and login again..

thanks alot

---

### Post by alejaaandro on 2008-02-18
i'm coming back to this, since i haven't found a permanent solution.. 

it's strange but I don't seem to get the problem every time i start my computer... renaming the session file works every time, but it's really stupid having to rename-logout-login whenever i have the problem..i tried all the other solutions (the missing code for nvidia etc) but nothing seems to work.. i erased the session file and it worked flawlessly for 3-4 days. Then i got the problem again.. 

today, i tried running compiz on a terminal (i guess that reboots compiz, right?) and it fixes the problem but again it's not permanent.. i could make it run on startup, but isn't it supposed to run anyway? any ideas why it might not start correctly in the first place?

i m a neewbie and i m trying to work my way to it, but i dont like just covering up the problems.. i prefer knowing whats the deal and fixing it, so, i would appreciate any help...

(ubuntu 7.10)



edit: i tried gtk-window-decorator& an works better than running compiz, since it doesnt need to restart the desktop, it only enables the decorator... any ideas why that isnt done in the first place?

---

