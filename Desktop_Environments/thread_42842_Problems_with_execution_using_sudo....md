---
title: "Problems with execution using sudo..."
date: 2005-06-19
forum: Desktop Environments
---

### Post by iammike on 2005-06-19
Sorry if this has been covered but trying to search for things related to sudo is pulling up everything under the sun.  haha

I'm trying to use wifi-radar and the program is working fine for me now after some good tweaking and such.

My problem is this, the program requires sudo to run and it runs from command line so I have these problems.

1.  If I have the icon set to NOT run it through the terminal I never see anything, no prompt for password, no anything.

2.  If I tell it to run in the terminal I'll get the prompt for the sudo password in the term window but it's kinda annoying to have it open a term window and the wifi-radar window every time.

I guess it isn't a BIG deal but I was wondering if there is a way to get around the password prompt or to make it prompt for the password like Synaptic or Update Manager do.

---

### Post by cwaldbieser on 2005-06-19
Try looking into the commands gksu, gksudo, gksuexec.  The man pages explain then pretty thoroughly.  For KDE, there is kdesu.  These commands bring up a GUI front-end for asking for passwords.

---

