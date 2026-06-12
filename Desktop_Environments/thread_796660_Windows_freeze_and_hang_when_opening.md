---
title: "Windows freeze and hang when opening"
date: 2008-05-16
forum: Desktop Environments
---

### Post by Thirtysixway on 2008-05-16
Out of the blue, I'll go to open terminal or text editor, or any other application not already open, and the window will come up and freeze.

Example, for terminal the Window will have the word "Terminal" as the title, and the File Edit View Terminal menus won't be there, and the scroll bar is missing.  Then after a few seconds it goes gray and I have to force quit.

When restarting I can't open up the logout window, so I need to press ctrl+alt+shift+backspace to get to the login screen and click reboot, sometimes it freezes and I have to hardboot.

Does anyone know what's going on?:confused:  It's pretty frustrating and is the only real issue I've had with Ubuntu lately.  It's an 8.04 Desktop Wubi install.

---

### Post by hermes0710 on 2008-05-16
I suppose you have compiz enabled. Disable it to see if it's a display issue. (System>preferences>appearance and in the last tab select none)

---

### Post by sfnationalist on 2008-06-02
The exact same thing happens to me without Wubi. I have Hardy installed on my hard drive the conventional way, though. Usually these instant application freezes don't start happening until my machine has been up for a  few hours, though. The problem also happens regardless if Compiz is on or not, which irks me to no end. It's tough when you can't get debug info because your terminal emulator won't load.

---

### Post by jazzgossen on 2008-06-02
I've had similar problems, that were caused by overheating. Try adding the sensors panel applet to monitor your temperatures, and see if there is any correspondence.

---

