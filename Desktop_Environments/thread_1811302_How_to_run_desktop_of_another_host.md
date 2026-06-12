---
title: "How to run desktop of another host?"
date: 2011-07-24
forum: Desktop Environments
---

### Post by ratcheer on 2011-07-24
The short form of my question: Can I log into a remote host from a local host (on the same LAN) and get the full GUI desktop environment of the remote host?

Long form of question: I worked for years on Solaris hosts with the CDE environment. Our server hosts were in another physical location. My desktop machine was another Sun Solaris host which also ran CDE. At the CDE login screen, I could click a dropdown menu and tell it to login to one of the server hosts at the remote location. In my login script on the remote machine, I had "export DISPLAY=localhostname:0.0", where localhostname was the hostname of my desktop host. There was also some kind of security command that had to be in the login script to allow the windows to be sent to another host, but unfortunately, I cannot remember what that command is.

What I want to do is configure another host on my LAN, but without a mouse, keyboard, and display monitor. I would like to run the GUI desktop of the new host on my current main host, just like I did at work. Is this possible in Ubuntu with Gnome?

Thank you,
Tim

---

### Post by ratcheer on 2011-07-24
Ok, I remembered the security command. It just popped into my head. It is either "xhost +" or, more likely "xhosts +". I am going to Google it, but it is only a part or the question/answer.

The question I am asking is about a standard feature of X-Windows, which I am pretty sure Ubuntu uses in some form or fashion. Does anyone know how to do it in Ubuntu?

Tim

---

### Post by ratcheer on 2011-07-24
Never mind. I have learned that doing this is highly insecure.

Tim

---

### Post by brian70809 on 2011-07-25
you can do this through an ssh shell.  

here is a link...

[https://help.ubuntu.com/community/VNC?action=show&redirect=VNCOverSSH](https://help.ubuntu.com/community/VNC?action=show&redirect=VNCOverSSH)

The only problem I have been having with some of these variations, is it's creating a separate xserver session, so i am not accessing some things.  I am not sure how to select a different instance..

good luck!

---

### Post by ratcheer on 2011-07-25
Thanks, Brian. If I can determine a more secure way to do it, my hope is that all I will have to do is turn the spare machine on and plug it into the ethernet switch. It wouldn't even have to take up any desk space.

Tim

---

### Post by cybergalvez on 2011-07-25
> **ratcheer said:**
> Thanks, Brian. If I can determine a more secure way to do it, my hope is that all I will have to do is turn the spare machine on and plug it into the ethernet switch. It wouldn't even have to take up and desk space.

Tim

use x2go

---

### Post by enimeizoo on 2011-07-25
In case it helps, "ssh -X" allows you to run graphical apps from the remote machine. You can open a X server on your machine, and run ssh -X to launch the desktop environment of the other machine.

It is just as secure as ssh is.

(edit) all you need is to have a sshd running on the remote machine, allowing X forwarding (and it is the default option). You don't even need to have a session open on the remote computer, it just needs to be turned on and booted.

---

### Post by 1clue on 2011-07-25
There are 2 possible vulnerabilities I know of.

One is the unencrypted data the X session passes back and forth, which is taken care of by the ssh session.

The other is the xhost +whatever command, which should be exactly the host you're dealing with rather than a different host.

Otherwise, I don't think it's any less secure than Terminal Services for Windows using a similar mode.

---

### Post by ratcheer on 2011-07-26
> **enimeizoo said:**
> In case it helps, "ssh -X" allows you to run graphical apps from the remote machine. You can open a X server on your machine, and run ssh -X to launch the desktop environment of the other machine.

It is just as secure as ssh is.

(edit) all you need is to have a sshd running on the remote machine, allowing X forwarding (and it is the default option). You don't even need to have a session open on the remote computer, it just needs to be turned on and booted.

Excellent info. Thanks.

Tim

---

