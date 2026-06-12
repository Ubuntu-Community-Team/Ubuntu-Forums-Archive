---
title: "Does Freenx work with Nomachine nxclient 2.1.0"
date: 2007-04-06
forum: Desktop Environments
---

### Post by voipfc on 2007-04-06
Is the version of Freenx available on Ubuntu compatible with nomachine client nxclient 2.1.0?

I am using Ubuntu 6.06 and on checking the forums it appears that the Ubuntu version of freenx only works with version 1.5 of the NoMachine client. 

When I install in the nomachine nxserver everything works until the installation routine attempts to connect the user nx to the server and that is when it fails as shown below?

Any experience with this issue?

> NX> 700 Result: OK.
NX> 700 WARNING: Error when trying to connect to NX server, error is:
NX> 700 WARNING: NX> 203 NXSSH running with pid: 5227
NX> 200 Connected to address: 127.0.0.1 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed..
NX> 700 WARNING: nxsetup cannot validate the sanity of the current installation:
NX> 700 WARNING: the current system or NX configuration could be broken.
NX> 700 WARNING: If difficulties arise (for example sessions cannot be started),
NX> 700 WARNING: it is advisable that you try to uninstall the NX server and the
NX> 700 WARNING: NX client packages then install them again.
NX> 700 WARNING: Search also the NoMachine Knowledge Base at the URL below:
NX> 700 WARNING: [http://www.nomachine.com/kb](http://www.nomachine.com/kb)
NX> 700 WARNING: for common errors encountered when performing a software update
NX> 700 WARNING: and the related hints on how to solve them..
NX> 700 Installation of NX server was completed with warnings.
NX> 700 Please review the install log '/usr/NX/var/log/install'
NX> 700 for further details.
NX> 700 Showing file '/usr/NX/share/documents/server/install-notices':
NX> 700 Bye.
root@ubuntu606m:~/downloads#


---

### Post by Bigsy on 2007-04-07
Freenx 0.6.0 is meant to work with the 2.1 client, altho it is giving me a couple of minor probs: [http://ubuntuforums.org/showthread.php?t=403493&highlight=freenx+0.6.0](http://ubuntuforums.org/showthread.php?t=403493&highlight=freenx+0.6.0)

If you add &#8220;deb [http://www.dentalonline.com/freenx/](http://www.dentalonline.com/freenx/) ./&#8221; to your sources list you can install the latest 0.6 server by apt-get

---

### Post by voipfc on 2007-04-07
In [http://ubuntuforums.org/showthread.php?t=403493&highlight=freenx+0.6.0](http://ubuntuforums.org/showthread.php?t=403493&highlight=freenx+0.6.0) you mentioned that it worked with the Kubuntu desktop. Is it possible to install the desktop alone on a Ubuntu 6.06 installation?

> **Bigsy said:**
> Freenx 0.6.0 is meant to work with the 2.1 client, altho it is giving me a couple of minor probs: [http://ubuntuforums.org/showthread.php?t=403493&highlight=freenx+0.6.0](http://ubuntuforums.org/showthread.php?t=403493&highlight=freenx+0.6.0)

If you add “deb [http://www.dentalonline.com/freenx/](http://www.dentalonline.com/freenx/) ./” to your sources list you can install the latest 0.6 server by apt-get

---

### Post by Bigsy on 2007-04-08
Yes it is: [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

Although I suspect my issues are probably down to me running it on Feisty as aftr mucking around it is working on GNOME now..... I suspect it will probably work fine off the bat on 6.06.

---

### Post by voipfc on 2007-04-12
Is that the right deb source you've added. When I add it to /etc/apt/sources.list as you typed it I get gives a syntax error in apt-get. Are there some extra bits like dapper, main, restricted etc that I have to add.


> **Bigsy said:**
> Freenx 0.6.0 is meant to work with the 2.1 client, altho it is giving me a couple of minor probs: [http://ubuntuforums.org/showthread.php?t=403493&highlight=freenx+0.6.0](http://ubuntuforums.org/showthread.php?t=403493&highlight=freenx+0.6.0)

If you add &#8220;deb [http://www.dentalonline.com/freenx/](http://www.dentalonline.com/freenx/) ./&#8221; to your sources list you can install the latest 0.6 server by apt-get

---

