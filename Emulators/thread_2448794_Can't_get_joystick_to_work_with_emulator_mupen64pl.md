---
title: "Can't get joystick to work with emulator mupen64plus"
date: 2020-08-13
forum: Emulators
---

### Post by plutobuntu on 2020-08-13
Hi, I've installed mupen64plus-qt and it seems like it works fine, the roms load but I am unable to play because it doesn't seem to register my joystick at all.
 I've searched for help online, and tried to modify the .cfg file. But it I have two problems:
1- It doesn't seem to save properly, after I load a rom the changes to the file reset to default.
I change the name to of the joystick to "SHANWAN Trust Gamepad", and it changes back to the previous name...
 2-Also, I don't have a way to know which are the correct inputs. For what I've seen online, I should check with jstest-gtk, but in my case, while I have it installed, I don't have any inputs to copy there since the program doesn't recognize my joystick.
The program that recognizes my joystick is gamepad tool:
[http://generealarcade.com/gamepadtool/](http://generealarcade.com/gamepadtool/)
This has worked with other emulators (zsnes, higan), but it seems to not work with mupen64plus. In the interface of gamepad tool, I have no way to know which are the imputs I should be copying for the .cfg file.
I hope I've been clear enough.
PD: if you happen to know an alternative to the emulator I'm trying for N64, please let me know. But I think it is the only alternative for Ubuntu.

---

### Post by deadflowr on 2020-08-14
*Thread moved to **Emulators***

What is the gamepad device?

> PD: if you happen to know an alternative to the emulator I'm trying for N64, please let me know. But I think it is the only alternative for Ubuntu.
Not really an alternative since it still uses mupen64plus, but you can try retroarch, as it has a nifty gui to set things.
Takes a moment to figure out
See:[https://www.retroarch.com/index.php?page=linux-instructions]("https://www.retroarch.com/index.php?page=linux-instructions")
[https://www.retroarch.com/index.php?page=interface]("https://www.retroarch.com/index.php?page=interface")


Edit: I forgot about the alternative gui for mupen64plus, M64PY:
[http://m64py.sourceforge.net/]("http://m64py.sourceforge.net/")
Which has a nice gui for setting up controller configurations.

---

### Post by plutobuntu on 2020-08-14
My gamepad device is: trust gtx 540, it has an xbox controller mode.

I guess I'll check retroarch, but it seems a bit too complicated.

I have installed m64py 0.2.4 form the software store and it doesn't seem to work. It asks me for paths to the roms, plugins, library and data. I set the rom directory, but every time it seems to "forget it" and it asks me again.
Maybe if I try installing the 0.2.5 it could work? I'm ashamed to say I can never install tar files tho...

EDIT: I installed and tried Retroarch. It works and I can assign buttons, but I have no idea how to configure the c-buttons for the n64 games. I'm not sure they can be assigned from the GUI.

EDIT 2: I figure it out, I had to assign the c-buttons to the right analog... I guess that settles it!

---

### Post by deadflowr on 2020-08-15
Yeah, it took me longer than I wanted to figure out how to setup retroarch,
but I also had to figure out how to setup different control schemes for both mupen and pcsx-reloaded (PlayStation One emulator).
( i finally figured out that a specific settings option that is suppose to allow menu access for the running game was disabled,
enabling that allows configuring settings for the game being played and the emulator it uses)

That said, if you find the solution at hand works, please go ahead and mark this thread a s solved:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

