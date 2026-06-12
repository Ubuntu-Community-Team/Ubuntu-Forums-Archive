---
title: "lost terminal session and got this when I tried again"
date: 2009-02-03
forum: General Help
---

### Post by hoosiergsp on 2009-02-03
I was trying to set grub to have an indefinite timeout. I lost my terminal window, when I opened a new terminal session and went to sudo to edit the grub menu I got this:

E325: ATTENTION
Found a swap file by the name "/boot/grub/.menu.lst.swp"
          owned by: root   dated: Tue Feb  3 10:24:45 2009
         file name: /boot/grub/menu.lst
          modified: YES
         user name: root   host name: hoosiergsp-desktop
        process ID: 5764
While opening file "/boot/grub/menu.lst"
             dated: Mon Feb  2 13:55:36 2009

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /boot/grub/menu.lst"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/boot/grub/.menu.lst.swp"
    to avoid this message.
"/boot/grub/menu.lst" 168 lines, 5107 characters
Press ENTER or type command to continue

Is there a reversal or solution to fix this?
I would like to eventually have grub with no timeout between boot up to operating systems (vista/ubuntu). This is a simple task and I don't know what I did to foul this one. As always, help appreciated.

---

### Post by cariboo on 2009-02-03
The answer is right in the error message:

> 2) An edit session for this file crashed.
If this is the case, use **":recover" or "vim -r /boot/grub/menu.lst"**
to recover the changes (see ":help recovery").
If you did this already, **delete the swap file "/boot/grub/.menu.lst.swp"**
to avoid this message.
"/boot/grub/menu.lst" 168 lines, 5107 characters
Press ENTER or type command to continue

I would do as suggested. There is a gui app to edit /boot/grub/menu.lst called startupmanager, that is in the repositories.

Jim

---

