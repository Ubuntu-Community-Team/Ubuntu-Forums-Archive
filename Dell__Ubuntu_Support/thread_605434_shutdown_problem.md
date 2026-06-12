---
title: "shutdown problem"
date: 2007-11-07
forum: Dell  Ubuntu Support
---

### Post by vincentvee on 2007-11-07
running gutsy on my inspiron 1501, ever since the upgrde  from feisty i'm having an issue when shutting it down, shutdown starts OK but then leaves me with a black screen with some text on it, the only way to shutdown then is to force a "hard" shutdown - hoding power button down until it turns off, anyone have similar problem or know how to fix this :confused:

---

### Post by dacap06 on 2007-11-07
Apparently, no one else has seen the problem.  We need more information to figure out what to do.  Could you post the last 100 lines or so of /var/log/syslog and also of /var/log/messages?  The easy way to do that is in a terminal window:
[INDENT]
sudo tail -100 /var/log/messages > /tmp/last-messages
 sudo tail -100 /var/log/syslog > /tmp/last-syslog
 sudo chmod 644 /tmp/last-*
[/INDENT] 
Then you can includes the two files you just created in /tmp in your post.

DaCAP

---

