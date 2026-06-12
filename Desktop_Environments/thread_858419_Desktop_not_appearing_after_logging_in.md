---
title: "Desktop not appearing after logging in"
date: 2008-07-13
forum: Desktop Environments
---

### Post by NewToLinuxAIR on 2008-07-13
Hi Folks

I am very new to Linux, and in need of help.

The problem I have is that after logging in my desktop is not appearing, I have no desktop icons, no tool bar and right click at all. The only thing I have is a cursor and the wall paper. 

I have not loaded anything on, I am not getting any error messages, logging in is as normal, and this has happened out of the blue.

Can anyone help me to rectify the problem so I can get going again and to tell me what has happened?

Thanks.

---

### Post by tech0007 on 2008-07-13
Ctrl-alt-F1 to open a console. Then login.

'sudo /etc/init.d/gdm stop'
'sudo /etc/init.d/gdm start'

(Use /etc/init.d/kdm if you have kubuntu.)

Then ctrl-alt-F7 to go back to X.

---

