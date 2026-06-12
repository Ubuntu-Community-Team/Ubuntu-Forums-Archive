---
title: "Disappearing (mouse) pointer"
date: 2009-03-05
forum: General Help
---

### Post by sclaes on 2009-03-05
The pointer disappears after the 4th time the power saving was activated (System Settings->Monitor & Display->Power saving).

Any idea why this happens? How can I get the pointer back without rebooting?


I tried xsetpointer but 'xsetpointer 3:' gives an error:
'Extended device 3: not found'

But according to 'xsetpointer -l' it is one of the available devices... (3: "Configured Mouse"   [XExtensionPointer])

Any suggestions?

TIA

---

### Post by sclaes on 2009-08-27
> **sclaes said:**
> The pointer disappears after the 4th time the power saving was activated (System Settings->Monitor & Display->Power saving).

Any idea why this happens? How can I get the pointer back without rebooting?


I tried xsetpointer but 'xsetpointer 3:' gives an error:
'Extended device 3: not found'

But according to 'xsetpointer -l' it is one of the available devices... (3: "Configured Mouse"   [XExtensionPointer])

Any suggestions?

TIA

Problem still not solved. The only way to get the pointer back is to reboot the computer. BTW: the pointer disappears after the computer comes back from power save mode, but not always. Switching to terminal mode before leaving the computer alone seems to help.

---

### Post by dwiedenfeld on 2009-09-07
I have the same problem. It seems to happen after the machine has been on for several hours, but not always.

I should point out that it is the cursor that disappears. I have both a USB mouse and a touchpad, and it affects both.

Another point: the cursor just becomes invisible. Both the mouse and touchpad will move its position around, but you can't see it. I set it so "Crtl" indicates where the cursor is located, and you can see it can be moved around. If you can figure out how to get it over, say, the applications menu, you can click, and it opens the menu. In other words, everything seems to work, it's just that the cursor is invisible.

The only solution I've found is to reboot. Unplugging the mouse and plugging it back in, or turning the touchpad off then back on, do not do anything.

It's on a Compaq Presario F500 laptop running Ubuntu Jaunty (not Kubuntu as the first post in the thread). The mouse is basic Logitech. 

Any ideas on how to get this solved, or how to get it back?

---

### Post by sclaes on 2009-09-11
> **dwiedenfeld said:**
> I have the same problem. It seems to happen after the machine has been on for several hours, but not always.

I should point out that it is the cursor that disappears. I have both a USB mouse and a touchpad, and it affects both.


Some call it the (mouse) pointer others call it the (mouse) cursor. It's the thing that moves on the screen if you move your (favourite) pointing device (a mouse, a rat or something else).

> **dwiedenfeld said:**
> 
Another point: the cursor just becomes invisible. Both the mouse and touchpad will move its position around, but you can't see it. I set it so "Crtl" indicates where the cursor is located, and you can see it can be moved around. If you can figure out how to get it over, say, the applications menu, you can click, and it opens the menu. In other words, everything seems to work, it's just that the cursor is invisible.

The only solution I've found is to reboot. Unplugging the mouse and plugging it back in, or turning the touchpad off then back on, do not do anything.


Right. The pointer/cursor just disappears. It's still possible to see where it should be by moving the pointing device, but the pointer/cursor remains invisible.

Because it's a bit tricky to shutdown the computer without visible pointer/cursor, I switch to a terminal (ctrl-alt-F1) and type 'sudo shutdown -r now' to reboot the computer. I don't know any other way to get the pointer/cursor back.

Someone suggested ctrl-alt-backspace (to restart xwindows) but that doesn't help. Worse: it can cause the problem.

---

### Post by commonplace on 2009-11-01
My wife is having this exact problem on a clean install of Ubuntu 9.10 (Karmic). Did anyone ever find a solution? Under power management, the close-lid action is set to 'Blank screen'. I was going to set it to 'Do nothing' but that's apparently no longer an option.

