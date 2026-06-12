---
title: "login problemo"
date: 2009-04-28
forum: General Help
---

### Post by flyingsliverfin on 2009-04-28
ok...
when it loads the graphical login window, it says something like

user $HOME/.dmrc file is being ignored. The session could not be saved. The file should be owned by user and have 644 permissions. The $ HOME dir should be owned by the user.

after that it always boots me into the xubuntu desktop I have installed not the ubuntu one I like better. when  I change the setting back to GNOME, then it doesn't save it next time I boot up. 

I use Jaunty, but the problem started before I updated

---

### Post by amingv on 2009-04-29
Try doing what it's telling you:

Log in to XFCE, open a terminal and type:
```
sudo chown <yourUserName>:<yourUserName> /home/<yourUserName>/.dmrc
```

and then
```
chmod 644 /home/<yourUserName>/.dmrc
```

Of course, replace <yourUserName> for your actual username.

Pick gnome again as your default session, try to log in and see if it works.

---

### Post by flyingsliverfin on 2009-04-29
hm.... before we go there another problem just popped up at last boot (need to fix this before anything else)

as I reach the login screen I can't use the mouse or the keyboard. This is the 1st time happening. now im booting from my usb stick...

what logs should I check from the mem stick?

ill post this on a seperate thread too, this isn't the original problem

---

