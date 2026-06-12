---
title: "Random logouts"
date: 2010-11-09
forum: Desktop Environments
---

### Post by w1ll1am on 2010-11-09
I would first like to say that I stated using Ubuntu with the 9.04 release and I think that it has progressively gotten worse since then. 

anyway I have Ubuntu 10.10 64bit and I have reinstalled five times in the last week I finally thought I got everything working well and then this crap started happening.

I am in college and I use a program called JES (jython environment for students) and when i am using it sometimes I get randomly logged out and everything is lost. I had the same problem with an earlier install this week using Firefox I believe that is has something to do with Java because both programs use it and I was on a graphical site every time it happened. 

I have ubuntu 10.10 installed on a netbook that i use also and the same program(JES) installed and this does not happen?

any help would be great thanks.

---

### Post by mahmoodn on 2010-11-10
I have the same problem with ubuntu 10.10 amd64 desktop. After some normal work, I see that the screen goes black and after some seconds, the login window appears. I don't know how can I find the problem with logs. Is it xorg, kernel, daemon, ....

---

### Post by w1ll1am on 2010-11-10
> **w1ll1am said:**
> I would first like to say that I stated using Ubuntu with the 9.04 release and I think that it has progressively gotten worse since then. 

anyway I have Ubuntu 10.10 64bit and I have reinstalled five times in the last week I finally thought I got everything working well and then this crap started happening.

I am in college and I use a program called JES (jython environment for students) and when i am using it sometimes I get randomly logged out and everything is lost. I had the same problem with an earlier install this week using Firefox I believe that is has something to do with Java because both programs use it and I was on a graphical site every time it happened. 

I have ubuntu 10.10 installed on a netbook that i use also and the same program(JES) installed and this does not happen?

any help would be great thanks.

What program are you using when it happens?

---

### Post by mahmoodn on 2010-11-10
I can not point to a specific application. During normal use for example firefox or nautilus) this happens. Since it is random it is very hard to track

---

### Post by w1ll1am on 2010-11-10
> **mahmoodn said:**
> I can not point to a specific application. During normal use for example firefox or nautilus) this happens. Since it is random it is very hard to track

It is really annoying me I think that it has something to do with java that is the only thing that both Firefox and the program I was using both use. I have not had the problem today and i just did an upgrade so I will post back in a few days if the problem has not happened and assume that the upgrade has fixed it.

---

### Post by kerplunkx on 2010-11-11
Same problem on my sisters computer - it happens with or without a browser open and appears to be random.  

Ubuntu 10.10 (64bit)

---

### Post by w1ll1am on 2010-11-16
This has still not happened to me again I guess the update fixed it I will post back if it happens again if anyone else is still experiencing this even after an update keep posting and maybe someone will find a fix

---

### Post by Shwazy on 2010-11-16
This exact issue has been happening with me as well. Ubuntu desktop, 64 bit here. My computer has been periodically freezing for a half a second or so, then dropping me to GDM. My session is not suspended, it is terminated when this happens, causing me to lose any unsaved documents. It is extremely annoying.

EDIT: Ok, it just happened again, and I have noticed a pattern. Every time it has happened to me so far, it has been while resizing the qbittorrent window. I have no idea what this means, really. Perhaps it's a bug in QT4? Does qbittorrent use any java?

I'm at a loss.

---

### Post by Shwazy on 2010-11-16
EDIT: how do i delete a post here?

---

### Post by soldier1st on 2010-11-16
i encountered this issue with another user but it only happened when running a wine app and when a screensaver launched automatically in 10.10 32bit but it does not happen in 10.04.1 but i suspect that it was the gpu not being very well supported in 10.10 but in 10.04.1 this does not happen so i would check your hardware and see if it is well supported or not.

---

### Post by w1ll1am on 2010-11-17
Well it is happening again now it happens when I open VirtualBox I do not think that it is my hardware I am using a sparkle graphics card which uses nVidia GPU and I have the restricted drivers installed. This is kind of annoying because I was using virtaulBox last week to put music on my iphone with itunes under windows xp and now as soon as it opens I get logged out. Whats the deal?

---

### Post by w1ll1am on 2010-11-17
I decided to set up dual monitors today and started having this problem again with VirtualBox and with totem. 

if i had it set up so the second monitor was a separate x screen and i had Xinerama enabled I would get logged out.

if I did not have Xinerama enabled it would not happen but you can't drag one window to another screen with it disabled.

if i have it set to TwinView all the problems go away and everything works fine.

I am not sure what the issue is but it is working for me now that I have the dual monitors set to TwinView.

Hope this can help someone figure out the problem.

---

### Post by mahmoodn on 2010-12-21
I have found this line at the time of logout in system logs:

X server for display :0 terminated unexpectedly

Any idea about that?

---

