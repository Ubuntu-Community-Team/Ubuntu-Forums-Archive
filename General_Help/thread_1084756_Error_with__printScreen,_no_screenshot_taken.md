---
title: "Error with  printScreen, no screenshot taken"
date: 2009-03-02
forum: General Help
---

### Post by Biochem on 2009-03-02
I need to take a lot of screen shot for a workshop I'll give next week. The problem is, my screenshot shortcut doesn't work. I always get the following message.
> There was an error running "/usr/share/compiz/take-screenshot.sh":
Failed to execute child process "/usr/share/compiz/take-screenshot.sh" (No such file or directory).

I did removed compiz once but I reinstalled it when I notice that error. But, it didn't solve the problem.

On the other hand, the screen shot application (in Accessories) still work, as seen in the attached picture of the error message. It is just that it is much slower to get it manually than to just press print screen. 

Can someone please tell me how to modifie the action  of the keyboard shortcut or send me a copy of the missing script (ubuntu 8.10).

Thank you,
Biochem

---

### Post by Biochem on 2009-03-02
OK I managed to fix it by editing the gnome configuration editor.

/apps/metacity/keybinding_commands/command_window_screenshot

---

