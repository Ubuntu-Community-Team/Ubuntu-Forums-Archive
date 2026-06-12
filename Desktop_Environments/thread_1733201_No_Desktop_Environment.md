---
title: "No Desktop Environment"
date: 2011-04-19
forum: Desktop Environments
---

### Post by brettreardon123 on 2011-04-19
After updating my Ubuntu 10.10 to 11.04, my desktop environment has disappeared. Linked is an image of what I am able to see. I can't use Alt+F2 to run programs, and anything I open from the desktop is without the usual taskbar (with minimize, maximize, and close buttons). I was wondering if there was any way to install or force start my Unity or Gnome desktop environment, as this is not much use to me at this point.

[http://dl.dropbox.com/u/6411204/IMG_20110418_211639.jpg](http://dl.dropbox.com/u/6411204/IMG_20110418_211639.jpg)

---

### Post by Copper Bezel on 2011-04-19
Were you using Emerald or Metacity-style decorations with Compiz previously?

Hmm. Ctrl+Alt+T is the new shortcut for opening a terminal, but it probably won't work. You don't have Ctrl+Alt+Backspace to get back to the login screen unless you've enabled it, I'm assuming you had automatic login turned on (or this wouldn't be a problem,) and there's no way to know whether Compiz is running at all. Metacity clearly isn't running as the fallback, and neither Emerald or gtk-window-decorator is running as the window decorator to provide your frames and window controls. 

Here's a thing: since you have desktop icons, that means Nautilus is running. Do you have a txt file in your Templates directory? If so, you can right-click the desktop, create a .txt file, and then right-click the file and use Properties to make it executable. Then you can run any command from inside, like 

compiz --replace && gtk-window-decorator && gnome-panel

which should get you back your Gnome parts, if they're working at all.

---

### Post by matt_symes on 2011-04-19
Hi

EDIT: Slight typo. Copper bezel meant to type... (I type typo's all the time :D)

```
compiz --replace && gtk-window-decorator --replace && gnome-panel
```

You can also try ALT + F2 to bring up the run dialog and enter the commands posted above that way.

If the above command do not work create a new user, log out and log into that account.

Do you have the panels then ? If it does i would suggest it's your gnome settings

The command for that from ALT + F2 is

```
users-admin
```

Kind regards

---

### Post by Copper Bezel on 2011-04-19
Alt+F2 doesn't work without a Gnome Panel, which is why I suggested the workaround with creating a text file (but thanks for the correction on the command!)

If he can log out at all, again, we don't have (quite as much) a problem, because he can use safe mode or whatever other DE options he might have installed. We could also, reasonably, kill x from a VT to *get* to the login screen, if it comes to it.

Incidentally, this might be a better method: if the terminal shortcut doesn't work, use the text file workaround to launch gnome-terminal, then do everything else from there. That way, we get error feedback to see what's broken.

---

### Post by matt_symes on 2011-04-19
Hi

> Alt+F2 doesn't work without a Gnome Panel

I did not know that. Thanks :P

Kind regards

---

### Post by Copper Bezel on 2011-04-19
Yeah, this is why Synapse is a good thing to have around. = ) (And I run it from a Compiz keybinding, not its own internal hotkey catcher, which is unpredictable.)

---

### Post by brettreardon123 on 2011-04-19
Unfortunately, the text document workaround did not work. This launched the terminal, which showed:
compiz (core) - Error: Couldn't load plugin 'ccp'
compiz (core) - Error: Couldn't load plugin 'ccp'
Window created on XQueryTree, map state isViewable? 0

the third line is repeated about 20 times, with the number one instead of zero on 3 of them. Nothing else changed in the entire visible screen, and I'm back to where I started. I tried typing "users-admin" in and nothing happened. None of the usual prefixes are in the window (the typing I do starts immediately at the left, with none of the usual username, $/#, etc). Would the best route at this point be to start fresh with a new installation of Ubuntu?

---

### Post by Copper Bezel on 2011-04-19
Honestly, if the terminal is doing *that*, I'd start to think that that's on the table, yes, assuming that you don't keep your home partition encrypted and thus can recover your data using a LiveCD. This is looking weirder than I'd thought.

Do you get that same odd behavior (no prompt) if you switch to a virtual terminal with Ctrl+Alt+F1 and log in there? (If you've never done this before, it's Ctrl+Alt+F7 or F8 to get back.)

---

### Post by brettreardon123 on 2011-04-19
Ok, I got to the virtual terminal, and I get a prompt. I tried running the code that you said to run from the txt, but it still did not work... any other suggestions on what I can run to make this work? I seem to be able to run commands in virtual terminal, since I can get a prompt and stuff I put in gives me an output.

---

### Post by Krytarik on 2011-04-19
To reset your terminal to the defaults, and restore its funtionality, copy the content of "/etc/skel" into the toplevel of your home directory, you may backup your own files before.

---

### Post by brettreardon123 on 2011-04-19
Is there a way to do that in virtual terminal? That's effectively all I am able to access right now...

---

### Post by Krytarik on 2011-04-19
> **brettreardon123 said:**
> Is there a way to do that in virtual terminal? That's effectively all I am able to access right now...
Sure, run a command like this:
```
cp /etc/skel/* ~
```

---

