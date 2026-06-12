---
title: "Titlebar not loading!"
date: 2007-03-19
forum: Desktop Environments
---

### Post by Spectre5 on 2007-03-19
Hey everyone,

I am pretty new to Ubuntu and Linux in general.  I have Xubuntu 6.10 installed and it has been working fine.  However, without changing any settings or doing anything differently, I have a weird problem.

I was using linux normally and then restart my computer.  It restarts fine and the login window appears as normal.  After logging in, it shows a blue screen, but never loads the background image or the toolbars.  Interestingly, everything is still loaded (i.e. I can switch between workspaces with the scroll of a mouse, but right click does nothing).  The mouse moves, but cannot right click.  I can hit alt+F2 to open a command prompt.  But the titlebar and background never load.

Interestingly....if I press ctrl+alt+del to lock the computer (go into screensaver), then I goto "New Login" (which brings me back to the login page), then enter my name and password again to re-login...and everything loads and works fine!  (It gives a msg saying I am already logged in, but I tell it to continue anyways).

How weird is that!  I have no idea why this is happening!

Any help would be greatly appreciated.

-Scott

PS:  I have another problem....when I open OPenOffice stuff, the title bar is all messed up!  ONLY openoffice stuff does this, not any other applications.  Just something that is annoying and weird (it was messed up when I had Xubuntu 6.06 installed too).

---

### Post by Spectre5 on 2007-03-19
I have a little more news.....it seems that it is "stuck" in some login.  When I load and sign-in and get the blue screen....I can still swtich workspaces as I mentioned before.  On one of them is a command shell, and another is the Thundar file manager.  The other two are blank.  These are what was last on the screen when I rebooted.  I tried restarting via the terminal and logging out via the terminal, but this same setup still loads each time!  It even loads if I select a new session when logging in.

But as I mentioned before, I can always get to the normal desktop by doing another login.

---

### Post by Spectre5 on 2007-03-19
I figured it out!

Just in case anyone else has this problem, to fix it I just deleted the xfce session log stuff, it can be found here:

~/.cache/sessions

---

### Post by battra on 2007-06-07
Thanks so much for posting the solution.  I had the exact same problem and this fixed it.   :D

---

