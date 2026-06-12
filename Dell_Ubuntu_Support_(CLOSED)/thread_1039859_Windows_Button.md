---
title: "Windows Button"
date: 2009-01-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Ancalagon82 on 2009-01-14
So my Mini9 came in today.  According to the Quick Reference Guide, the windows button is supposed to make a window go full screen.   However, mine is not working at all.  Not just in Firefox, but in any other window.  Considering the screen isn't huge to begin with, I need all of it!

Any ideas how to turn it on?

---

### Post by Ancalagon82 on 2009-01-18
Bueller.... Bueller....

---

### Post by sirebral on 2009-01-18
Whoa!!!  Read my Suggested Firefox Addons.  I didn't know about this post but I do have some space saving ideas for you.

I also have suggestions for cleaning up your desktop.

I removed the bottom panel. I added a Window List to the top panel, removed the Main Menu, and then I added a Weather Report, the Trash Bin, and the System Resource Monitor, a Workspace Switcher, and the Web Browser button, and the Go Home.

I like the Weather Report and the Sys Resource Monitor.

Then I edited the preferences for the Window list so that they Group When Space is Limited.  I gave myself a second desktop in case I open a lot of windows.

So my Top Bar looks like this:

Go Home, Main Menu, Web Browser, Desktop Switcher, Window List, Weather Report, System Resource Monitor, Trash, Notification Area, Power Manager, nm-applet, Volume Applet, Clock, Quit...

No sure about the full screen, but as you can see i wanted to help.

---

### Post by armandh on 2009-01-18
tool bar, right click, properties, auto-hide
keeps bar hidden until the pointer is at the edge

the full screen [windows] button works on most apps but not the desktop itself
try Oo writer

---

### Post by ArKay on 2009-01-19
> **Ancalagon82 said:**
> So my Mini9 came in today.  According to the Quick Reference Guide, the windows button is supposed to make a window go full screen.   However, mine is not working at all.  Not just in Firefox, but in any other window.  Considering the screen isn't huge to begin with, I need all of it!

Any ideas how to turn it on?
Are you running the Dell Installed Ubuntu or did you install 8.10 or some other variant on your own ?

If you haven't done much you might just restore it back to factory specs and see if the windows key works then. From my understanding it is hard coded in the Dell version, but none of the others.

I know it's not that much help - but it's all I got.

---

### Post by wenfei on 2009-01-22
> **Ancalagon82 said:**
> So my Mini9 came in today.  According to the Quick Reference Guide, the windows button is supposed to make a window go full screen.   However, mine is not working at all.  Not just in Firefox, but in any other window.  Considering the screen isn't huge to begin with, I need all of it!

Any ideas how to turn it on?
I have a similar problem. My Windows key was deactivated after I accepted a recent auto update(from Dell, I think) to the kernel. Did your button work at first and then stopped for some reason?

I saw a recent workaround to restore the function, but did not bookmark it. I will update as soon as I find it again.

---

### Post by Solange82200 on 2009-01-22
My windows button doesnt do anything when I press it either. If anyone finds a fix, please let us know....

---

### Post by n6mod on 2009-01-24
> **wenfei said:**
> I have a similar problem. My Windows key was deactivated after I accepted a recent auto update(from Dell, I think) to the kernel. Did your button work at first and then stopped for some reason?


It was the update to maximus:

maximus (0.4.2netbook0belmont1) hardy; urgency=low

  * Revert existing installations Super_L to <Ctrl><Alt>f

 -- Neil J. Patel <neil.patel@canonical.com>  Tue, 06 Jan 2009 11:47:32 +0000

Is Neil around here? Can anyone explain a) why this was done, or b) how to configure maximus? I can't find any docs at all on it.

(PS: On the subject of the last updates... why are my title bars red, and what made you think jamming the Y! crapware down my throat was a good idea?)

---

### Post by n6mod on 2009-01-24
Found it, sorta.

Fire up gconf-editor and change apps/maximus/binding from <Ctrl><Alt>F to Super_L

That works for exactly one restart. On that boot, the Windows (Super_L) key works, but if you go back into gconf-editor, the binding is set back to <Ctrl><Alt>F and a new 'reverted' key is set.

What's going on? Where's gconf for dummies? And why are my windows still red?

I tell ya... I specify Ubuntu for all the servers I'm responsible for (around 100 hosts), but this stuff is why I'm still using Macs on the desktop.

---

### Post by Ancalagon82 on 2009-01-24
Dag Gonnit!    Someone posted the fix (real simple, took like three clicks) in another thread, I did it, it worked, and now I've forgotten!   :(

---

### Post by n6mod on 2009-01-24
If you leave the reverted key set, then whatever is trying to force this change is happy, and the preference sticks.

---

### Post by ugm6hr on 2009-01-24
[http://ubuntuforums.org/showthread.php?p=6529628#post6529628](http://ubuntuforums.org/showthread.php?p=6529628#post6529628)

---

### Post by n6mod on 2009-01-24
> **ugm6hr said:**
> [http://ubuntuforums.org/showthread.php?p=6529628#post6529628](http://ubuntuforums.org/showthread.php?p=6529628#post6529628)

That's not what changed. If all you ever use is Firefox, then remapping the windows key to F11 is fine. But that's not what Maximus does, and not what the update changed.

If you actually want to revert things to pre-update condition, you need to make the changes in gconf-editor I mentioned in my previous posts.

I still haven't found the script that wants to hammer that preference, but I haven't picked apart the postinst scripts yet.

---

### Post by ugm6hr on 2009-01-24
> **n6mod said:**
> That's not what changed. If all you ever use is Firefox, then remapping the windows key to F11 is fine.

True, but it will resolve the issue for most users.

Other than FF, the only other commonly required full-screen application will be Totem / multimedia, which has its own built-in shortcut for fullscreen.  The only reason FF is a problem is the lack of an F11 shortcut with the default Mini 9 A00 BIOS.

I personally use a single top panel with autohide.

---

### Post by wenfei on 2009-02-02
I found it by accident!

From Desktop Goto:
System/preferences/keyboard shortcuts
select toggle fullscreen mode from the windows management section

...then press your Windows Key and it remaps it again.

It has been working for me for a while now and it survived a recent synaptics update.

Let me know if this works for you...


regards

---

### Post by Arndtwe on 2009-02-02
Like just posted... this really is a very simple solve. Go to System>Prefrences>Keyboard Shortcuts. Scroll down until at the the "window management" sub list (third from top, at least on my machine) find where it says "Toggle fullscreen mode" then click the right side of that line. Once it is selected, simply push the super button and that's it.

I noticed that I was having the same issue, did this, and now it is fixed.

---

### Post by mirach on 2009-02-02
> I found it by accident!

From Desktop Goto:
System/preferences/keyboard shortcuts
select toggle fullscreen mode from the windows management section

...then press your Windows Key and it remaps it again.

This fix works but it's not quite the same. It doesn't take Firefox all the way fullscreen like the xmodmap F11 does - The address bar and status bar still occupy valuable real estate...

Regards,

---

### Post by armandh on 2009-02-03
they are different things

the super button takes the app to full screen [OS function]
the F11 takes the firefox output to full screen [app function]

---

### Post by RichTJ99 on 2009-02-04
Thanks, that worked for me.

---

