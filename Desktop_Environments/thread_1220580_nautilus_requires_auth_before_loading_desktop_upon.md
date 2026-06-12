---
title: "nautilus requires auth before loading desktop upon login"
date: 2009-07-23
forum: Desktop Environments
---

### Post by musikgoat on 2009-07-23
I'm trying to identify an odd error that I can only assume has cropped up from an upgrade from intrepid to jaunty.

When I log in to my account, I am immediately prompted to input my password as nautilus requires elevated privileges.  Once I log in, the /root directory is opened in nautilus and also icons from my desktop appear.

If I do not login (click cancel), the desktop icons do not show up at all.  If I were to open a nautilus browser from the command line, the desktop environment shows up (as well as a nautilus window, this time in my ~ directory).  I get some warning messages but I believe they are irrelevant:

```
tim@Central:~/Desktop$ nautilus

** (nautilus:7153): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: unknown format for key 'tim - home/usershare_acl' as it contains 'Everyone:R,'.  Assuming that the share is read-only
Nautilus-Share-Message: unknown format for key 'central - downloads/usershare_acl' as it contains 'Everyone:R,'.  Assuming that the share is read-only
^C

```

If I were to close that nautilus window, I do not loose the desktop icons, until I kill the process. 

My Desktop and my home folder have the correct permissions (owned by me and read/write by me), so what I believe to be the case is that gnome has somehow setup nautilus to start either with sudo or root privileges.

I have been scouring the web for similar reports and I cannot find anything that matches with the problem I have.

Let me know if there is any information I can grab from the system to troubleshoot this further.


-Tim

---

### Post by musikgoat on 2009-07-24
Anyone come across this before?

---

### Post by jopes on 2009-07-30
I've got a similar problem. Where my my desktop is unclickable, and no icons show up. I tracked down a potential solution here:
[http://ubuntuforums.org/showthread.php?t=71469]("http://ubuntuforums.org/showthread.php?t=71469").

But there is a problem for me in that solution, i cannot get into: System > Preferences > Sessions as that menu does not exist for my current user. :confused:

---

