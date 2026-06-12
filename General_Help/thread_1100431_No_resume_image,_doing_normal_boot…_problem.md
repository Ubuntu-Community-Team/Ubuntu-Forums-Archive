---
title: "No resume image, doing normal boot… problem"
date: 2009-03-19
forum: General Help
---

### Post by roimekoi on 2009-03-19
Got a problem, 
When i away from keyboard without using the computer for a while the ubuntu freezes, then after i reboot, i got this error message.
<blah>
No resume image, doing normal boot…
</blah>

i tried 3 method...
[http://www.mattcutts.com/blog/ubuntu-freeze-no-resume-image/](http://www.mattcutts.com/blog/ubuntu-freeze-no-resume-image/)
and
[http://ubuntuforums.org/showthread.php?t=636268#post3922624](http://ubuntuforums.org/showthread.php?t=636268#post3922624)

[http://ubuntuforums.org/showthread.php?t=422875](http://ubuntuforums.org/showthread.php?t=422875)

The message disappear but now every time i reboot my comp,
It will boot into TTY(ubuntu terminal) asking me login name and password.. even after i entered the correct thing im still in the TTY screen.

How to resume back to the normal GUI ubuntu? I am sorry about my broken English.

---

### Post by user_ex3 on 2009-04-30
I had the same issue.  I tried serveral things until I finally just reinstalled the desktop, etc...  works great now.   
 
 
try:  sudo apt-get install --reinstall ubuntu-desktop

---

