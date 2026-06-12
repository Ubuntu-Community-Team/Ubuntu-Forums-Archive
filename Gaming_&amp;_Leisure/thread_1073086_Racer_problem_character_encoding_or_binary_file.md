---
title: "Racer problem: character encoding or binary file?"
date: 2009-02-17
forum: Gaming &amp; Leisure
---

### Post by SoylentSteak on 2009-02-17
When I double-click racer_0.5.4beta1-english.run I get a message saying it couldn't detect the character coding, and to be sure I wasn't trying to run a binary file. I've tried many different character codings, to no avail. I'm not even sure what a binary file is. How can I get this thing up and running?

---

### Post by SoylentSteak on 2009-02-19
Okay, I have it running, but it won't recognize my controller. It looks for it in dev/js0, but it's actually in dev/input/js0. How do I make it look for it there?

/edit: I created a symbolic link, and on the terminal it says it finds the controller, but it still doesn't recognize anything in the game itself. It just reads "controllers found:0"

---

### Post by SoylentSteak on 2009-02-24
Perhaps I should do something like create a new .ini file? Or just modify default.ini somehow. I have seen other posts stating that one should go to racer.ini and change mouse to genjoy, but there is no genjoy in default.ini for it to point to......
I think the controller ID plays a part in this, but I don't know exactly how I should add the references to it, and how much of the ID name I should use:

Bus 001 Device 002: ID 046d:c216 Logitech, Inc. Dual Action Gamepad

Here is some of the terminal output when I go to the "controls" screen:

QDXJoy: opening joystick dev n=0, devName='/dev/js0'
joystick name: Logitech Logitech Dual Action
QDXJoy ctor
QDXJoy: opening joystick dev n=1, devName='/dev/js1'
QDXJoy: can't create/find joystick #1

---

### Post by baawooly on 2009-03-04
I'm having the same problem with racer looking for the joystick in /dev/js0.  Has anyone discovered a solution?

---

