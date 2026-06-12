---
title: "Session freeze after login"
date: 2004-12-18
forum: Desktop Environments
---

### Post by hashimoto on 2004-12-18
Ladies and Gentlemen,

Obviously something has gone bad in my .metacity folder or saved session data. After logging in the splash screen stops at Metacity and nothing happens after that. The bad thing is that I have no idea what has caused the problem. Logging in with safe mode is ok, though. My .xsession-errors reports following:

Window manager warning: Failed to read saved session file /home/hannu/.metacity/sessions/1103365307-5137-3677352881.ms: Failed to open file '/home/hannu/.metacity/sessions/1103365307-5137-3677352881.ms': No such file or directory
The application 'gnome-session' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
ICE default IO error handler doing an exit(), pid = 4839, errno = 0

Anyway, your valuable help would be greatly appreciated! What can I do to fix this? I already renamed the .metacity folder but that didn't help. 

BR
Hashimoto

---

### Post by hashimoto on 2004-12-19
Oh never mind. Patience and a cup of coffee seemed to help: I tried to log in once again, left the PC there waiting in"frozen" state to get a cup of coffee. And voila, it logged in while I was away. Saved the new session and things work again.

BR
Hashimoto

---

### Post by theToolman on 2005-06-11
I had metacity stallign and take about 5 minutes to log in; turned out that my save session somehow included 2 copies of metacity loading, one a 'restart' type load and another standard.  They were both at the same boot priority order. (Cant remember what value, either 20 or 40..)

I think the multiple loading simultaneously was making it hang for ages.

Hope this helps for someone.

---

