---
title: "Correct way of exporting variables at startup?"
date: 2005-12-09
forum: Desktop Environments
---

### Post by Bahamut on 2005-12-09
I want to export the environment variable GTK_IM_MODULE="im-ja" to make the jap input manager the standard one. I'm fairly new to linux and after seaching a bit I found out that when bash creates the login shell it executes /etc/profile, ~/.bash_profile and ~/.profile so i just thought I put 

export GTK_IM_MODULE="im-ja"

into /etc/profile

But that did not work so I tried to put it in ~/.bash_profile and ~/.profile

but that did not work either. I really feel stupid by now. Where can I put this simple export command to make it work?

Bahamut

---

### Post by amohanty on 2005-12-09
In your home folder create .gnomerc if it is not already there and put it in there.

HTH

---

