---
title: "Xbox 360 Controller Configuration?"
date: 2010-10-26
forum: Gaming &amp; Leisure
---

### Post by btpaulie on 2010-10-26
I have a wired Joytech brand Xbox 360 controller that uses a USB connection. On my windows partition, XP actually found the drivers for the controller for me (probably the only time Windows has done something intuitive for me). However, I'm not so lucky with Ubuntu. I want to use this as a game controller, but I can't get it to register at all. Can someone tell me how to configure this controller to act as button presses? E.g. set pressing the "a" button to register as a "z" keystroke on my keyboard.

---

### Post by mister_playboy on 2010-10-27
USB drivers are "universal" and they should work the same way in both Ubuntu and Windows.  Ubuntu most likely can see the controller just fine.

What specific emulator are you using?  You'll need to configure the controller input differently for each emulator.

---

### Post by btpaulie on 2010-10-27
> **mister_playboy said:**
> USB drivers are "universal" and they should work the same way in both Ubuntu and Windows.  Ubuntu most likely can see the controller just fine.

What specific emulator are you using?  You'll need to configure the controller input differently for each emulator.

I'm using ZSNES emulator.

---

### Post by mister_playboy on 2010-10-27
Make sure you have the gamepad plugged in before starting the emulator.

Config > Input > Set Keys

It will ask you to press a button for each assignment.  When you press a button it will move on to the next assignment.  If you press the button and it doesn't move to the next question, then Ubuntu isn't seeing the gamepad.

Try that and tell us what happens. :popcorn:

---

### Post by thatguruguy on 2010-10-28
For what it's worth, I use a generic x-box gamepad on everything from zsnes to dolphin-emu with no issues.

---

### Post by btpaulie on 2010-10-28
I tried, but it still does not automatically read the controller. I get to the menu below, and no luck. Thanks for your help so far, though![IMG]http://ubuntuone.com/p/Mmf/[/IMG]

---

