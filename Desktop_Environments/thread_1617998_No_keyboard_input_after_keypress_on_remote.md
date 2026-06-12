---
title: "No keyboard input after keypress on remote"
date: 2010-11-10
forum: Desktop Environments
---

### Post by Viciou§ on 2010-11-10
Hello!

I am running Lucid 10.04 and Gnome.
I have a remote that works like a keyboard mouse HID combo.

I am trying to get all the buttons to work but some buttons on the remote doesn't generate a keypress in xev.
Most buttons on the remote generate a key combination, play button generates ctrl+shift+P for example.

The problem is that when pressing theese keys, I can no longer get any input from the keyboard or remote.
In xev I can see NotifyGrab and NotifyUngrab events and afterwards the computer seem to no longer recognize any keypresses from my keyboard or remote.
I can use my mouse finw though but pressing menus doesn't bring up the menu, only marks it. Switching between windows works.

I am really stuck in debugging this and getting it the remote to work.
Lirc is out of the question.
The mouse functionality of the remote disappears and 2 or more buttons generate the same response with lirc (using devinput driver).

Is there anything  I can do to see what happens when I press the non functioning keys on the remote?
It has to be something that I can run before pressing the keys since I can no longer use the keyboard afterwards.
Most of the times I just reboot the computer but by waiting 5+ minutes things start to work again.

Edit: I have tested using evtest and it seems like the buttons get stuck.
I found this: [http://ktemkin.com/en/?p=25]("http://ktemkin.com/en/?p=25")
but /sys/devices/platform/i8042/serio0/force_release doesn't exist :(

---

### Post by Viciou§ on 2010-11-14
Bump

---

