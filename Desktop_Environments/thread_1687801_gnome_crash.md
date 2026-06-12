---
title: "gnome crash"
date: 2011-02-14
forum: Desktop Environments
---

### Post by vicious blue on 2011-02-14
Hi there
 
I'm a newbie in ubuntu, not an an expert on windows eighter, just trying to get out of microsoft monopoly. 
 
Last week I have installed Ubuntu 10.04 lts 64 bit on my laptop, via wubi. Though I was happly learning the basics of linux I had a crash today. My computer was running on batteries and it was dead. Due to lack of swap, it did not hybernate. When I tried to reboot, the splash screen appeared. As I enter user names password, instead of gnome an applet appears with instead of graphical interface. Since I lack script knowledge, I can unly type exit and return to previous splash screen. Recobver options didn't work eighter. What can I do?

---

### Post by thefasterblueone on 2011-02-14
Try typing: 

  ```
startx
```

---

### Post by vicious blue on 2011-02-15
> **thefasterblueone said:**
> Try typing: 

  ```
startx
```

 I did but the message was  x: user not authorized to run the X server, aborting  then, the screen returns to:    username@ubuntu:~$  So I tried to type su and the password. the reply was authirazation failture

---

### Post by Krytarik on 2011-02-17
Did you solve your issue in the meantime?

It seems like you logged into an "xterm" session instead of "GNOME". When you are at the login screen, enter or click at your name, then choose the respective "Session" option at the bottom.

---

