---
title: "Ubuntu freezes after login"
date: 2005-10-12
forum: Desktop Environments
---

### Post by der_kaiser on 2005-10-12
I have  computers : a laptop Toshiba Satellite and a desktop PIV 3Ghz/512Mo/160Go , and both of them have the same problem : after entring the login and the password, Ubuntu freezes during almost 5 minutes, and after that continues to load applications normally.
I have a wireless network at home using static IP adresses.
Can anyone help me?

---

### Post by mlomker on 2005-10-12
That's really unusual.  You're running Hoary?  You're saying that you get to the graphical login (GDM) and after entering the password it takes 5 minutes to get to your desktop?

Try pressing Ctrl-Alt-F2 to get to another terminal and then log into it.  Run this:

```

top

```

That'll give you some memory and processor utilization information.  Maybe you'll be able to see something hogging your processor.

Ctrl-Alt-F7 switches you back to the desktop (or the great pause, as the case may be).

---

### Post by der_kaiser on 2005-10-12
The command "top" gives nothing interesting...
Yes I'm running Hoary (and very soon Breezy), and what's the most amazing is that's happening in both of the computers. That's why I was thinking of a network problem...

---

### Post by mlomker on 2005-10-12
> That's why I was thinking of a network problem...

Networking is done before you go graphical.  You could verify that network is working by using **ping** at a command prompt.

---

### Post by der_kaiser on 2005-10-13
The network is working perfectly, and I can access to Internet from the laptop using the desktop as a gateway..

---

