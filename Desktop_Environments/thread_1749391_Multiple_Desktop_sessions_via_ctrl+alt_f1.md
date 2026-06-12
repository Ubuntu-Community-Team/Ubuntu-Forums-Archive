---
title: "Multiple Desktop sessions via ctrl+alt f1"
date: 2011-05-04
forum: Desktop Environments
---

### Post by MikeR. on 2011-05-04
Hey all,

I want to be able to run multiple desktop sessions, but when I goto the next session terminal and type startx -- :2 the screen just goes all black. :/ help?

---

### Post by aphatak on 2011-05-04
Try this -
[LIST=1]
[*]Hit ctl-alt-f2.  This gives you a virtual console with a log-in prompt.
[*]Log in.  You can use the same username that you logged in with before you hit ctl-alt-f1, or another user id belonging to a different account on the same PC.
[*]At the command prompt, enter 'xinit -- :<x> VT<n>'.  This tells the X-server to start a new instance using display number <x> and show it on Virtual Terminal <n>.  For simplicity's sake, let's say <x> can be '2' to '6', and <n> can be '8' to '12'.
[*]This should result in showing you a screen with a prompt;  this time, it is not really a plain old character console, though;  it is your X-server pretending it is a character terminal.  This screen should have the command prompt again.  Move your mouse till the cursor appears in the make-believe terminal area, then enter the command to start a graphical environment.  If you want a Gnome desktop, this command is 'gnome-session'; if KDE desktop, it is 'startkde', if you want XFCE, it is 'startxfce4'; if LXDE, it is 'startlxde'.  Pray to that Great OS in the Sky, and hit <enter>.  You should see the desktop environment of your choice.
[/LIST]
If you hit ctl-alt-F7, the graphical environment into which you logged in shows up.  If you started an additional graphical environment in VT[8..12], clt-alt-F[8..12] takes you to that screen.
Remember, however, if initially you gave the xinit command in VT1 (you guessed it - that's what you get when you get ctl-alt-F1), VT1 is booked till you get out of the corresponding environment.  You can hit clt-alt-F2 to start another environment in VT9 (reached by ctl-alt-F9) and so on, until you run out of the F keys.
To get out of the new environment, -
[LIST=1]
[*]Switch to it with the appropriate ctl-alt-Fn key.
[*]Log out of it.  You should see the pretend-character terminal again.  Now depending on which desktop environment you chose, it may or may not show you a command prompt.  Make sure you move your cursor to the mock-terminal area, then hit ctl-c, and give it a second or two.  Do this until the command prompt shows.
[*]At the command prompt, enter the command 'exit'.  This takes you to the real character terminal - the one where you entered the xinit command.  Enter the command 'exit'.  You should see the log-in prompt again.
[/LIST]
There are plenty of wierd and wonderful things you can do.  You can start a graphical session on another computer on the network - as long as you have ssh-with-X access to it, you can have up to twelve (yes, twelve) more graphical sessions in any combination of remote and local, and so on.  If you need to do such things, put a post in here, and I can help out.

---

### Post by MikeR. on 2011-05-04
> **aphatak said:**
> Try this -
[LIST=1]
[*]Hit ctl-alt-f2.  This gives you a virtual console with a log-in prompt.
[*]Log in.  You can use the same username that you logged in with before you hit ctl-alt-f1, or another user id belonging to a different account on the same PC.
[*]At the command prompt, enter 'xinit -- :<x> VT<n>'.  This tells the X-server to start a new instance using display number <x> and show it on Virtual Terminal <n>.  For simplicity's sake, let's say <x> can be '2' to '6', and <n> can be '8' to '12'.
[*]This should result in showing you a screen with a prompt;  this time, it is not really a plain old character console, though;  it is your X-server pretending it is a character terminal.  This screen should have the command prompt again.  Move your mouse till the cursor appears in the make-believe terminal area, then enter the command to start a graphical environment.  If you want a Gnome desktop, this command is 'gnome-session'; if KDE desktop, it is 'startkde', if you want XFCE, it is 'startxfce4'; if LXDE, it is 'startlxde'.  Pray to that Great OS in the Sky, and hit <enter>.  You should see the desktop environment of your choice.
[/LIST]
If you hit ctl-alt-F7, the graphical environment into which you logged in shows up.  If you started an additional graphical environment in VT[8..12], clt-alt-F[8..12] takes you to that screen.
Remember, however, if initially you gave the xinit command in VT1 (you guessed it - that's what you get when you get ctl-alt-F1), VT1 is booked till you get out of the corresponding environment.  You can hit clt-alt-F2 to start another environment in VT9 (reached by ctl-alt-F9) and so on, until you run out of the F keys.
To get out of the new environment, -
[LIST=1]
[*]Switch to it with the appropriate ctl-alt-Fn key.
[*]Log out of it.  You should see the pretend-character terminal again.  Now depending on which desktop environment you chose, it may or may not show you a command prompt.  Make sure you move your cursor to the mock-terminal area, then hit ctl-c, and give it a second or two.  Do this until the command prompt shows.
[*]At the command prompt, enter the command 'exit'.  This takes you to the real character terminal - the one where you entered the xinit command.  Enter the command 'exit'.  You should see the log-in prompt again.
[/LIST]
There are plenty of wierd and wonderful things you can do.  You can start a graphical session on another computer on the network - as long as you have ssh-with-X access to it, you can have up to twelve (yes, twelve) more graphical sessions in any combination of remote and local, and so on.  If you need to do such things, put a post in here, and I can help out.

its not recognizing VT as a command option did i enter it right? 'xinit -- :3 VT 8'

---

### Post by aphatak on 2011-05-05
I'm afraid you didn't.  There should be no space between 'VT' and '8'.  You could copy and paste this -
```
xinit -- :3 VT8

```

---

### Post by aphatak on 2011-05-11
Oops! Noticed an error in my response - it should be 'vt8', not 'VT8'.

---

