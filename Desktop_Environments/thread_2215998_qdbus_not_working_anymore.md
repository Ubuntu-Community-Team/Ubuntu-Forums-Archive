---
title: "qdbus not working anymore"
date: 2014-04-09
forum: Desktop Environments
---

### Post by lennard3 on 2014-04-09
hello people,

I had a kubuntu system running until something called qdbus stopped working. when i boot up and try to login i get the message:* can you call qdbus? *and when i press alt+F1 to do so I get another error. could someone tell me what is going on and help me out?

---

### Post by marco-parillo on 2014-04-09
Could it be this bug:

[https://bugs.launchpad.net/ubuntu/+source/kde-workspace/+bug/1304805](https://bugs.launchpad.net/ubuntu/+source/kde-workspace/+bug/1304805)

If so, and if you are getting this with today's updates to 14.04, you might have a quicker response in the [U+1 forum]("http://ubuntuforums.org/forumdisplay.php?f=427").

---

### Post by su:bhatta on 2014-04-10
Yes, if it is a 14.04 install, I was getting the same yesterday. 
A small window that says, 'cannot call DBus, can you call qdbus' or something like that.

But it went away after upgrading. 
Yes, the launchpad page says : 'Fix released'. So an upgrade should help you.

Assuming you have only 1 session,that of KDE, try using Ctrl+Alt+F1 and go to tty1.

Login with your usual user ID and Password (password will not show, just type and hit enter)
Once you are logged in run:

```
sudo apt-get updte
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
```

Then you can restart LightDM and get back to the login screen.
See if that helps.

---

