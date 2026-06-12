---
title: "X11 forwarding"
date: 2010-03-17
forum: Desktop Environments
---

### Post by jmsgz on 2010-03-17
hi folks


question 1
   i cannot forward X11 from desktop to desktop via ssh or putty although both services including nautilus work well otherwise.....can you point me to where i can get info to fix? Gnome is installed on both machines. 

question 2
   what minimum services would i need on a ubuntu server to use nautilus to move files to from desktop?

jmsgz :-)

---

### Post by hictio on 2010-03-18
question 1:
If I understand correctly what you are trying to do...
How are you connecting (via SSH) to the server you want to export the Nautilus to? With what options?
You have to do this, from Machine A (has to have a working X Server running), connect to Machine B via SSH, like this:

```

ssh -X -l user machineB

```

The '-X' takes care of doing all the export display for you. Once connected to Machine B, test that you can export X11 programs using a small one, like xeyes, type:

```

xeyes &

```

If everything worked Ok, you'll have to have Xeyes running on the desktop of Machine A.

Question 2:
Again, if I understand you correctly, if you connect via SSH to a Linux server using Nautilus, you don't need that Nautilus installed on the server you are connecting to.
Think of the same thing as if you were using Nautilus to connect to a Windows share, you don't need Nautilus installed on the Windows box, not explorer.exe on the Linux one.

---

### Post by loboc on 2010-03-18
nautilus and gedit both have good integration for scp for working with remote files. 

If you need other programs over the ssh -X tunnel I wouldnt use nautilus as my window manager because it is big and if you dont pass the correct flag (-nodesktop i think) it will draw the desktop background. 

If you have both boxes on your home network and are have root on both you could look into setting up xdmcp for remote sessions.  with out the encryption of ssh they should be faster, and its the original feature of X11 that made it X11.

---

