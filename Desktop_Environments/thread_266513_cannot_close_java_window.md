---
title: "cannot close java window"
date: 2006-09-27
forum: Desktop Environments
---

### Post by kimstebel on 2006-09-27
Hello everybody,

i'm having a problem with java. I installed jre 1.5.0_06 and the plugin for firefox 1.5.0.7. Everything works fine except i can't close a java applet window by clicking X or by clicking the upper left corner and choosing close(if i try, nothing happens). If the programm itself does not provide a way to close the window, i cannot close the window at all (except by reloading the page). This renders at least one java app i often use unusable. The same problem occurs with Opera 9, so it's probably not a browser issue.
Any help would REALLY be appreciated...:(
thx in advance
kim

---

### Post by arneh on 2006-10-09
I have the same problem over here! does anybody how to solve this problem??

Arne

---

### Post by s_p_a_r_k_y on 2006-10-09
I have programmed some java apps before and I'm pretty sure that the java developer can catch a close window request and ignore it...perhaps something else must be completed to grant the request?

---

### Post by Medieval_Creations on 2006-10-09
if you type the command 'xkill' in a terminal, it should change the mouse pointer to a skull & cross bones... then just click on the window you want closed and it should kill that process for you.

That hopefully will work for a temporary fix to close the windows.

---

### Post by linuxgeekery on 2006-10-09
If that doesn't work, fire up a terminal and do 'sudo kill -9 `pidof java`'. (Without the single quotes, but with the backticks) That should do the trick, although it kills the whole java runtime.

---

### Post by kimstebel on 2006-10-16
Thanks for your replies so far and sorry i didn't respond earlier. unfortunately your replies do not solve my problem. :(

> I have programmed some java apps before and I'm pretty sure that the java developer can catch a close window request and ignore it...perhaps something else must be completed to grant the request?
Yes, the programmer could ignore the close request, but he doesn't in my case. I hate to say it, but: it works fine on windows...

> if you type the command 'xkill' in a terminal, it should change the mouse pointer to a skull & cross bones... then just click on the window you want closed and it should kill that process for you.
I do not want to kill the whole process, I just want to close one of its windows. :( i'm aware of the kill command. thx anyway

maybe it's a problem with the window manager and how it interacts with the jvm?? any ideas? please!

---

### Post by arneh on 2006-11-05
Still nobody knows how to fix this problem?? 

A sample application with the window problem can be found at:

 [www.volano.com](www.volano.com)

cheers

---

