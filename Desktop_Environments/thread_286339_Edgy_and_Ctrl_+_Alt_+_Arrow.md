---
title: "Edgy and Ctrl + Alt + Arrow"
date: 2006-10-27
forum: Desktop Environments
---

### Post by ScottMorris on 2006-10-27
Hello fellow Ubuntuers :D , I have a small problem.  I upgraded my 6.06 to 6.10 last night and I have Beryl installed, but after the update the Desktop Cube won't spin with a Alt + Ctrl + Click on the desktop as well as with the Right or Left Arrow keys.  I haven't been able to find out the cause to this problem but it isn't there until I open a program and then the changing to the cube is gone.  If someone knows the remedy this problem it would be much appreciated.

---

### Post by scantan on 2006-10-29
I've just upgraded to Edgy too, and have just found out that my CTRL key doesn't work with shortcuts, but only if I press the CTRL key first.

For example, if I try the ALT + CTRL + click combination and press the CTRL key first, it is as if I had only pressed the ALT key. But of I press the CTRL key first, then the ALT key, then I get the desired effect. Quite anoying.

If I want to CTRL-Tab or any other CTRL+key shortcut (e.g. CTRL+W to close a window), it only works if I press any other modifier key (SHIFT or ALT) before pressing CTRL, even if I then release the first key (SHIFT or ALT). Quite strange.

I am using a brazilian ABNT2 layout keyboard.

---

### Post by nashattan on 2006-10-29
If you have a problem with shortcuts using beryl, you should be able to change them by running 
```
beryl-manager
```
and clicking on "beryl settings manager."  From there you can change whatever shortcuts you want.  In particular, the ones you are talking about are on the "rotate cube" section.  From there you can change the keyboard and mouse shortcuts from their appropriate tabs.

---

### Post by ScottMorris on 2006-10-29
I have tried that an I like having Ctrl + Alt + Right/Left as my desktop switching the same as it is in Metacity and the way it was before I installed Ubuntu 6.10.  And its weird how it works when I first boot up but then when I open a program the shortcut doesn't work anymore.  I even tried Alt + Ctrl + Left/Right and still no luck.

---

### Post by ScottMorris on 2006-10-29
Is this one of the many Edgy problems or is this a problem with Beryl and can be fixed by uninstalling it and reinstalling it? :confused:

---

### Post by scantan on 2006-10-30
I've just found out that my CTRL key works normally if CAPS Lock is on!?!

If CAPS Lock is off, CTRL only works if another modifier key is pressed first, even if this other modifier key is released.

Still lost here...

---

### Post by ScottMorris on 2006-10-30
i wonder if this is a Edgy problem or an Beryl problem?  I still have the same problem with my caps lock key still on, the weird thing is that the shortcuts work fine in Metacity, in Beryl my super key and pause key don't work even though they aren't mapped to any window manager operations.

---

### Post by scantan on 2006-10-31
> **ScottMorris said:**
> i wonder if this is a Edgy problem or an Beryl problem?  I still have the same problem with my caps lock key still on, the weird thing is that the shortcuts work fine in Metacity, in Beryl my super key and pause key don't work even though they aren't mapped to any window manager operations.

You are right. I tested the CTRL key in metacity and all worked fine.

I then tried disabling Beryl... but CTRL only worked when I killed beryl-manager.

Another fact: I have enabled the feature that shows where the cursor is when you press CTRL. And for this CTRL works even with Beryl alive and running. Only in key combinations CTRL doesn't work.

I found a reference about this problem on a Gentoo Wiki:
[http://gentoo-wiki.com/HOWTO_XGL/Troubleshooting#ctrl_key_not_working](http://gentoo-wiki.com/HOWTO_XGL/Troubleshooting#ctrl_key_not_working)

But the cure didn't work for me.

scantan

PS: After reviewing my post, I just thought of disabling the "show cursor" feature. Maybe by pressing the CTRL first the system half triggers that event and doesn't work with any other key. I'll test it when I have access to my computer.

---

### Post by scantan on 2006-10-31
I found a just-started thread on the Beryl-project forum. But no solutions there:

[INDENT][http://forum.beryl-project.org/topic-5997-control-key](http://forum.beryl-project.org/topic-5997-control-key)[/INDENT]

On the other hand I found Ticket #659 on the [Beryl Bug Tracker]("http://bugs.beryl-project.org/") that deals with a simliar problem, "Running Beryl as the window manager breaks the Super key":

[INDENT][http://bugs.beryl-project.org/ticket/659](http://bugs.beryl-project.org/ticket/659)[/INDENT]

Although related to another key, a note on the ticket states that it can be related to some Beryl plugin shortcut and suggests "changing to another profile in beryl--settings, reseting that to default" and then checking if the problem persists.

---

### Post by jasonlfunk on 2006-10-31
SOLVED:
I turned off the find mouse when ctrl key is pressed and that fixed it.

System -> Preferences -> Mouse -> Pointers Tab -> Uncheck "Highlight the pointer when you press Ctrl"

---

### Post by scantan on 2006-10-31
I finally had a chance to test it too (disabling the "Highlight the pointer when you press CTRL" feature), and it also worked for me.

Now CTRL works fine.

Given that I didn't upgrade Beryl and CTRL worked in Dapper/Ubuntu 6.06, I can only think something in Edgy/Ubuntu 6.10 has changed to trigger this quirky behavior.

Maybe this isn't a Beryl bug.

---

