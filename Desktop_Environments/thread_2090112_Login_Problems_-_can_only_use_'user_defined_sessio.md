---
title: "Login Problems - can only use 'user defined session' or 'recovery console'"
date: 2012-12-01
forum: Desktop Environments
---

### Post by roswell1211 on 2012-12-01
Hi,
I've posted on here before and recieved great help so I'm hoping someone can help me today.
I have no idea what I did to cause the problem below, but any info I haven't provided just let me know.

I don't often fully reboot my machine (I do often suspend it though). Today I rebooted and when I get back to the login screen I cannot log into Ubuntu normally.
My user only has two log in options (recovery console and user defined session). I haven't deliberately defined a session - because I don't know what I'm doing :-)
When I try to log in with user defined session the login screen just hangs.
When I try to log in with another user/guest session nothing happens. 
I have tried logging into the recovery console and after searching the forums tried :
sudo service lightdm stop
sudo mv ~/.Xauthority ~/.Xauthority.old
sudo reboot now

This made no difference.
Ideally, what I want is for an option to log in with the ubuntu logo next to my user name again (the way I've always been logging in in the past).

I have looked online and cannot see any solutions for my problem - any ideas?

---

