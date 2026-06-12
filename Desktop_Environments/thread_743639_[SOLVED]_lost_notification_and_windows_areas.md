---
title: "[SOLVED] lost notification and windows areas"
date: 2008-04-02
forum: Desktop Environments
---

### Post by mike g on 2008-04-02
I have lost both the notification area with all it's menus and ability to get to the terminal.  I have also lost the windows area at the bottom of the screen with all it's related items.  I have the desktop screen and "shortcuts" still intact.  The mouse works and I am able to both right and left click as well as use the wheel.  I am able to open the system, home etc shortcuts on the desktop.

I am running xubuntu 7.10 on an old HP Pavilion.

The system was working correctly when I shut it off but when I turned it back on the top and bottom areas were missing.  I have tried clicking on various areas of the screen in hopes the bars got hidden somehow but no luck.

How do I get back the missing areas?  I am able to get into the safe terminal mode, which does not look correct either, it is small and in the lower right corner of the screen with the scroll bar missing.

Please Help!!!!!!!!!

---

### Post by chewearn on 2008-04-03
Here are some ideas; it worked for me once:

1. Press ALT+F2 to bring up the Run dialog, then run: "xfce4-panel". This will bring back the panel.

2. Go to: Applications > Settings > Settings Manager > Desktop; enable the checkbox "Allow Xfce to manage the desktop". This will bring back the desktop and background picture.

3. Delete everything under ~/.cache/sessions

4. Go to: Applications > Settings > Settings Manager > Sessions and startup; enable the checkbox "Prompt on logout"

5. Restart.

---

### Post by Guitar John on 2008-04-12
My problem seems to be a little more difficult.  The only way I can get everything back is to log into "Failsafe Terminal" or something like that. Then type into the terminal ```
xfce4-panel
```

 Then following AstalaVista's instructions:

> 

2. Go to: Applications > Settings > Settings Manager > Desktop; enable the checkbox "Allow Xfce to manage the desktop".
This does bring back the desktop and background picture.

The problem is that I cannot logout.  My only option is "Exit Xfce Panel.  

When I do that, it only exits the panel, it doesn't Restart, Shut-Down or anything else.  If I shut off the computer using the power button, I'm back to square one.  

Any ideas?

EDIT:  I enabled Right click menu, and went to "Quit".  I got:
```
**Unable to quit session**

Quitting the session requires that Xfce's session manager
 (xfce-session) is running, but it was not detected.  Please 
quit Xfce via another means.
```

---

### Post by bithkits on 2008-06-12
Thanks AstalaVista, it worked great for me!

---

