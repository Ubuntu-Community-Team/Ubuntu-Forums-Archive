---
title: "KDE5 no longer works"
date: 2015-05-20
forum: Desktop Environments
---

### Post by FreakShow! on 2015-05-20
Hi,

I installed Kubuntu 15.04 and was very happy with how things were going. I started to notice there were some issues with the animations. I'd click to minimise a window and the screen would flicker and look as if nothing had changed. When I started to mouse over the supposedly minimised window, the window behind would then start to appear. Finding where the title bar for that window and moving that second window would then repaint the window and allow it to appear.

I tried toning down the animations, but that didn't seem to do much. What I should have done is turned off the animations. What I did instead though, was install the AMD Graphics driver, fglrx, using the hardware drivers settings window. This seemed to go OK, but still the same issues remained.

At the time, I had a virtualbox windows 7 running updates and so left that to finish before I continued trying to do anything (note, I hadn't rebooted after installing the AMD driver). I came about a couple of hours later and whilst I could move the mouse, no windows would respond to clicks, or keyboard input. I tried dropping to a terminal and running some commands I'd googled, such as restarting the kwin server, but I was told kwin was not installed. As I couldn't find much more, I hit the reset button.

Rebooting, I logged in, and was greeted with Skype, Terminal window and a dolphin window that had loaded from the previous session. Nothing else. No background picture, no taskbar. The top left corner did activate the command view (all windows currently open showing so that you can select a particular window).

I blamed the AMD driver and googled how to roll back, but half way through typing the command off of my phone, the system locked. Probably after 5-10mins. So I rebooted and quickly tried to do it, but couldn't before it froze. So instead, I installed the XFCE4 interface. This is what I'm running on right now.

How can I get KDE to work again? I've purged the fglrx driver (I think). I reinstalled KDE5 too. Both of these via terminal so it may be I've missed something.

Anything I can try? Anything extra I should have done to remove fglrx and kde5 first before reinstalling?

TIA!

EDIT: Should probably say, my system is an AMD AM1 5350. It has 8Gb RAM and is driving two monitors, one via DVI and one via HDMI.

---

