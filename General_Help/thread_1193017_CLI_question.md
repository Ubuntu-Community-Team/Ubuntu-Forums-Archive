---
title: "CLI question"
date: 2009-06-21
forum: General Help
---

### Post by ffxigotenks on 2009-06-21
I connect to my computer over telnet (i know about the security issues, but have no choice) and I'm moving a large amount of data from one drive to another, I was wondering if it was possible to monitor the progress from another computer. for example I start moving the files on computer A from computer B using telnet, then I move and can only access computer A from computer C, is there a way to echo the display on computer B. hope I didn't confuse anyone

---

### Post by jordan420 on 2009-06-21
im not really sure.. i know that ksysguard can monitor disk and network activity from any computer on the network. i dont know if you could use something that would tell you exactly how much of the job is done on another computer. i would suggest you just use ksysguard or another program that supports network monitoring and just do the math.. im pretty sure it can tell you how much data has passed since the beginning of the session.

---

### Post by lloyd_b on 2009-06-21
> **ffxigotenks said:**
> I connect to my computer over telnet (i know about the security issues, but have no choice) and I'm moving a large amount of data from one drive to another, I was wondering if it was possible to monitor the progress from another computer. for example I start moving the files on computer A from computer B using telnet, then I move and can only access computer A from computer C, is there a way to echo the display on computer B. hope I didn't confuse anyone

Take a look at the "screen" utility.  It will allow you to start a process (from computer B in your example), "detach" from the session (with the copy process still running), then connect from computer C and "reattach" to that session.  

"sudo apt-get install screen" (or use the package manager of your choice) to install it, then "man screen" in a terminal window for info on using it.

Lloyd B.

---

