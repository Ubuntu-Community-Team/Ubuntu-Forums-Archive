---
title: "trying new desktop environments"
date: 2018-07-14
forum: Desktop Environments
---

### Post by Skaperen on 2018-07-14
having read that Unity (which i currently use) will not be the default DE in some coming version of Ubuntu, and that Gnome will be, i decided it might be a good idea to try out some others to get an idea what i might want to choose in a future Ubuntu.  my current plan is to not upgrade to 18.04 LTS and wait until a while after 20.04 LTS is out.  i am using 16.04 LTS now.

i regularly run multiple users and switch among them using the drop down menu in the far upper right corner.  what i have found is that multiple users is using multiple X servers.  so i am thinking that it could be possible for different users i log in to to run different Desktop Environments.  there are 3 issues i need to clear up before i realize this can be possible.

1.  can a single user easily switch from Unity to another DE (such as Gnome or Xfce) so that each time they login, that DE will start up?

2.  is there a menu in these other DEs (such as Lxde or Gnome) that switches among logged in users like the one at the far upper right corner in Unity?  a DE that can't switch user has to be crossed off my list.  but i don't even want to try it on one user because then i would be stuck there.

3.  how compatible with VNC are these various DEs?  the main point i am seen trying to run them in cloud instances is that they (the DEs) were not very understanding of being started after X was already running.

---

### Post by TheFu on 2018-07-14
It is best to test different DEs using temporary userids to avoid any conflicts that DEs made from the same underlying libraries might cause.  Once you pick a DE, it is best to stay with it on that userid because the settings are storage in the userid's HOME.  You can, of course, clean/delete/remove/move up the settings and change DEs as much as you like, but finding exactly where each setting for the hundreds of different programs is stored is a complex task.

The login manager for each DE has a "gear" icon somewhere on the login page.  If you click that, it will show the installed DEs and often the installed window managers from which you can choose.  I would logoff between DE changes, not just switch users, but it might work fine.  Definitely no need to reboot between these changes.

VNC doesn't work well(or at all) with any graphics tool that demands direct access to the GPU.  Gnome3, Unity, KDE would be poor choices for use with any remote desktop.  Actually, if you want a remote desktop running elsewhere, take a look at x2go. It feels 2-3x faster than any VNC-based solution.  People who have switched from VNC to x2go say it is like comparing night and day. If you do use VNC, please only use it with a point-to-point VPN or ssh-tunnel.   VNC protocol is not secure.   x2go is based on NX, which includes the ssh tunnel already. Your ssh credentials and only the existing ssh port need be open between the client and server.  Use the x2go PPA to install the server and client.

---

### Post by saderror256 on 2018-07-16
> 1.  can a single user easily switch from Unity to another DE (such as  Gnome or Xfce) so that each time they login, that DE will start up?
yes, click the gear, or the ubuntu icon in your user login

> 2.  is there a menu in these other DEs (such as Lxde or Gnome) that  switches among logged in users like the one at the far upper right  corner in Unity?  a DE that can't switch user has to be crossed off my  list.  but i don't even want to try it on one user because then i would  be stuck there.
This is dependent on the DE you are using, but most likely, the answer is **yes**

> 3.  how compatible with VNC are these various DEs?  the main point i am  seen trying to run them in cloud instances is that they (the DEs) were  not very understanding of being started after X was already running.
most likely they all are compatible correctly, but VNC should work with an interface

---

### Post by Skaperen on 2018-07-18
an alternative i was considering was to try DEs in VMs.  but i thought i might want to give some of them a more serious try.  or i can try them on cloud instances.  that was what i wanted to use VNC for (cloud based desktops).  i will have a look at x2go for that.  ssh to them will typically be running, anyway, so the keys will all be set up.  but i do not want to be opening the windows of the apps running on the cloud instances as that would just be using the local DE.

i use an obscure alternate sshd port to eliminate the log file noise of kiddies trying common weak passwords (no doubt with enough successes elsewhere for them to keep that going).  i wonder if NX can deal with that.

the problem i encountered with VNC was that X was already up and running and the DEs i was trying (Cinnamon and Mate) complained that they were unable to start X.  apparently the way people have done remote desktops has been to run a program that scrapes X using the remote host graphics hardware (so X and the DE was already started in the usual way before the VNC connection).  what i got curious about is how those DEs would work when X was already running to allow user logins and different users (as in different people) used different DEs.

cloud instances won't have a hardware graphical display from what i understand.  i have also heard that VPS systems don't either (but a lot of these are based on cloud infrastructures like OpenStack).

maybe they will get Wayland running on VNC in the near future.

---

### Post by TheFu on 2018-07-18
NX honors the normal ~/.ssh/config settings, just like every other ssh-based tools.
x2go has a pretty gui for settings, if you don't want to use the ~/.ssh/config file.

---

### Post by Skaperen on 2018-07-18
what i would need is some command option to specify the port number to use.  or i can use the hack i did for rsync which is to append +nnnn to the host name or IP address (v4 or v6) ... such as skaperen@myserver+8192 will use port 8192.

---

### Post by TheFu on 2018-07-18
> **Skaperen said:**
> what i would need is some command option to specify the port number to use.  or i can use the hack i did for rsync which is to append +nnnn to the host name or IP address (v4 or v6) ... such as skaperen@myserver+8192 will use port 8192.

The ssh_config manpage for ~/.ssh/config is pretty clear.  There are lots of examples online too. You don't have to enter port numbers. They are picked up from the config file.  

You can change all sorts of settings by the alias you use for a connection. port, userid, tunneling options, cipher, IPs, hostnames, lots of stuff.

---

### Post by Skaperen on 2018-07-19
these were cases where the choice of port number frequently changed, particularly a case where a local bastion host was running multiple ssh port forwardings via a remote bastion host as a quick access to a new remote network of servers until a VPN could be decided on and set up allowing everyone to select the remote host of interest.  it turns out this was used for several weeks.  teams often needed to access more than one remote host.  people either used my hack or wrote their own scripts.  after the VPN was up i took the bastion ports scheme down and got a flood of complaints so i put it back up with a time warning.

my hack is an ssh client wrapper (in bash) that added the host+port feature and also added a user+screen feature that allowed a quicker means to login to a named screen session.  i still use this script for that instead of manually doing a screen command after i am connected. so you might see me do "pdh+code@volta+3888" (i don't need to type "ssh") ... yeah i still use it for ports, too, and leave my ".ssh/config" file "-r--------" to avoid editing accidents.

---

