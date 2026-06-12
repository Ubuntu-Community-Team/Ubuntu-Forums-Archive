---
title: "Forwarding X"
date: 2006-03-14
forum: Desktop Environments
---

### Post by f1dave on 2006-03-14
Hey guys and girls,

I'm trying to forward an X session from home to my university so I can access all my stuff graphically. Basically, my home setup is thus: my computer sits behind a dsl router with ports forwarded for ssh (works fine) and X11 (177, 6000-6100). Now the problem is I can ssh -X in ok, but when i echo $DISPLAY all I get is a blank line- it seems the display isn't being forwarded through. Checking sshd_config, ForwardX11 is set to yes. So what could possibly be going wrong?

Cheers for any help you can provide.

---

### Post by pasdar1 on 2006-05-15
Hello,

I have the same situation and get the same errors.  Any ideas???

---

