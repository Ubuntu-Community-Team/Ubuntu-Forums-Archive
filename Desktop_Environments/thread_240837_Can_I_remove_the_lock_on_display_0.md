---
title: "Can I remove the lock on display 0?"
date: 2006-08-21
forum: Desktop Environments
---

### Post by earobinson on 2006-08-21
Can I remove the lock on display 0 so that the command Xvnc will run instead of giving the "Server is already active for display 0" error?

---

### Post by amohanty on 2006-08-21
Try:
> Xvnc :50

HTH
AM

---

### Post by earobinson on 2006-08-21
But that will show me display 50 I want to see display 0

---

### Post by amohanty on 2006-08-21
Couple of questions:

1. What are you trying to do here:
  - setup a vnc server?
  - connect to a vnc server?

2. Using the command I provided above sets up the vnc server to use display 50. This means that all clients will need to connect to <hostname>:50. 

Now to be fair I have never tried to init Xvnc on the same display as the Xserver, and I dont have access to my home machine, so I cant try it out. So I dont know if it can be done.

Now if you wanted a local application to use the VNC display look at the command line manual for the app. Most apps allow you to specify a display, for e.g.:
xterm -display:50 will fire up a xterm on the VNC server display.

You **dont** have to use 50 but I would suggest not using 0 becuase that's what your XServer is using. As I mentioned above, I havent tried to start VNC server on display 0 so it could be possible.

HTH
AM

---

### Post by earobinson on 2006-08-21
I understand that problem is I want you use 0 as an exercise

---

### Post by amohanty on 2006-08-21
Do you already have X running? If you do and you cannot launch Xvnc, it means that you cannot use Xvnc on the same display as X.

To do so, kill gdm, I think the key combo is (Ctrl-Alt-Backspace) or you could do a **sudo telinit 1** or a **sudo killall gdm**

Then at the command line launch Xvnc and try connecting to it with a client.

HTH
AM

---

