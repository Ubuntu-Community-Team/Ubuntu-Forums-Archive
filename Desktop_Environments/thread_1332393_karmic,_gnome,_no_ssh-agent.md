---
title: "karmic, gnome, no ssh-agent"
date: 2009-11-20
forum: Desktop Environments
---

### Post by schmadde on 2009-11-20
I updated my 9.04 installation to karmic recently. Since then, ssh-agent no longer gets started upon login. I found an Xsession in /etc/gdm that should start ssh-agent, but it does not seem to be executed. The Xsession in /etc/X11 has not mention of ssh-agent. 

Whats happening here? Is this a bug or do I need to reconfigure something so ssh-agent ist started upon login

---

### Post by ScarEye on 2009-11-20
bump, need ssh-agent for pssh

---

### Post by pbrane on 2009-11-20
I upgraded from 9.04 to 9.10 as well. I did a 'echo $SSH_AGENT_PID' in a terminal and got the PID of ssh-agent. So it must be running on my system. I'm not sure how to help you with yours, sorry.

---

### Post by ScarEye on 2009-11-20
Okay from what I understand ssh-agent is used by Xsession, What you need to do is when your in terminal type:

ssh-agent bash


now that bash session is running the agent and you should be able to do everything normally now.

Hope this helps some.


Thanks,
ScarEye

---

### Post by schmadde on 2009-11-21
I know how to start ssh-agent manually. But it is a nuisance to copy over the Environment variables in every shell window in order to make use of it Gnome Applications don't get to know anything about it either so e.g. sftp with Nautilus is out. Besides, it should not be started manually (it worked fine in 9.04).

It does seem to work on some systems (thanks pbrane) so it seems to be a bug indeed.

---

### Post by HDave on 2010-01-20
Any way to fix this?  It worked fine in 9.04.  Sheesh I am tired of these regressions...

---

