---
title: "Question about xrdp and ehcp"
date: 2008-07-18
forum: Desktop Environments
---

### Post by PhillipJr89 on 2008-07-18
Sorry, but I didn't know a good place to ask this, but I had some questions about some things. The first question is about xrdp and why it doesn't seem to move if a windows pc connects to it. The next question is that I was wondering if there is a way to configure the server or xrdp to accept connections from windows in a similiar fashion to Windows where you can log into a session to an individual user rather than having to log into an open session. The last question I have is in regard to the ehcp's ftp user control. I am basically wondering if there is a way to just control the ftp users and give them all access to the same folder rather than give them each individual ftp folders. Thank you for any help, and sorry if this post comes as incoherant to some.

---

### Post by PhillipJr89 on 2008-07-25
bump

---

### Post by tjandracom on 2008-08-02
you must connect with the x11rdp, not with xvnc. 

but you must first built the X11rdp binary from the source. (it is a separate file not included in the xrdp package, and never been mentioned anywhere that this file is very important). then you must copy the file (X11rdp) to /usr/bin and set the permission so others could execute the file. the hardest part is building the X11rdp binary from the source, because it seems there's no other easy way to get it.

try this:

[http://www.linuxquestions.org/questions/linux-server-73/xrdp-authenticates-but-does-not-load-x-server-rdp-592138/](http://www.linuxquestions.org/questions/linux-server-73/xrdp-authenticates-but-does-not-load-x-server-rdp-592138/)

after all that, each user can connect individually and have their own session, as Windows Terminal Server does, from any Linux or Windows client. the only disadvantage is that the xrdp is much slower than Windows Terminal Server (you must have 100Mbps connection at minimum, while in Windows 10 Mbps is sufficient).

---

