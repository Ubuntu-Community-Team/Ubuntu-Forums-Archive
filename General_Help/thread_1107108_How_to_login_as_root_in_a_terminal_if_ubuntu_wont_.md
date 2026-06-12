---
title: "How to login as root in a terminal if ubuntu wont load the correct graphics driver?"
date: 2009-03-26
forum: General Help
---

### Post by KCG102282 on 2009-03-26
As I mentioned in an earlier post I installed Ubuntu 8.04.2 LTS 64-bit edition, but when I rebotted after the install it would boot, but I can't see anything. So what I am wanting to do is edit my xorg.conf file, but how do you login to a termianl at start up instead of going to a gui?

---

### Post by SuperSonic4 on 2009-03-26
ctrl+alt+F2 will take you to the terminal. From there you can either use ```
sudo su -
``` (i think) or just use sudo as normal. For example 
```
sudo nano /etc/X11/xorg.conf
```

---

### Post by coffeecat on 2009-03-26
I presume you mean that the xserver is crashing and that you're being dumped into the command line. First of all, read this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Once you've thoroughly understood that :wink: log in to the command line as yourself, and then:

```
sudo nano -w /etc/X11/xorg.conf
```

After you've made your changes, the key commands are at the bottom - ctrl-O to save changes, and ctrl-X to exit.

---

### Post by oldos2er on 2009-03-26
> **KCG102282 said:**
> As I mentioned in an earlier post I installed Ubuntu 8.04.2 LTS 64-bit edition, but when I rebotted after the install it would boot, but I can't see anything. So what I am wanting to do is edit my xorg.conf file, but how do you login to a termianl at start up instead of going to a gui?

 Boot into recovery mode, and when the menu comes up, run xfix.

---

### Post by KCG102282 on 2009-03-26
Thanks guys I got it and now I am running it without he LiveCD :)

---

