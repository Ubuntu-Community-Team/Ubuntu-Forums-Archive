---
title: "Login Screen Missing???"
date: 2008-02-23
forum: Desktop Environments
---

### Post by turqoisehex on 2008-02-23
Hi Everyone,

I'm a long time Ubuntu user, but just recently made it my daily use OS

I'm running 7.10 on a Asus G2 laptop

When I log in, I don't get any login screen, it just goes straight to the desktop. :confused:

This is the same whether I reboot, cold boot or resume from hibernate. I couldn't find anything like this and I have no idea what could have caused it. 
When I boot, I get the orange screen, I hear the login music, the screen dims for a moment, then it goes to my desktop.

Any suggestions are much appreciated as this is a pretty major security issue. Thanks!!!

EDIT:

Ctrl+Alt+BkSpace, DOES bring up my login screen. Weiirdd!

---

### Post by aidanr on 2008-02-23
In a terminal:
```
gksudo gdmsetup
```
Go to the Security tab and make sure "Enable Automatic Login" is unchecked.

---

### Post by turqoisehex on 2008-02-24
:popcorn:

Well, I feel silly. Thank you very much for pointing that out to me, I set it a few days ago and completely forgot about it. At the time, I assumed that it would put in my username and still prompt for the password. Thanks again!

---

