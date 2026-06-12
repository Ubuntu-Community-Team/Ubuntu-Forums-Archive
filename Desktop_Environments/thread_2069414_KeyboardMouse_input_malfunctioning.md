---
title: "Keyboard/Mouse input malfunctioning"
date: 2012-10-10
forum: Desktop Environments
---

### Post by may5 on 2012-10-10
I recently installed Ubuntu 12.04 LTS on my desktop computer. Pretty much everything worked great out of the box, however sometimes I encounter an issue with my keyboard and mouse input. The symptoms (detailed below) are very odd and hard to describe to the point where I'm not even sure what to enter into Google, and all of my attempts at searching for others with this problem have turned up no results. Nothing even close. So I've decided to register an account on here and formally ask. Please excuse me if this has been posted in the wrong section.

The issue only crops up after my machine has been on for a while, following a period of disuse in which it is either locked (with Ctrl+Alt+L) or I've logged out. The only remedy I've come across is a swift reboot, after which the problem reappears at its own discretion.

I've experimented with my machine when it is in this state to attempt to collect an understanding of the exact issue. Nevertheless, I lack a general theory on what is happening, and so the following description likely reflects my confusion in its disorganized state.

**Symptoms:**

The mouse only works within one application. Clicking on any other application, the top bar, or the dashboard has absolutely no effect. Even the cursor does not change to reflect the mouse hovering over a button or text box, unless said button/text box is within the mouse-active application.

The keyboard works in a similar manner, but not necessarily for the same application as the mouse. A single application will respond to keyboard input, including commands that affect the application such as Alt+F4, or holding Alt to show the menu buttons on the top bar. I cannot switch applications with the keyboard in this state. Alt+Tab and Alt+` have no effect. Pressing the Windows key will show the menu with which I can launch another application. This menu does respond to keyboard input, but not mouse input. I can launch a new application with this menu, but the keyboard and mouse will still be tied to their respective applications. I can, however, use Ctrl+Alt+T to launch a new terminal window, and the keyboard will be tied to the new window, though the mouse does not change. Exiting an application with the keyboard (since I cannot click the close button) will give the previous application the keyboard.

Sometimes I can get the input for either the keyboard or the mouse to switch to another application, but the circumstances in which this occurs are not very clear to me. Again, rebooting the computer is the only (temporary) solution I've found.

Both my keyboard and mouse are USB devices. I'm somewhat new to Ubuntu/Linux in general, so I don't really know what commands to run that would enlighten me. Any suggestions would be very helpful!

Thanks!

---

### Post by TSandman on 2012-11-07
I've got exactly the same problem under XFCE (Xubuntu 12.10)

Very very hard to properly search in google :(


I've found that when that happened, I could "most of the time" switch applications by alternating right clicking on the system menu bar to get its contextual menu, then selecting an open application on it with the left mouse button... 

the fastest way I've found to work around this (no fix at all, but faste than rebooting) is that I have to restart lightdm, then everything comes back to normal for a while (many hours).  Unfortunately, if I've left the computer running overnight, I still have to restart lightdm as everything is acting crazy again...

---

### Post by may5 on 2012-11-08
Thanks, it's good to know I'm not the only one with this problem!

If I might ask, what command did you use to restart lightdm?

As a sort of update, I've found that unplugging and reinserting both the mouse and keyboard USB connectors while in this state has no effect, and the output of the xinput command (no parameters) is the same in this state as when the machine functions normally.

---

### Post by may5 on 2012-11-20
**Update:**

I just happened to figure out the cause of these problems by chance. It turns out these issues were caused by my keyboard! I have a Saitek Eclipse II which has a button on it that changes the color of the backlight behind the keys. Pressing this button causes the strange symptoms to occur. What's strange is that it affects the mouse as well. I usually press this button a few times to turn off the back light when I lock my computer, so when I log back in the input is all messed up. I've since switched keyboards and the problem has disappeared. I never thought to Google my keyboard model, but after this discovery I found that there's an open bug report for it [URL="https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/945962"]
Bug #945962[/URL] but it seems to have expired.

---

