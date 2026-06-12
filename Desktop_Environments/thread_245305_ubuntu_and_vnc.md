---
title: "ubuntu and vnc"
date: 2006-08-27
forum: Desktop Environments
---

### Post by av05 on 2006-08-27
hi everyone,

i've set up ubuntu on an old box. 
i've checked the relevant boxes on Remote Desktop Preferences- and i'm able to login from my windwos box using a vnc client.
however, when the ubuntu box boots up, and there's no user logged in (it's just stays in the login screen prompts for a username) - i can't connect at that stage using the vnc viewer from my windows box.
any idea what should i do? is that related to xvnc in some way- or do i already have xvnc installed as part of the standard vnc server on ubuntu?

tnx, and sorry if this is a dump one :-)

---

### Post by atomkarinca on 2006-08-28
in order to login, vncserver must be running. this is what i do: i connect via ssh and run vncserver as root. then i can login via vnc. (or you could add vncserver to startup programs, i've never bothered trying that :) jeez i should do that!)

---

### Post by mod187 on 2006-08-28
I have mine set to auto log-in at start up. This allows vnc to work.

---

### Post by funchords on 2006-08-28
I followed this guide: 
[http://www.ubuntuforums.org/showthread.php?t=122402](http://www.ubuntuforums.org/showthread.php?t=122402)

---

