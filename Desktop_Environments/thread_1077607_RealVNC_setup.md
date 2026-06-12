---
title: "RealVNC setup"
date: 2009-02-22
forum: Desktop Environments
---

### Post by kamasabi on 2009-02-22
I've tried researching over and over the passed few days on how to set up a vnc server on my file server *ubuntu 7.10* and have only found bits and parts on how to do it.  I've gotten it to work to get me to the point where I can get up to a terminal, and be able to log in on a user's current session (able to see desktop environment), however, I want to be able to connect in at the login screen, requiring the use of my regular ubuntu credentials, basically like having VNC as a startup service.  Does anyone have "for dummies" instructions on how to set this up and configure it?

---

### Post by dimmat on 2009-03-03
I had a similar problem with Ubuntu 8.10. In my case I wanted to have access to my Ubuntu PC from a Windows-based PC using Microsoft Terminal Services Client (mstsc). The default VNC server (Vino) worked fine but had three major drawbacks:
a) Vino starts only when the user logs into Ubuntu (No VNC server at login screen).
b) I was getting a mirror of my desktop, not a new session.
c) I needed a VNC client to connect from Windows!

I overcame the above problems by removing the default VNC server and installing TightVNC together with XRDP. XRDP acts like a "bridge" for TightVNC. 

The steps of the procedure are:

1. Uninstallation of the default Ubuntu VNC server (Vino):
----------------------------------------------------------------------------
Go to: System --> Administration --> Synaptic Package Manager 
Search for the "Vino" package, Mark For Removal, Apply. 


2. Installation of TightVNC and XRDP:
---------------------------------------------------------
While you are using Synaptic Package Manager, seacrh for "tightvnc" package (be careful, not "xtightvnc") and Mark For Installation. Likewise, search for the "xrdp" package and Mark also For Installation. Apply.
PS: if you want, you may discard any other "vnc" package that you don't need!


3. Configuration of XRDP (Optional)
----------------------------------------------------------
Open a terminal and type the three following commands: 

```

$ cd /etc/xrdp

$ cp xrdp.ini xrdp.ini.bak 

$ sudo gedit /etc/xrdp/xrdp.ini 

```

Remove Xrdp2-Xrdp6 sections, leave only the Xrdp1 section. Your xrdp.ini should look like this:

```

[globals]
bitmap_cache=yes
bitmap_compression=yes
port=3389
crypt_level=low
channel_code=1

[xrdp1]
name=RDP_To_TightVNC
lib=libvnc.so
username=ask
password=ask
ip=127.0.0.1
port=-1

```


4. Connecting
--------------------------
Restart the system and you are ready to connect!

To connect from another Ubuntu machine, use: Applications --> Internet --> Terminal Server Client, type the IP of your Ubuntu VNC machine, use RDPv5 or RDP, click Connect!

To connect from a Windows-based machine, use: Start --> Run --> mstsc, type the IP of your Ubuntu VNC machine, click Connect. 

When connected, use your Ubuntu user account credentials (u/n and p/w) and remotely login to your desktop. Enjoy!!

---

### Post by kamasabi on 2009-03-04
thanks for the info, I'll give this a shot later on in the evening! :D

---

### Post by wlraider70 on 2009-03-04
I don't want to hijack this thread, but i just did all that (minus the vino uninstall)

i can get all the way to enter my username and password and then I get an error.

the error is very unspecific, screen shot attached.

---

### Post by dimmat on 2009-03-06
I verified the above procedure again in a clean install of Ubuntu. There is nothing wrong with it, just follow the steps precisely.

Nevertheless, this time I had a small issue with Synaptics. I could not find the "tightVNC" package. I had enabled all repositories (Settings --> Repositories --> Ubuntu Software --> Tick to all repositories, then "Reload") but in vain. I solved this problem by typing in a terminal:

```
$ sudo update-apt-xapian-index
```

The hidden packages appeared again... :D


Cheers!

---

