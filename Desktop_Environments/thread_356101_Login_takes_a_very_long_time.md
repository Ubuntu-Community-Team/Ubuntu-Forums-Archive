---
title: "Login takes a very long time"
date: 2007-02-08
forum: Desktop Environments
---

### Post by azruial on 2007-02-08
Hi, I am new to these forums, I switched from Windows XP to Fedora Core 5 over the summer.  Then I installed SuSE and got compiz and Xgl up and running.  I hated the package manager and that led me here for apt (which I love).  So hi everyone!

So my issue is that it takes over 2-3 minutes to go from the login screen to a working desktop.  I initially attributed this to Xgl, but I have done some experimenting and it actually takes just as long to load the straight-up Gnome session as it takes to load the Xgl session. What does load in a reasonable amount of time is the "failsafe gnome" session.  I don't really know much about this but I tried several 'speed up your login time' threads here without much success.  my /var/logs and dmesg are at [http://www.ccs.neu.edu/~brysons/docs]("http://www.ccs.neu.edu/~brysons/docs") and it would be great if you could give me some advice as to how I should continue in troubleshooting this problem.  I really don't know much about it and I am always looking to learn! :) 

Thanks in advance to anyone who has any advice,
 ~az

---

### Post by wolf08 on 2007-02-09
Since the gnome-failsafe loads quickly, I would assume that you have some problem with a program that starts on login. Check out 'System --> Preferences --> Sessions' and try messing (meaning enable, disable) some options in the startup programs tab.

---

### Post by azruial on 2007-02-09
Hi wolf08, thank you for your reply.  Unfortunately I tried that.  I did that first, then I found instructions on this forum for disabling even more software using sysv-rc-conf.  But I haven't found anything that seems to have any kind of significant effect.  I suspect that it may have to do with my network card because I have had issues with it before under fedora.  Also, I am connected to my university's network, so it may have trouble detecting things.  In those text files I thought I saw something about searching for some sort of router... I'm still looking at it.      It's just frustrating to try something and then have to wait 3-5 minutes to reload and find out if it worked. ](*,) 

At any rate, thanks for the reply, but no luck yet :(

~az

---

### Post by azruial on 2007-02-28
Still nothing here, tried disabling all startup apps and everything I could and the gnome session and xgl session still take around 4-6 mins to load.  Failsafe works great except of course no xgl... :confused: is there any way to make a new session that is just like the failsafe but then work on adding the xgl capabilities?

---

