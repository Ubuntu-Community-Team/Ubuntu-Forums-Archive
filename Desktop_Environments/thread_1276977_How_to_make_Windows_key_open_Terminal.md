---
title: "How to make Windows key open Terminal?"
date: 2009-09-27
forum: Desktop Environments
---

### Post by wotnartd on 2009-09-27
Hey folks, I've been using Ubuntu for a few months and am trying to figure out how to get the Windows key to open terminal, like a shortcut key, I guess.  Anybody have any ideas on how to make this work?    I'm still pretty much an ubuntu newbie, and any guidance would be very helpful.  Thanks.

---

### Post by wojox on 2009-09-27
Sure that's what I use it for as well. Just open System > Preferences > Keyboard Shortcuts and scroll down to Run a terminal Double click it and press the windows key.

---

### Post by wotnartd on 2009-09-27
> **wojox said:**
> Sure that's what I use it for as well. Just open System > Preferences > Keyboard Shortcuts and scroll down to Run a terminal Double click it and press the windows key.

 Thank you so much, wojox.  I guess I was looking so hard I didn't see what was right there in front of my face.  I appreciate this very much.

---

### Post by Simeo on 2011-01-05
I still can't assign windows key to open a terminal... my key does nothing.

---

### Post by TechWiz2100 on 2011-01-05
> **Simeo said:**
> I still can't assign windows key to open a terminal... my key does nothing.

Windows key is a special mod or "Super" key ergo it cannot be used alone it must be assigned with another key such as Win+T or in linux speak <Super> + T 

=P

---

### Post by likwidoxigen on 2011-02-05
Don't mean to revive a dead thread but I hate not to see this "Solved:"

All you have to do is put in Super_L   instead of <Super>T  or whatever you had in there.   After you remove the < and > it's no longer a modifier and just a regular old key, you just need to specify l or r for which "super" key you're interested in.

Enjoy!

---

### Post by Krytarik on 2011-02-06
> **likwidoxigen said:**
> Don't mean to revive a dead thread but I hate not to see this "Solved:"

All you have to do is put in Super_L   instead of <Super>T  or whatever you had in there.   After you remove the < and > it's no longer a modifier and just a regular old key, you just need to specify l or r for which "super" key you're interested in.

Enjoy!
Ok, it finally works with "Super_L".8-) But you have to enter it manually into Gconf:
- press Alt+F2
- enter "gconf-editor"
- browse to "/apps/metacity/global_keybindings/run_command_terminal"
- set the key(s) you want

---

### Post by Copper Bezel on 2011-02-06
I've had weird luck with setting these commands. I have Alt+F2 bound to xfrun4, since I'm not using a Gnome panel, and sometimes it would just not take the command. Set it to Super+F2 and I haven't had any problems. Likewise XKill, which I had set to Super+X until, in one particular session, the keystroke wasn't being recognized and I changed it to Super+Q, which works consistently.

I'd actually set these both in Compiz and in Keyboard Shortcuts (which are ignored in case of a conflict, right?) the first time.

---

### Post by Krytarik on 2011-02-06
> **Copper Bezel said:**
> 
I'd actually set these both in Compiz and in Keyboard Shortcuts (which are ignored in case of a conflict, right?) the first time.
I just yet tested it. If there are conflicting shortcut settings, those set in Compiz precedes those set in Keyboard Shortcuts.

---

