---
title: "Changing Window Managers from the cli"
date: 2007-03-23
forum: Desktop Effects &amp; Customization
---

### Post by nanoga on 2007-03-23
My desktop is my main environment, but there are often times when I want to vnc back to it from my laptop.  However, when beryl is running, the vnc connection is horrible in terms of lag.  As such, I'm looking for a way to change the current window manager from the cli when i'm ssh'd in. 

kwin --replace reports an error "cannot connect to X server", and when I try it sitting in front of the desktop, it starts to replace beryl, but is then killed (I'm assuming by beryl-manager).  Any ideas on how to do this?

---

### Post by olejorgen on 2007-03-23
Not sure if it'll work, but: [http://www.die.net/doc/linux/man/man1/beryl-manager.1.html](http://www.die.net/doc/linux/man/man1/beryl-manager.1.html)

So I'd try kill -s USR2 <beryl-manager pid>

---

### Post by nanoga on 2007-03-23
Thanks.  That works perfectly.   I'd seen that in the man page before, I guess I just didn't know how to send the USR2 signal to the process.  

Thanks again!

---

