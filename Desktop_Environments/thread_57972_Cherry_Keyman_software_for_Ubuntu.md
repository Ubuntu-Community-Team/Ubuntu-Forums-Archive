---
title: "Cherry Keyman software for Ubuntu?"
date: 2005-08-18
forum: Desktop Environments
---

### Post by kamiccolo on 2005-08-18
I have an Cherry CyMotion keyboard with many multimedia- and browsing-keys on it. These don't work with Linux normally. Cherry says, it works with SuSE Linux. And when it works there, then it could work ob any distribution. Has anyone an idea how I can get it work?

---

### Post by craigevil on 2005-08-18
Hm I was thinking about buying one of those keyboards. Do they have software you can download?

 A list of all valid keyboard symbols can be found in
# /usr/include/X11/keysym.h, keysymdefs.h, XF86keysym.h

"Multimedia key" bindings for XFree86. Gather the keycodes of your
# advanced function keys by watching the output of the xev command whilest
# pressing those keys and map those symbols by using xmodmap or
 try using xbindkeys and/or xev to set up the keys.

Of course Xorg may be a little different. But the same process should still apply.


If for some reason you do not have the software it is available at [http://support.cherry.de/download/KeyMan_LINUX_06.zip](http://support.cherry.de/download/KeyMan_LINUX_06.zip)

Looks like it is source so you will have to complie it. From what I can gather loking at other posts in other forums you might need KDE to install/run it.

Here is a good like with a basic HOWto:
[CyMotion Linux Cherry Keyboard](http://www.jumpstation.co.uk/linux/cymotion/)

An interesting thread at LQ.org [LinuxQuestions.org - Cherry CyMotion keyboard software - where Linux users come for help](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=270896&perpage=15&pagenumber=1)

---

### Post by kamiccolo on 2005-08-18
These links are great, but they are about the Linux-version of my keyboard. Mine is originally made for Windows and Mac OS. I buyed it in a time when I still used Windows. And now it's difficult to get these extra keys work under Ubuntu and formerlly Fedora.

---

### Post by fredricsolstad on 2006-02-17
Umm.. since I am a complete beginner when it comes to compiling and such, can someone give me some really _basic_ instructions on how to do it? 

I have a Cherry CyMotion Linux, I've created a group called keyman and given myself full access to it. I've also downloaded all the software for Debian from the cherry website. 

And what do I do next and how do I do it? 

(I tried to follow the instructions, but the directories that they talk about in the instructions doesn't exist for me. I'm running Ubuntu 5.10)

---

