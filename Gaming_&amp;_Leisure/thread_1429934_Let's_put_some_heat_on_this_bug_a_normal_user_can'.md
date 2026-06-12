---
title: "Let's put some heat on this bug: a normal user can't escape frozen full-screen apps"
date: 2010-03-14
forum: Gaming &amp; Leisure
---

### Post by gabba on 2010-03-14
**People, I won't say it again: [read this bug description]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/537137") *before* making any suggestions. And let's take a proactive attitude, otherwise this'll never get fixed.**

Recently I had Battle for Wesnoth freeze when I press the quit button. It's apparently related to [this bug](https://gna.org/bugs/?func=detailitem&item_id=15115), since it went away by installing libsdl1.2debian-pulseaudio. (Damn pulseaudio, forcing everybody to use it directly instead of adapting to every existing system like it was supposed to do.)

Anyways, before finding the fix, I was able to kill the app by using Ctrl-Alt-F1 to get a console, and killall -9 wesnoth to exit the frozen game. However it set me thinking: what's a non-technical user supposed to do in this situation? He/she won't know what to do (obvious stuff like alt-tab doesn't work) and will reboot and lose data or his/her OS.
Putting myself in the shoes of Average Joe who succumbed to the overdone PR on the [http://www.ubuntu.com/](http://www.ubuntu.com/) front page, I felt betrayed. Where's the disclaimer on their front page saying "warning, this is a highly experimental distro containing unstable packages and experimental systems (*cough* pulseaudio, compiz). You might need to reboot your system [or kill your X server] at any time, therefore exercise extreme caution and save and backup your data."

And this is just one example, but over the years I've had countless other fullscreen apps (mainly 3D ones) freeze on me, on Ubuntu or other distros, and I've always had to kill them in this gurus-only method.

Therefore I opened the following bug. I'm asking them to provide some key combination (or whatever workaround) that works at least as well as Alt-tab in windows that allows you to escape frozen full-screen apps.
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/537137](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/537137)
**Please go there, make a launchpad account if needed, and subscribe to the bug and click the "Does this bug affect you?" link**. And help me prevent them to pass it off as a duplicate of a vaguely related bug, or change the package to something that'll get ignored, like fglrx-installer (i.e. "Oh, it's ATI's fault! We can't do anything about it!").

Edit: For Ubuntu 9.10 Karmic users: If you can, include other examples of freezing full-screen apps in your bug comments (we need a variety of causes so they don't write it off as a specific bug), and add your hardware info to the bug with:
```
apport-collect -p your_package 537137
```
If you don't know what package to relate it to just go with:
```
apport-collect -p xorg 537137
```

Edit2: Another thing you can do to help out is to publicize this thread and the bug on other forums you frequent. The more people subscribe to this bug, click "it affects me too" and comment in it, the more its heat rating will increase. We can actually make it impossible to ignore.

---

### Post by DoktorSeven on 2010-03-14
Less of a bug than a needed feature; I say promote it in Brainstorm:
[[IMG]http://brainstorm.ubuntu.com/idea/9670/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/9670/)

---

### Post by gabba on 2010-03-14
Actually I think there are two parts to this problem:
- Regarding frozen apps, it's a serious usability and reliability issue with Ubuntu, which can make users lose data or their OS. (Plus Windows has had a solution to this since forever.) I call that a bug.

- Regarding properly working full-screen apps, it's still annoying not to be able to alt-tab out of them. So from this point of view it's a feature, which doesn't invalidate my first point. Does the fact that the idea [already exists on Brainstorm]("http://brainstorm.ubuntu.com/idea/2205/"), that it gets completely ignored despite the votes and that it gets the abusive "duplicate" treatment have anything to do to my willingness to focus on the bug aspect of this? Maybe.

--
More or less off-topic note:
I noticed that Ubuntu is much more sensitive to sudden rebooting than Windows. Windows usually recovers, I have to do a reinstall for that reason about once a year among the whole pool of computers I maintain (and I do Windows and Ubuntu free tech support for 10-20 friends). Ubuntu on the other hand can get borked rather easily by this, which makes the above bug only worse.

---

### Post by Rasa1111 on 2010-03-14
edit: oops, sorry,  Didnt realize this was in the "gaming" forum. 
 I never play video games on my system, but I think it should still work... 

could one not use the "magic keys"? 

 e.g.~  Alt+ SysRq (prntscreen) REISUB~

 One presses and holds Alt and SysRq keys, while pressing R, then E, then I, then S, then U, then B~   and Once you hit the B button, your system will reboot, safely. 

> 
Hold down ALT+PRINT and type slowly REISUB to restart your system. Hold down ALT+PRINT and type REISUO to turn it off.
 A short note on what REISUB or REISUO does:
 
[LIST=1]
[*]**R** &#8211; Switches the keyboard from raw to XLATE mode (detatching from the X-Server)
[*]**E** &#8211; Sending a SIGTERM to all processes except INIT
[*]**I** &#8211; Sending a SIGKILL to all processes except INIT (and that&#8217;s why to type REISUB slowly)
[*]**S** &#8211; Syncs all data in the cache to mounted partitions
[*]**U** &#8211; Unmounts all mounted partitions and remounts them read-only
[*]**B** &#8211; Reboot the system immediately without unmounting or syncing mounted partitions
**or**
**O** &#8211; Shut down the system immediately without unmounting or syncing mounted partitions
[/LIST]
 [http://www.matejunkie.com/magic-sysrq-reisub/](http://www.matejunkie.com/magic-sysrq-reisub/)

Sorry if you were already aware of this. 

 I just learned of it a couple weeks ago and it has saved me a few times. :)
works beautifully to. 

good luck.

---

### Post by gabba on 2010-03-14
> **Rasa1111 said:**
> edit: oops, sorry,  Didnt realize this was in the "gaming" forum. 
 I never play video games on my system, but I think it should still work... 

could one not use the "magic keys"? 

 e.g.~  Alt+ SysRq (prntscreen) REISUB~

 One presses and holds Alt and SysRq keys, while pressing R, then E, then I, then S, then U, then B~   and Once you hit the B button, your system will reboot, safely. 

[http://www.matejunkie.com/magic-sysrq-reisub/](http://www.matejunkie.com/magic-sysrq-reisub/)

Sorry if you were already aware of this. 

 I just learned of it a couple weeks ago and it has saved me a few times. :)
works beautifully to. 

good luck.

I appreciate your trying to contribute to this thread, but if you had read the **bug description I linked to in the OP**, you'd know I already mentioned this.:roll:

Summary: those keys avoid destroying your OS, but not killing all open apps and losing all unsaved data. And those keys are a bit too dangerous to publicize to newbs.

---

### Post by portets on 2010-03-14
yeah, but that's a lot to remember for a newcomer.

we need a key combo that doesn't reboot. a way that will take us back to the desktop and open "System Monitor" so we can safely kill the app manually. or a key combo that will kill the current application in focus.

or at least make ubuntu come with kde's default key combo that restarts the x server without restarting your system. (ctrl+alt+backspace).

wait, if you set system monitor to ctrl+esc, does it take you to the desktop and open system monitor?

---

### Post by hikaricore on 2010-03-14
> **portets said:**
> yeah, but that's a lot to remember for a newcomer.

we need a key combo that doesn't reboot. a way that will take us back to the desktop and open "System Monitor" so we can safely kill the app manually. or a key combo that will kill the current application in focus.

or at least make ubuntu come with kde's default key combo that restarts the x server without restarting your system. (ctrl+alt+backspace).

wait, if you set system monitor to ctrl+esc, does it take you to the desktop and open system monitor?

Ctrl+alt+backspace was the defacto standard kdm/gdm restart for ages..
However...they (Ubuntu) actually disabled it a little over a year ago because people were "accidentally" hitting it.
Mind you there's little proof that these people actually existed, but it got pushed through anyway.

---

### Post by bruno9779 on 2010-03-14
It is a bug. And a hell of a bug. It has been bugging me since my first linux install.

eg.: I have just purchased my first linux game ever, On the rain slick precipice of darkness ep1 last week.
The game is great, but if I leave it till the screensaver kicks in, it freezes, and ctrl+alt+F1 does not work.
In another app, ctrl+F1 and alt+F1 where mapped out by the app, so no luck here either

 Alt+ SysRq (prntscreen) REISUB~ is possible only with English keyboards (probably some other but not many) I have a spanish and a portuguese keyboard at home, and to do that key combination i need 3 hands.
Not a solution but a very lame workaround....

---

### Post by gabba on 2010-03-14
> **portets said:**
> or at least make ubuntu come with kde's default key combo that restarts the x server without restarting your system. (ctrl+alt+backspace).

Why can't people read the bug description I linked to???
Anyways ctrl-alt-backspace is now alt-sysrq-k.

> **DoktorSeven said:**
> Less of a bug than a needed feature; I say promote it in Brainstorm:
[[IMG]http://brainstorm.ubuntu.com/idea/9670/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/9670/)

I did vote for the brainstorm idea you linked to, however look at the stupid answer [this related idea]("http://brainstorm.ubuntu.com/idea/2205/") got, just because it got presented as a "would be nice" feature instead of focusing on the reliability aspect vs freezing apps. See the number of votes on that idea? That's right, 643 votes.

---

### Post by bruno9779 on 2010-03-14
That is an hardcore-stupid answer...

Sorry for the sarcasm, but that dev sounded like he worked for MS till last week. Only when holding a monopoly you can refuse to give basic portability, and pretend that everyone adapts to the way a Desktop environment is.

If more commercial apps are to be available for linux, there must be some kind of effort on our side.

---

### Post by Rasa1111 on 2010-03-14
> **gabba said:**
> I appreciate your trying to contribute to this thread, but if you had read the **bug description I linked to in the OP**, you'd know I already mentioned this.:roll:

Summary: those keys avoid destroying your OS, but not killing all open apps and losing all unsaved data. And those keys are a bit too dangerous to publicize to newbs.

 sorry. :-s

---

### Post by leandromartinez98 on 2010-03-14
I agree. I think Control-Alt-Delete should bring up the task manager. My mother had once rebooted her laptop because firefox was irresponsive. It was not even a full-screen halt, but she had no clue on how to kill it and, of course, she wanted to continue using the web... An easy combination to bring up the GUI to kill irresponsive applications is important.

---

### Post by Bios Element on 2010-03-15
> **hikaricore said:**
> Ctrl+alt+backspace was the defacto standard kdm/gdm restart for ages..
However...they (Ubuntu) actually disabled it a little over a year ago because people were "accidentally" hitting it.
Mind you there's little proof that these people actually existed, but it got pushed through anyway.

"they" = upstream with the x folks last I heard. Not ubuntu, ubuntu simply inherited the "usability improvement" the x folks dictated.

---

### Post by hikaricore on 2010-03-15
I was given the impression at the time that it was a Ubunut specific decision.
Granted this was awhile back and I've not really paid much attention to the issue since.  :p

---

### Post by MaximB on 2010-03-15
I think this major "bug" is not Ubuntu specific and should be handled from the core (the kernel perhaps).
I remember when I had ATI video card some games used to hung a lot, and I couldn't even restart the X server or go to shell, obviously in this case even a key combination that "should" bring the system monitor won't work, as the keyboard is not responding.

The problem is more deep then just a key combo.

Now that I use Nvidia I also sometimes have hangs, but I am able to go to shell and kill the program, but then again - it's a bad solution for the newbies who doesn't know the cli commands.

This "bug" needed a solution years ago, but I'm not sure the Ubuntu team should handle this (maybe Linus ?).

---

### Post by hikaricore on 2010-03-15
In an ideal world, no OS should ever ever hardlock but you'd be hardpressed to find a single one out there that doesn't do this under one condition or another.

---

### Post by caravel on 2010-03-15
> **hikaricore said:**
> Ctrl+alt+backspace was the defacto standard kdm/gdm restart for ages..
However...**they (Ubuntu) actually disabled it** a little over a year ago because people were "accidentally" hitting it.
Mind you there's little proof that these people actually existed, but it got pushed through anyway.
It was actually xorg that disabled it, not Ubuntu/Canonical.  You can also re-enable it again quite easily.

---

### Post by cbecker78 on 2010-03-15
I am a very new linux/ubuntu user, and have had this issue on several occasions playing Ultima in Exult (full screen).  After pushing every key combo I could think of to try and kill the process, I resolved to just hard reboot.  this seems to occur viewing flickr imagages in firefox fullscreen too, when multiple pictures are open in multiple tabs.  As a result of my multiple reboots over the last two months (I know, I should have learned my lesson), I apparently fried my HD, and finally gave in and bought a new pc.  I'm still sticking with ubuntu for now, but would very much like to see this resolved as I am just avoiding full screen applications right now out of general fear for the brand new computer.

---

### Post by del_diablo on 2010-03-15
Better solution: Force x server to NOT be able to "lock the screen" under any circumstances.
This would mean that we could in 100% of any cases be able to alt-tab and do whatever we want.

---

### Post by hikaricore on 2010-03-15
> **del_diablo said:**
> Better solution: Force x server to NOT be able to "lock the screen" under any circumstances.
This would mean that we could in 100% of any cases be able to alt-tab and do whatever we want.

What you're proposing is to not allow fullscreen applications at all.
A lot of games would not work well as the mouse would escape from their play area and not be able to wrap.
This is a very short sighted idea and does not address the actual problem.

---

### Post by OpenTangent on 2011-01-20
I've written an article on this issue for Memeburn:
[http://memeburn.com/2011/01/ubuntus-fundamental-flaw-frozen-full-screen-apps/](http://memeburn.com/2011/01/ubuntus-fundamental-flaw-frozen-full-screen-apps/)

hopefully it encourages the developers to come up with a solution for us. Would be really useful to be able to change workspaces while running fullscreen games.

---

### Post by handy on 2011-01-20
> **OpenTangent said:**
> I've written an article on this issue for Memeburn:
[http://memeburn.com/2011/01/ubuntus-fundamental-flaw-frozen-full-screen-apps/](http://memeburn.com/2011/01/ubuntus-fundamental-flaw-frozen-full-screen-apps/)

hopefully it encourages the developers to come up with a solution for us. Would be really useful to be able to change workspaces while running fullscreen games.

I agree. The ability to change workspaces whilst running full-screen games or whatever would be a brilliant innovation. Especially if this ability remained unaffected by a crashed full-screen game or app'.

---

### Post by gabba on 2011-01-20
> **OpenTangent said:**
> I've written an article on this issue for Memeburn:
[http://memeburn.com/2011/01/ubuntus-fundamental-flaw-frozen-full-screen-apps/](http://memeburn.com/2011/01/ubuntus-fundamental-flaw-frozen-full-screen-apps/)

hopefully it encourages the developers to come up with a solution for us. Would be really useful to be able to change workspaces while running fullscreen games.

Thanks for that article. I've been exploring other solutions to this, and they're all flawed in one way or another. For instance after a pretty complicated set-up (and sorting through half-functional helper apps) you can run the game on a separate X server to kind of emulate the alt-tab functionality. But if you switch out of the game to the other server and then switch back, you get a white cursor arrow stuck right in the middle of your screen. Doesn't really enhance the gaming experience.

---

### Post by henz103 on 2011-05-21
In Microsoft Windows I can ALT+TAB or ALT+F4 (Close) any fullscreen game also I can use my keyboard volume controls while inside games, I don't know why Ubuntu Developers say that its not operating system problem and its application problem. Its not true.

---

