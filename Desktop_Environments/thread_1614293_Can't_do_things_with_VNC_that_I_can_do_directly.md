---
title: "Can't do things with VNC that I can do directly?"
date: 2010-11-05
forum: Desktop Environments
---

### Post by SwarfEye on 2010-11-05
Hey,

I'm not sure if this is the right place to ask this question, but it seemed more appropriate than in the Networking forum.  If I should move this thread, please let me know.

So, I've been working on a couple of projects that involve a "headless" ubuntu box that I access via VNC.  I'm running 10.04LTS and for the time being, the box has also got it's "head" on... in large part because of this issue.

Basically, when I log in directly I am able to mount usb hard drives no problem, but when I log in through VNC, I am not authorized.

I'm logged in as the same user in both cases, and i start the vncserver as that same user.

What am I running up against here?

Thanks,

Bill

---

### Post by SwarfEye on 2010-11-06
Ok, 

I haven't gotten a single response on this, so I'm hoping to kick it back up to the top of the list.

Any thoughts would be appreciated.  Anyone know of a forum that is VNC specific?

Thanks,

Bill

---

### Post by G0lg0thaZA on 2010-12-12
Hey SwarfEye

Did you ever get a solution for this?

I have the same issue, I can mount manually via CLI, but this is not ideal - I also have to copy files then using sudo on the CLI as I do not have sufficient rights as the user.

If you did not find a solution... at least we can bump this question to the top again ;-)

Thanx

---

### Post by templewulf on 2011-01-20
I have a similar problem. I have x11vnc starting in /etc/gdm/Init/Default, and I can connect to it from the login screen.  However, when I try to log in, it tells me "Authentication failed". When I connect my keyboard, mouse and monitor directly, I can log in just fine.  Any ideas?

---