Anyone? It's quite bothersome having to reboot the entire laptop just to get make the mouse cursor visible again, and it's nearly impossible to navigate with an invisible mouse cursor (even though it works, it's just extremely difficult).

/Kevin

---

### Post by commonplace on 2009-11-02
Bump. My wife is pushing to go to Windows 7... I don't feel like dealing with the inevitable spyware and other problems that come along with it.

This is the only major glitch for her, but it's a deal breaker.

/Kevin

---

### Post by commonplace on 2009-11-02
[This]("http://ubuntuforums.org/showpost.php?p=8202056&postcount=6") solved it for my wife.

/Kevin

---

### Post by gstvslzr on 2010-01-26
I find out that the mouse still there. I installed the little eyes on the top panel (the one that follows the mouse) and it indeed followed. When I move the mouse (instintively) to my left, it reached my laptop screen and voila the mouse appears.

I still looking for a permanent solution to this dilemma.

---

### Post by italianoman421 on 2010-01-26
I have to bump this topic.  Karmic runs on my primary work computer and the cursor disappears on a daily basis at random times.  I really hate to transfer my stuff to windows 7, I much prefer Ubuntu, but this is making it unworkable. Any solutions? Also, is there a way to report this as a 9.10 glitch issue to address in 10.04? I've used Ubuntu without trouble for several distros and never had this issue.

Thanks

---

### Post by charonred on 2010-01-31
I have the same problem in Ubuntu and it's getting really annoying. I moved to Karmic 9.10 (32) from Hardy 8.04 LTS (32) so that my new graphics card would work properly; but this disappearing cursor is damned annoying.

I have dual monitors set as one large desktop and the mouse disappears in the last 20 mm of the left had screen before reappearing on the right hand screen, but sometime i have to move the mouse al over the pad before it is visible again.

---

### Post by specialk1st on 2010-07-13
I just posted this on another thread, but having had this problem myself I figured I would spread the word. :)

You can use this as a workaround to get back the missing cursor after opening your laptop lid ...

Try switching desktops via:
Ctrl+Alt+LeftArrow OR Ctrl+Alt+RightArrow

It is a reported bug.

Resource:  [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/552058](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/552058)

---

### Post by sakrificeking on 2010-07-24
I am having the same problem too. The mouse pointer disappears after waking up from standby (in Ubuntu 10.04). 

Ctrl+Alt+Right and Ctrl+Alt+Left made the cursor visible again, but this stopped working from today.
Ctrl+Alt+F1 and Ctrl+Alt+F7 works now.
I also enabled the option "Show position of pointer when Ctrl key is pressed" from System->Preferences->Mouse settings. This will show the location of mouse pointer when I press the Ctrl. So it helps in navigation when the pointer disappears.

These are just workarounds. I do not know the exact fix.

---

### Post by sclaes on 2010-08-05
> **sakrificeking said:**
> I am having the same problem too. The mouse pointer disappears after waking up from standby (in Ubuntu 10.04). 

Ctrl+Alt+Right and Ctrl+Alt+Left made the cursor visible again, but this stopped working from today.
Ctrl+Alt+F1 and Ctrl+Alt+F7 works now.
I also enabled the option "Show position of pointer when Ctrl key is pressed" from System->Preferences->Mouse settings. This will show the location of mouse pointer when I press the Ctrl. So it helps in navigation when the pointer disappears.

These are just workarounds. I do not know the exact fix.

Unfortunately those workarounds don't work here.

BTW: I can't find any option or setting that will show the location of the mouse pointer when ctrl is pressed.
I'm using KDE (version 3.5 iirc) and I looked in System Settings -> General -> Computer Administration -> Keyboard and Mouse -> Mouse

I just noticed that after restarting X Windows (ctrl alt backspace), the bouncing pointer (I suppose an alternative hourglass) appears while some applications are started. When it disappears the normal pointer should appear but it doesn't.

---

