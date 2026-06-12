---
title: "How to Connect vino-server to listening vncviewer?"
date: 2009-03-07
forum: General Help
---

### Post by splicer on 2009-03-07
I routinely use VNC to support clients who reside behind NAT'd connections.  For windows machines, this has not been a problem, because they can use VNC server's "Add new client" option to initiate the connection to my listening viewer.  However, those clients that have begun to use Ubuntu don't seem to have this option.

Does anyone know if there is a method that I may have missed that will allow vino-server to initiate a VNC connection to remote, listening viewers?

Thanks!

---

### Post by fragos on 2009-03-08
On your user's Ubuntu System-> Preferences-> Remote Desktop. By default these features are disabled. The options on both tabs speak for themselves.

---

### Post by splicer on 2009-03-08
No, I'm very much aware of Remote Desktop (aka vino) and have been using it on my own systems for some time as well as have customers turn it on when needed.  The question is about having vino (aka Remote Desktop) initiate the connection rather than a VNC client.

There are times, such as when behind a NAT'd gateway, when direct access to a client's machine from the internet is unavailable.  In these instances, it would be handy to have vino (Remote Desktop) initiate the connection to a remote vncviewer that is running in listening mode.  On window's machines running RealVNC, this is easily done by right-clicking on the VNC Server icon in the task tray and selecting "Add new client", which then causes VNC Server to reach out and connect to a VNC Viewer that is listening for connections.  As far as I can tell, there is no configuration option for vino that does this.

So my question is, does anyone know how to make vino (Remote Desktop) do this as well?

---

### Post by fragos on 2009-03-08
I doubt you'll find what you want in Linux as what you're asking for is a major security hole. You can achieve your goal by rather leaving a viewer open on your taget you install a server instead of a viewer. If you wish bydirectional initiation you install both a server and a viewer on both ends. In the Ubuntu case both server and viewer are already installed and all that is required is enabling with configuration.

---

### Post by Jingo on 2009-04-11
I'm looking for the same thing.

other vnc implementations have "vncconnect" eller "vncconfig" to let vncserver connect to vncviewer !

Havn't found a solution yet !

Anyone ?

---

