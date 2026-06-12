---
title: "Want a GUI on my desktop to see  remote Server.  Need advice."
date: 2009-04-04
forum: General Help
---

### Post by chong67 on 2009-04-04
I want to see my Ubuntu Server 8.10 using a GUI.

I have read the help section on a GUI for server, but I do not want to install the GUI on the server.  I have read this page:
[https://help.ubuntu.com/community/ServerGUI#X11%20Client%20Installation](https://help.ubuntu.com/community/ServerGUI#X11%20Client%20Installation)

I am confused about x11 client vs server installation.

My colleague told me you can install a Hummingbird software on your Window Desktop and see the remote server graphically.

Can someone point me to a tutorial?

Thanks for helping.

---

### Post by dusan.saiko on 2009-04-05
I do not give you a precise answer, but just to help you with X11 client/server:

- X11 client is an application, which connects to
- X11 server, which is a graphic environment where the application is painted.

I do not know what exactly you want to achieve and why, but Hummingbird seems some kind of quite commercial application which I would say is not needed at all.

- if you want to monitor your server graphically, you can use some software like Nagios or Cacti,

- or if you want to run graphical application from your server on your remote desktop (which I think I would consider as wrong approach), you could just connect to server using "ssh -Y" option and then just executing the graphic application like xclock. For this, you would need X server installed at your remote desktop, this is not problem for Linux/Unix, for Windows just use Cygwin - it comes with free X11 server as well.

well, good luck :-)

---

