---
title: "&lt;ctrl&gt;&lt;alt&gt;F1 - F8"
date: 2006-04-24
forum: Desktop Environments
---

### Post by steveneddy on 2006-04-24
I have a problem on the <ctrl><alt> F8 screen. It has crashed & I don't know how to restart the screen. It had stopped in the middle of restarting and is dead. I still have a usable screen on F7, and F1 is still logged on. 

Any help would be appreciated regarding this matter. I really just ned to know how to restart the F8 session, please.

This happenned when I was trying to get my xorg.conf file working for my video card working properly. Still not working BTW, but I have that question in another post.

Thanks, SE

---

### Post by henriquemaia on 2006-04-24
Does this helps?

on a terminal, type

**sudo xinit -- :1**

To kill it, press ctrl+alt+backspace while in it.

---

### Post by mannheim on 2006-04-24
I think that the F8 screen is only supposed to show the system messages from boot-up etc. (I'm not sure about this.) So, I don't think there is a console running on F8 that you can log in to. You've got:

F1 - F6     consoles for non-graphical login
F7            default screen used for graphical login
F8           system messages from boot time (?)
F9 - F12   screens available for other graphical login (other X sessions)

---

### Post by steveneddy on 2006-04-30
Pardon my ignorance, but how exactly do I get other X sessions going on F9-F12? I already have many desktop managers available to me at logon, but the option of having many X-sessions open at once sounds exciting. I have already, BTW, found good use of the ctrl-alt-F1/F6 screens. Thank you for sharing that with me mannheim.

---

