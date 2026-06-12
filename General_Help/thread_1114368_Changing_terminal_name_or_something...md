---
title: "Changing terminal name or something.."
date: 2009-04-02
forum: General Help
---

### Post by The Shin on 2009-04-02
Hey, I'm just a ubuntu newbie that just got back with it a few days ago. And I'm wondering how can I change my terminal name thing.. It also says example on ubuntu, how do I change the name ubuntu?

Heres what I mean-

[IMG]http://i44.tinypic.com/24b0y1d.png[/IMG]

---

### Post by Mehashi on 2009-04-02
It should be [your username]@[your computers name] so if you change the name for your pc it would change in the terminal.
^_^

---

### Post by mister_pink on 2009-04-02
Its the hostname of your computer. You need to change it in two places - open both files for editing at the same time with "gksudo gedit" then save them both. They must match or you might break sudo, hense opening them both at the same time.

The files are:
/etc/hostname
/etc/hosts

Hopefully someone else will be able to tell you the straightforward GUI way to do this, unfortunately I can't  remember or check right now!

---

### Post by change_mode on 2009-04-02
If you're using 8.04, the nm-applet can do this ;)

Click on the network icon and change your host name.

---

### Post by _Purple_ on 2009-04-02
You can change it from System> Administration> Network. Click [here](https://help.ubuntu.com/8.10/internet/C/networking-changecompname.html) for details.

---

### Post by coffeeaddict22 on 2009-04-02
Lots of options available.  Have a look here for some ideas.
[http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html]("http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html")

---

