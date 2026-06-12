---
title: "System crashes when Firefox bookmark gets dragged"
date: 2009-05-12
forum: General Help
---

### Post by Fleshtone on 2009-05-12
If I try to reorder the bookmarks in Firefox (3.0.10), the system crashes.  I can reorder them in the "organize bookmarks" dialogue, but not just by dragging them around in the bookmarks dropdown menu.

The system almost completely freezes, and I cant even xkill it through Alt+F2.  The only response I get is the "shut down the computer" menu when I hit the power button.  The menu itself doesn't respond, but it powers itself down after 60 seconds.

I'm surprised I didn't see this anywhere in the forums.

---

### Post by jimbog on 2009-05-13
I have had exactly the same problem for at least a month now, and I haven't been able to find anything in the forums. It's just one thing in a long list of annoyances and unfortunately I don't have the time to spend ages finding a solution.

Hopefully someone knows something about this; it happens 100% of the time when I try to drag bookmarks around the drop-down menu. It's a more spectacular crash than anything I ever experienced in Windows!

I'm using Firefox 3.0.10 and Jaunty Kubuntu.

---

### Post by jimbog on 2009-05-14
Some other people with the same problem: [http://ubuntuforums.org/showthread.php?t=1129486](http://ubuntuforums.org/showthread.php?t=1129486)

---

### Post by jimbog on 2009-05-19
Bump

---

### Post by lovinglinux on 2009-05-19
> **jimbog said:**
> I have had exactly the same problem for at least a month now, and I haven't been able to find anything in the forums. It's just one thing in a long list of annoyances and unfortunately I don't have the time to spend ages finding a solution.

Hopefully someone knows something about this; it happens 100% of the time when I try to drag bookmarks around the drop-down menu. It's a more spectacular crash than anything I ever experienced in Windows!

I'm using Firefox 3.0.10 and Jaunty Kubuntu.

I'm experiencing the exact same problem on Ubuntu Jaunty. It happens when I try to change the bookmark folder through the drop-down menu in the address bar, but not all the time.

My system becomes totally unresponsive, but I still can move the mouse around. The only way to get my stuff back is is killing X with CTRL+ALT+BACKSPACE.

EDIT: Apparently, it's the Open Book extension that is causing this. I disabled it and Firefox stopped crashing, at least for now.

---

### Post by mobilediesel on 2009-05-19
You can do CTRL+ALT+F1, log into the terminal, killall firefox, then exit and CTRL+ALT+F7 to get back to X. That doesn't fix the problem but it lets you get your system back without restarting the whole thing.

> **lovinglinux said:**
> EDIT: Apparently, it's the Open Book extension that is causing this. I disabled it and Firefox stopped crashing, at least for now.
I don't have that extension so I don't know what might be causing it on my system.

---

### Post by lovinglinux on 2009-05-19
> **mobilediesel said:**
> You can do CTRL+ALT+F1, log into the terminal, killall firefox, then exit and CTRL+ALT+F7 to get back to X. That doesn't fix the problem but it lets you get your system back without restarting the whole thing.


I don't have that extension so I don't know what might be causing it on my system.

:oops: Ubuntu is a learning experience every day. Thanks a lot for this tip.

I couldn't get back with CTRL+ALT+F7, but just exiting the terminal did the trick. I was testing without a crash tho.

---

### Post by jimbog on 2009-05-20
I don't have the Open Book extension either. I have disabled all add-ons and still get the crash. For me it happens 100% of the time.

Thanks for the tip about rescuing the system after the crash!

---

### Post by jimbog on 2009-06-02
Is there really no solution to this??

---

