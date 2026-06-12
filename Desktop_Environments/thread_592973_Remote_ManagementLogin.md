---
title: "Remote Management/Login"
date: 2007-10-26
forum: Desktop Environments
---

### Post by GoldEmish on 2007-10-26
Hello everybody,
I would like to set up a Remote Management on my server. Actually I have just SSH access through Putty, but i want to setup it to allow me a complete desktop access (vnc).

I tried the Putty SSH-Tunnel with 5900 port, but it doesn't work (It tells me "Connection Close"), maybe because the remote login is not enabled and my server has no user logged...

But how to enable the remote login just with the shell?

Thank you all

---

### Post by GoldEmish on 2007-10-28
no answers? :confused:

---

### Post by GoldEmish on 2007-10-29
please, nobody can help me?
How to enable remote Login?
I tried to edit /etc/gdm/gdm.conf enabling RemoteGreeter e XDMCP, but it is enought? Seems not...

---

### Post by bingoUV on 2007-10-29
I may have understood your question incorrectly, please bear with me.
Do you want a graphical remote login? Why do you not use vncserver?

If you want encrypted connection, NX ([http://nomachine.com](http://nomachine.com)) is your friend. It feels faster than vnc, but some people feel it has issues of incorrect rendering.

---

### Post by GoldEmish on 2007-10-29
thanks for your reply,
I already use the vino as vnc server, but i can connet to the remote machine only if there is an already logged user in that machine.
(with the login screen in the remote machine i get a "Closed Connection" by thightvnc)

I want login from remote, can I do it with standard vino in ubuntu?

Thank you

---

### Post by bingoUV on 2007-10-30
I do not know anything about vino, but linux has a dozen ways for remote connection, graphical or otherwise. I will tell you about my favourite way. 

Install ssh server (search in synaptic, I think ubuntu has a common package for ssh client and server). Then install NX server from [http://nomachine.com](http://nomachine.com). Now, as long as the ssh server is running, you can connect from any computer(the graphical goodness is tunnelled over ssh). Clients are available for most operating systems I have heard of.


The client can specify what it wants to run. Like, you may just want to run gnome-terminal(my favourite is mrxvt, but never mind). If you open any other window from this terminal, it will also show properly. Using the same server, different clients can run different programs.

But I guess what you are looking at is a full desktop. While connecting from the client, you can specify that too(gnome-session / startkde).

Hope this solves your problem.

---

### Post by GoldEmish on 2007-10-30
Thanks, i will try NX, but it is free?

---

### Post by bingoUV on 2007-10-30
yes, free as in beer. If you want free as in freedom, look for freeNX . From what I have heard freeNX works acceptably, only some features of the NX protocol have been left unimplemented.

---

### Post by timcredible on 2007-10-30
for a how-to on remote login using XDM (the linux/unix standard), please see [http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=1](http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=1)

---

### Post by vikrant82 on 2007-10-30
Try this, 

```
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true
```

You might also consider enabling autologin for a user.

---

### Post by GoldEmish on 2007-10-30
thank you everybody.

vikrant82, i alredy tried it, but in vnc i can not login.

bingoUV, i successfully installed the nx server of nomachine, but seems to be free.. what I miss?

---

### Post by bingoUV on 2007-10-30
> **GoldEmish said:**
> thank you everybody.

vikrant82, i alredy tried it, but in vnc i can not login.

bingoUV, i successfully installed the nx server of nomachine, but seems to be free.. what I miss?

I told you it is free. You do not miss anything. Does it resolve your problem?

---

### Post by GoldEmish on 2007-10-30
Yes, of course, seems to be good!

Sorry, but i read "Free **as** a beer" (Sounds like a joke!) :lolflag:

Thank you very much

---

### Post by daflame on 2007-11-18
If anyone is interested, I have Ubuntu packages for a working version of FreeNX  0.7.1.  Everything is quite good with only a config file change you can have unlimited sessions on your machine and RDP proxy using rdesktop.  The free version of !M server only allows 2 sessions max.  I have found this to be limiting at times.  Especially if you are trying to setup a server.  Plus it runs with the latest NX 3.0 backend and client.  I have working versions compiled for gutsy on x86_64 and i386.  If anyone needs other dist packages, please let me know and I'll start a VM to build one.

---

