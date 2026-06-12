---
title: "Xforwarding between to Ubuntu Machines"
date: 2006-03-10
forum: Desktop Environments
---

### Post by underwater on 2006-03-10
Hello,  

I'm just trying to do some xForwarding between my Ubuntu laptop and a desktop machine that I have on the lan.  I keep running into two problems, however.

The first is right after I logon after I ssh -X into the box

I get the error message
/usr/bin/xauth:  /home/myname/.Xauthority not writable, changes will be ignored

then if I try to launch a program like say xterm
X11 connection rejected because of wrong authentication.
X connection to localhost:10.0 broken (explicit kill or server shutdown).


So I'm thinking it is a simple authentication problem, but for the LIFE of me I can't find where.  Xforwarding is set to yes in my sshd config  There are no firewalls or anything like that....  

I've googled around and although there are other people who have gotten this problem, their problem doesn't seem to be my problem at all.  

Is there some simple step that I'm missing that other peopel know about?

---

### Post by cwaldbieser on 2006-03-11
[QUOTE=underwater]Hello,  

I'm just trying to do some xForwarding between my Ubuntu laptop and a desktop machine that I have on the lan.  I keep running into two problems, however.

The first is right after I logon after I ssh -X into the box

I get the error message
/usr/bin/xauth:  /home/myname/.Xauthority not writable, changes will be ignored

then if I try to launch a program like say xterm
X11 connection rejected because of wrong authentication.
X connection to localhost:10.0 broken (explicit kill or server shutdown).


So I'm thinking it is a simple authentication problem, but for the LIFE of me I can't find where.  Xforwarding is set to yes in my sshd config  There are no firewalls or anything like that....  

I've googled around and although there are other people who have gotten this problem, their problem doesn't seem to be my problem at all.  

Is there some simple step that I'm missing that other peopel know about?[/QUOTE]
I think there is some XDMCP setting in the gnome login dialog.  I also think that using the -Y option instead of -X might allow you to bypass the problem as well.

---

