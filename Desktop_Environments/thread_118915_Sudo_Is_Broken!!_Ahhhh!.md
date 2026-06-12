---
title: "Sudo Is Broken!! Ahhhh!"
date: 2006-01-18
forum: Desktop Environments
---

### Post by shade11 on 2006-01-18
I have have edited my /etc/sudoers file. It turns out that I accidentally typed something wrong. So now I cant use use sudo anymore. Or synaptic or anything elso you have to use in sudo. I NEED HELP AHHHHH! I need to find a way to be able to edit it again to fix the error I made so I can get it to work again.
Please help!

---

### Post by kaamos on 2006-01-18
Boot in recovery mode (just choose that in grubs menu) to get root access and edit the file with the command "visudo". The sudoers file should never me edited directly because visudo checks for errors and typos..

---

### Post by shade11 on 2006-01-18
Gonna try it out. I dont think it was a typo. Maybe a worng command.

---

### Post by shade11 on 2006-01-18
Whew. Thanks a bunch.

I cant thank the people at Ubuntu forums enough. I get help from everyone for noobish questions like mine.:mrgreen:

---

