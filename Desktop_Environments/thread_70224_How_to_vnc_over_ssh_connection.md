---
title: "How to vnc over ssh connection?"
date: 2005-09-29
forum: Desktop Environments
---

### Post by Zikona on 2005-09-29
I have used this process succefully in fedora box using tightvnc. Steps I was taking were:


1. Opened Putty and checked “Allow agent forwarding"
2. Enabled X11 forwarding and assigned 1 for X display location
3. Enable "Local ports accept connection from other hosts"
4. Under Add new forwarded port: For the source port I enter 5801 and destination also 5801 and mark both as local and then click add.
5. Under Add new forwarded port: For the source port I enter 5901 and destination also 5901 and mark both as local and then click add.
6. I open ssh connection to ssh server and login in
7. Started vncsever by typing: vncserver -geometry 1200x800 :1
6. When I bring up IE in windows machine and type in [http://localhost:5801](http://localhost:5801) I see vnc connection


Now the problem I have is with Hoary 5.04. I have installed tight vnc and gnome desktop environment. When I establish vnc connection on same network without secure ssh connection everything works fine. The issue I have is to vnc my box over WAN. If I follow direction I decribed earlier I get an error message in IE stating: "The page cannot be displayed". When I type in [http://localhost:5901](http://localhost:5901) in IE then error message is: "RFB 003.003" ](*,) . Can somebody point me to what I might be doing wrong here? THxs in advance.

---

### Post by John.Michael.Kane on 2005-09-29
[http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html](http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html)
[http://martybugs.net/smoothwall/sshvnc.cgi](http://martybugs.net/smoothwall/sshvnc.cgi)
[http://www.realvnc.com/pipermail/vnc-list/2003-January/036707.html](http://www.realvnc.com/pipermail/vnc-list/2003-January/036707.html)
[http://www.trekweb.com/~jasonb/articles/vnc_ssh.shtml](http://www.trekweb.com/~jasonb/articles/vnc_ssh.shtml)

hope this helps

---

### Post by samson1978 on 2006-02-23
Fantastic. It works! What a great way to have a secure connection to your remote box. With using just putty and tight vnc. Cheers.

---

