---
title: "Gdm could not write to your authorization file"
date: 2008-12-16
forum: General Help
---

### Post by renkertd on 2008-12-16
I have ubuntu desktop 8.10 - got the following message after i put in my id and password :  GDM could not write to your authorization file.  I am not out of disk space - I can get into the system by doing the ctl alt f1 - and it lets me sign in as usual - but i cannot get in using the desktop because of the error i mentioned.  Can anyone tell me how to fix this ?  -  only thing i remember doing related to my user id was to increase some rights , which i saw posted on a forum or help guide.  Turned it off last night, and now this popped up.   Tks for your help .
renkertd - email [email]renkertd@juno.com[/email]  12/16/2008
ubuntuforums.org

---

### Post by Achetar on 2008-12-16
boot into recovery mode and drop to shell. Then do the following:

```

$ cd /home/<your username here>/
$ sudo rm .Xauthority
$ sudo chown -R <your username here>.<your username here> *

```

That should fix it. reboot (the command is sudo reboot) and try logging in again.

---

