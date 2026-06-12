---
title: "Start program at logon for all users"
date: 2009-06-18
forum: General Help
---

### Post by elmosim2 on 2009-06-18
Is there a way I can set a program to startup when any user logs in.

I'm trying to use remastersys to create a live cd with opera starting up when the user logs in.
When I set it in Preferences -> Startup Applications it works fine until I make it into a live cd.  
Sorry for all this seemingly useless info but I wanted to get that out before people just tell me to use "Startup Applications"

---

### Post by jerrrys on 2009-06-18
this may be what your looking for

[http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=Kvf&num=30&newwindow=1&ei=VnE6SpveC5DgsQP9rJnSBQ&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=how+to+write+a+startup+script+ubuntu&spell=1](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=Kvf&num=30&newwindow=1&ei=VnE6SpveC5DgsQP9rJnSBQ&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=how+to+write+a+startup+script+ubuntu&spell=1)

---

### Post by geirha on 2009-06-18
When logging in graphically, all .desktop files under /etc/xdg/autostart and ~/.config/autostart/ are launched. So the ones under ~/.config/autostart (which is typically created by System -> Preferences -> Startup Applications) are only launched for the one user, while the ones under /etc/xdg/autostart are launched for all users.

---

### Post by elmosim2 on 2009-06-19
geirha, that was exactly what I needed.  
I created what I needed to in "Startup Applications" and then moved the entry from ~/.config/autostart/ to /etc/xdg/autostart and it worked perfectly.  

thanks!

---

