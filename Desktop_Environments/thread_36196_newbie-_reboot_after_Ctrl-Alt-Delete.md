---
title: "newbie- reboot after Ctrl-Alt-Delete"
date: 2005-05-22
forum: Desktop Environments
---

### Post by darby on 2005-05-22
I`m learning slowly and after installing the Wacom stuff covered in another thread I tried to reboot using Ctrl-Alt-Delete. I get a message saying the X-server cannot restart, then a couple of screens showing me where the trouble lies,then a message saying the X-server is disabled and I should restart GDM when configured correctly.

The two screens showing where the trouble is don`t mean anything to me as there is no obvious fault.When I continue I enter username and password and then get to my normal login name peter@ubuntu.

Where do I go from here please?

---

### Post by testingubuntu on 2005-05-22
post the output of 

tail -40 /var/log/messages

---

### Post by darby on 2005-05-22
Thank you Sir for your prompt reply.

I entered your suggestion at the command prompt and got a pretty big page. How would I post that bearing in mind I`m running a dual boot with XP?

Thank you.

---

### Post by khc on 2005-05-22
It would probably be better to post your /var/log/Xorg.0.log

---

