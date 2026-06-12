---
title: "remote GUI login"
date: 2005-10-08
forum: Desktop Environments
---

### Post by Zelut on 2005-10-08
can someone tell me how I can login remotely thru the GUI?  Right now I've been using ssh access as my remote doorway but there are a few things I'd like to do with the GUI.  I can use vnc but I am reliant on the other users settings/accnt.

Thanks in advance

---

### Post by mlomker on 2005-10-08
> I can use vnc but I am reliant on the other users settings/accnt.


VNC is the modern way to do it.  I suppose you could use an old-school Xterminal of some kind, but I'd stick with VNC.

---

### Post by Zwack on 2005-10-08
It depends on what you have available...

VNC is one option.

If the other machine has an X server on it then you can either do an xdmcp login (so you're running remotely but displaying locally) or you can tunnel X through SSH.

If the other machine is a windows machine you might want to look into cygwin as a free X Server.

If it is a Unix/Linux box then try the X-terminal howto (if it still exists)

I hope that this helps.

Z.

---

### Post by Zelut on 2005-10-08
The other computer is another Breezy box so I'm assuming it has X server.  So how would I remotely pull up the GUI login prompt?  for vnc I'd use vncviewer IP, but that pulls up the remote desktop session...

---

### Post by mlomker on 2005-10-08
I'm not sure what your objectives are here, but VNC can be run as a daemon on the machine.  It isn't dependent upon the user's settings.  [The how-to is here.]("http://ubuntuforums.org/showthread.php?t=42941")

---

### Post by theidealist on 2005-10-12
Yeah that how-to is currently broken with Breezy, considering it relies on inetd, which Breezy (apparently) has none of by default.  After apt-getting it (inetd) as well as following the other directions set forth in the how-to, still no dice - any suggestions?  I would post this there, but figured I would set to work on the problem myself, then if I found a solution I'd post it there.

Thanks,

-Patrick

---

### Post by mlomker on 2005-10-12
I've never done it, so I don't have specific information.  I can give you [another lead]("http://gentoo-wiki.com/HOWTO_Xvnc_terminal_server"), though.

---

### Post by wylfing on 2005-10-12
Don't go messing with inetd if you don't have to. It's a security nightmare.

Have you tried the obvious? Choose System > Preferences > Remote Desktop.

---

### Post by Zwack on 2005-10-17
Offhand, I'm assuming that you don't want to use VNC for some reason.

In that case, GDM configuration is where you want to go.  You'll probably need to configure both machines though.

System -> Administration -> Login Screen Setup...

Under Security you probably want to add "Show Actions Menu" and "Allow Running XDMCP Chooser from the login screen".  You will also need to switch to "Greeter: Local -> Standard Greeter" on the General tab.  If you don't you won't get the Actions Menu. This is only needed on the machine that you want to use as a client (i.e. sit in front of)

Under XDMCP select "Enable XDMCP" and make sure that you are allowing sessions.  This is only needed on the machine that you want to connect to.

Then you should be able to log out on the "client" and select Actions on the login screen  and there should be a chooser option.  That will allow you to choose which machine to connect to.  Select the appropriate machine and log in...

Good luck.

Z.

---

