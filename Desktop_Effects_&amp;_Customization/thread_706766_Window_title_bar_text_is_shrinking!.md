---
title: "Window title bar text is shrinking!"
date: 2008-02-24
forum: Desktop Effects &amp; Customization
---

### Post by memps001 on 2008-02-24
The text in my window title bars is entirely too small to read.  I searched through some forums, and found that many people ran this code and fixed their problem: compiz -replace.  When I run this line, it fixes the problem temporarily, but the terminal hangs, it won't return to the prompt line.  This is what it says:

```
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
Starting emerald
/usr/bin/compiz.real (core) - Warn: Unknown option '-replace'

/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

And then when I close Terminal, the title bars disappear completely!  They return if I log out and back in, but the text remains really really tiny (practically just a line).  How can I return the text size back to normal?

Some other relevant info:
I'm using Ubuntu Gutsy
The nvidia driver I have installed (according to Synaptic) is "nvidia-glx-new" & "nvidia-kernel-common"
I have Emerald Theme Manager installed (an attempted fix from another thread)

---

### Post by russo.mic on 2008-02-25
That is normal.  When you run a process in the terminal, it doesn't return to the prompt until the process is finished.  When you close the terminal, you close any program that has been called by that terminal.

Press Ctrl+F2 to call a run dialog, and then type compiz-replace.  that will run compiz without a terminal.  

Also, to start it at login, go to System, Preferences, Sessions, and add it to the start up list. 

Good Luck!

Russo

---

### Post by memps001 on 2008-02-25
Yeah! Awesome, that totally did it!  However rather than open a run dialog like you suggested (ctrl+f2 didn't do anything on my desktop), I created a launcher that would run the code when I clicked it.

So now my window titles are back, but I'm wondering how long it'll last.  You suggested that I put it in my startup items, but that seems like it's just a workaround.  But then again, maybe I shouldn't look a gift horse.

While we're talking title bars, I think I may have a problem with this Emerald Theme Manager.  When I select a theme that I've imported, nothing happens.  In order to change the theme I have to select it, log out, and log in again.  I don't think this is right, is it?  Shouldn't it change instantly?  If you've got any advice or any leads I'd appreciate it.  And thanks again!

---

