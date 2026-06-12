---
title: "Ways to make your computer _completly_ remotely accessible"
date: 2008-10-14
forum: Desktop Environments
---

### Post by Pyro.699 on 2008-10-14
Hello,

I was wondering what the best method/application that would allow a user such as myself to have complete remote access to a desktop computer or laptop. I know all about **putty** and **vnc **but i would like to know if there are any other applications out there that allow *linux to windows* communication. On windows there are programs like *Real VNC *and *Anyplace Control* but they are incompatiable with linux (atleast *Anyplace Control*is). Not to long ago i tried to get the builtin VNC (on ubuntu) to work and the only ip i can connect to is **127.0.0.1** which seems kind of redundant. Ive seen serveral tutorials on this site and the ubuntu manuals that explain exactly how to get it setup, but this question is more aimed towards the idea of having a computer dedicated solely to being controlled remotely.

Another question, is there an operating system (preferably a distribution of linux) that specializes in this kind of situation, that is, an operating system dedicated to being controlled remotely.

Thanks
~Cody Woolaver

---

### Post by Mazin on 2008-10-14
All VNC programs should be compatible with each other on the basic level.  That means Real VNC should be able to connect to Ubuntu, and vice-versa.  VNC is probably the best way to go.

If you want to remotely control your Ubuntu computer, go to System&#8594;Preferences&#8594;Remote Desktop preferences and:

check Allow others to view and control your desktop
uncheck Ask for confirmation
check Ask for password (to be safe)

In advanced tab:

uncheck Only allow local connections
uncheck Require encryption


Then try connecting with Real VNC to your Ubuntu computer's IP address.

---

### Post by Mazin on 2008-10-14
Something cool you can do with Linux and Macs (or anything with an X server actually) is that you can forward X windows.  This means that you can run a program on the server, but have its window appear on your computer like it's local.

To use it, run ```
ssh -X user@yourserver
``` on your Linux or Mac client and then try running something like "gedit" or "xeyes".

I use my desktop remotely from my laptop quite often, but usually I just open a remote shell with ssh (use PuTTy on windows); I don't usually need graphical programs, but if I do, I just use X forwarding.

---

### Post by Pyro.699 on 2008-10-14
So, the easiest thing would be to just use putty and foreward the x server to that?

---

### Post by Mazin on 2008-10-14
Problem is, you probably don't have an X server running on Windows.  You can, however, get a text prompt with Putty.  If you do want to try X forwarding with Windows, you can check out [Cygwin]("http://www.cygwin.com"), which provides a full Unix environment (including X) on Windows.

Otherwise, VNC works.

---

### Post by Pyro.699 on 2008-10-14
Is there a way to install a fully functional X server in windows, aside from using cygwin?
Also, i just tried to connect to **127.0.0.1** with the Remote Desktope Viewer and it said the port isn't open.

Is there an operating system dedicated to this kind of operation? I'm rarely going to be near this computer and want to be able to control every aspect of it from afar.

Another question i have is if there is a http way to control a computer?

Thanks
~Cody Woolaver

---

### Post by Mazin on 2008-10-16
SSH is the canonical method of remotely-using computers.  Usually computers that are only going to be controlled remotely aren't graphical.  think headless servers, etc.

```
sudo apt-get install openssh-server openssh-client
```

and then you can use any ssh client (e.g. Putty) to login to your computer and get a command line:

```
mazin@lulz:~$ ssh toast.local
mazin@toast.local's password: 
Linux toast 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
Last login: Thu Oct 16 14:18:53 2008 from localhost
mazin@toast:~$  fortune
Q:	How many Zen masters does it take to screw in a light bulb?
A:	None.  The Universe spins the bulb, and the Zen master stays out
	of the way.
mazin@toast:~$ 

```

If you're using Ubuntu on both computers, you can use remote login (although I've never done this).  In System Administration&#8594;Login window&#8594;Remote, set Style to Same as Local.  And then, with another Ubuntu computer on the network, on your login window go to Options and choose Remote Login. There's tons of ways to use Ubuntu remotely;  after all, Unix was commonly used as big time-sharing mainframes where many dumb terminals connected to the central server.

For graphics, you have the choice of VNC, X-forwarding, etc., but who needs those silly graphics anyways? :p

---

### Post by Pyro.699 on 2008-10-16
Thanks for that information it was quite helpful and i can now login using ssh. (Just localhost, i will try using ip's when i get home).

---

