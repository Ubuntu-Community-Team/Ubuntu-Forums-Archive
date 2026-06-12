---
title: "Why does sudo gedit just not run anything?"
date: 2007-06-17
forum: Desktop Environments
---

### Post by doccpu on 2007-06-17
I am trying to use my machine by setting up samba files and edit stuff but root is not allowed and users can't change anything. So how can i even set up samba and stuff via the gui. I got sudo gedit to work a few times now it just returns but never actually runs gedit in roots privs. 
Whats the point of running linux gui if you cant get anything done on your own machine?
[email]dhorner@usa.net[/email]

---

### Post by smartboyathome on 2007-06-17
Try gksudo gedit. gksudo gives you a graphical sudo, it is the one you are supposed to use if you want anything graphically root.

---

### Post by spock84 on 2007-06-17
> **smartboyathome said:**
> Try gksudo gedit. gksudo gives you a graphical sudo, it is the one you are supposed to use if you want anything graphically root.

That's just stupid. gksudo is just a GUI for sudo. sudo should do just fine.

As for why gedit apparently doesn't run, I have no idea. Aren't there any error messages in the terminal? Are there any gedit processes running? Are there other apps that won't run?

---

### Post by mcduck on 2007-06-17
> **spock84 said:**
> That's just stupid. gksudo is just a GUI for sudo. sudo should do just fine.

As for why gedit apparently doesn't run, I have no idea. Aren't there any error messages in the terminal? Are there any gedit processes running? Are there other apps that won't run?

No, sudo is only made for command-line use, and it doesn't work correctly with all GUI applications. In worst case running a GUI app with sudo instead of gksudo results in problems like changing your setting file's ownerships to root, making it impossible for you to log in to your graphical desktop.

Always use gksudo with GUI applications!

---

