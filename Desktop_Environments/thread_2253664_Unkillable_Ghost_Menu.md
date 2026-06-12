---
title: "Unkillable Ghost Menu"
date: 2014-11-21
forum: Desktop Environments
---

### Post by RadiantPhoenix on 2014-11-21
What I did:
[LIST]
[*]Clicked on the update manager applet to bring up its menu 
[*]Update Manager applet disappeared 
[/LIST]
What I expected:
[LIST]
[*]Menu disappears 
[/LIST]
What I got:
[LIST]
[*]Menu becomes blank and floats on top of everything 
[/LIST]

What I tried to do to fix it:
[LIST]
[*]xkill 
[*]Clicked on ghost menu 
[/LIST]
What I expected:
[LIST]
[*]Menu disappears, maybe the system becomes unstable or something, but that's not a huge problem, I can just reboot it. 
[/LIST]
What I got:
[LIST]
[*]Nothing happened 
[/LIST]

Illustrative image:
[ATTACH=CONFIG]258103[/ATTACH]

EDIT: Note: I'm pretty sure it will go away if I restart the computer, but that's sometimes very inconvenient.

EDIT 2: Forgot to mention: Running Xubuntu 12.04-x64

EDIT 3: Possible solution:```
xfwm4 --replace
```

---

### Post by Frogs Hair on 2014-11-21
Look in session and startup and clear saved sessions under the session tab . Log out and back in and see if that helps.

---

### Post by RadiantPhoenix on 2014-11-22
As I said in the first edit, I expected it to go away when I restart. (and it did)

The problem is that closing everything I have open is sometimes very inconvenient.

---

### Post by Frogs Hair on 2014-11-22
Did you try to clear saved sessions as was suggested ? The logout and in was to be done once after clearing the sessions.

---

### Post by RadiantPhoenix on 2014-11-22
I didn't check logging out and logging in, because I'm pretty sure that would still require me to close everything I'm doing, at which point I might as well restart the computer (which works).

Was that supposed to be something that would provide more information on what the bug was?

---

### Post by Frogs Hair on 2014-11-22
On occasion while using XFCE I would encounter a menu related artifact on the screen which would re-occur and I found that clearing the session in session and startup and logging out and back in removed the artifact . It's something to try that might help. Logging out will require closing open applications.

---

### Post by RadiantPhoenix on 2014-11-22
It's not re-occuring for me, it just sticks around until I restart, and I was hoping I could find a way to make it go away without closing the other stuff I'm working on.

---

### Post by Frogs Hair on 2014-11-23
If it is something related to the session memory it will remain until logout or restart. I wrote re-occurring because the artifact in my case would return after reboot until the session memory was cleared.

---

### Post by RadiantPhoenix on 2014-12-22
I had a similar problem show up a few minutes ago, and made it go away with ```
xfwm4 --replace
```
This was a window, not a menu, but it might work for menus too.

---

### Post by RadiantPhoenix on 2015-02-04
Had the menu problem again. "xfwm4 --replace" didn't immediately solve it, but I eventually managed to make it go away like this:

[list]
[*] After "xfwm4 --replace" didn't make it go away, I used "sudo aptitude update" to get the icon back
[*] I attempted to click on the icon, but it didn't respond, nor did it acknowledge the mouseover
[*] Neither did the other icons nearby
[*] ... then I moved the mouse away and the ghost menu went away, and the icons started responding again. Yay!
[/list]

... I also got a crash report about Update Manager, so that might be it.

---

### Post by RadiantPhoenix on 2015-04-21
Had the problem again. This time I had to go the further step of right-clicking on something else on a panel.

---

