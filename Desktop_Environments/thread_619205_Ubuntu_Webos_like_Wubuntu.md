---
title: "Ubuntu Webos like Wubuntu"
date: 2007-11-21
forum: Desktop Environments
---

### Post by ifezs001 on 2007-11-21
Hi All,


Could someone help me about the following question?

I would like to reach Ubuntu via HTTP or HTTPS.

HTTPS could be better. I would like to log in my ubuntu desktop like in windows with the mstsc web access.

I would like to use a totaly free software for that. 

Thanks

Ifezs

---

### Post by bingoUV on 2007-11-21
What do you mean by "reach"ing Ubuntu? And why must you use HTTP / HTTPS?

Thumb rule : when you want to use a protocol for some other purpose than what it was designed for, you must be thinking something wrong.

---

### Post by JetskiDude911 on 2007-11-21
It really sounds like you want VNC, which will allow you to access your Ubuntu desktop remotely. HTTP is for serving up web sites, not accessing the computer remotely. 

You could also use SSH to access your computer. 

Both a pretty simple to setup. To setup VNC access, go to System -> Preferences -> Remote Desktop. You can set it up from there. You can then use a VNC client to connect to the machine (just Google around to find one).

To gain SSH access, just open a terminal and type sudo apt-get install ssh openssh-server. You can then use Putty to access the machine from Windows.

---

### Post by ifezs001 on 2007-11-22
Hi,

I can reach my Ubuntu remotely, that is not an isssue.

The problem that I would like to reach it via Internet browser only.

Like for Windows the mstsc with IIS web server.

I would like the same. Like the NX server with web plugin, but I would like a totaly free
solution.

Kind Regards

---

