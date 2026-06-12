---
title: "NX server installation issue"
date: 2008-02-17
forum: Desktop Environments
---

### Post by sdionne000 on 2008-02-17
I installed FreeNX using these [http://www.nomachine.com/download-package.php?Prod_Id=5](http://www.nomachine.com/download-package.php?Prod_Id=5)
installed Client then node then server and in the install of the server I got these warnings can anybody help
NX> 700 WARNING: Error when trying to connect to NX server. Error is:
NX> 700 WARNING: ssh: connect to host 127.0.0.1 port 22: Connection timed out

NX> 700 WARNING: NX has been configured to use the SSH server on default port
NX> 700 WARNING: 22 but no SSH daemon is listening on this port. When the
NX> 700 WARNING: installation completes, please ensure that SSHD is installed
NX> 700 WARNING: and is up and running. If you want to contact SSHD daemon on
NX> 700 WARNING: a port different from 22, you need to configure NX Server and
NX> 700 WARNING: Node accordingly. More information is available on the NoMachine
NX> 700 WARNING: Knowledge Base at: [http://www.nomachine.com/kb/index.php](http://www.nomachine.com/kb/index.php)
NX> 700 Installation of NX server was completed with warnings.
NX> 700 Please review thesdwqqw dsx install log '/usr/NX/var/log/install'
NX> 700 for further details.
NX> 700 Showing file: /usr/NX/share/documents/server/install-notices
NX> 700 Bye.

ANY help would be greatly appreciated...
I have SSH installed and working so I have no idea why I am getting the above
thanks

---

### Post by sdionne000 on 2008-02-17
this error is happening on 7.10 ubuntu

---

### Post by greavette on 2008-02-25
Hello,

I am by no means an expert on FreeNX as I have been struggling to get this working on Gutsy as well.  But it looks like from your error message that you do not have openssh-server installed and running.  

I used the instructions from this thread - [http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)
and have found the posts there to be very helpful.

I hope this helps!

---

### Post by daflame on 2008-02-26
> **sdionne000 said:**
> I installed FreeNX using these [http://www.nomachine.com/download-package.php?Prod_Id=5](http://www.nomachine.com/download-package.php?Prod_Id=5)
installed Client then node then server and in the install of the server I got these warnings can anybody help
NX> 700 WARNING: Error when trying to connect to NX server. Error is:
NX> 700 WARNING: ssh: connect to host 127.0.0.1 port 22: Connection timed out

NX> 700 WARNING: NX has been configured to use the SSH server on default port
NX> 700 WARNING: 22 but no SSH daemon is listening on this port. When the
NX> 700 WARNING: installation completes, please ensure that SSHD is installed
NX> 700 WARNING: and is up and running. If you want to contact SSHD daemon on
NX> 700 WARNING: a port different from 22, you need to configure NX Server and
NX> 700 WARNING: Node accordingly. More information is available on the NoMachine
NX> 700 WARNING: Knowledge Base at: [http://www.nomachine.com/kb/index.php](http://www.nomachine.com/kb/index.php)
NX> 700 Installation of NX server was completed with warnings.
NX> 700 Please review thesdwqqw dsx install log '/usr/NX/var/log/install'
NX> 700 for further details.
NX> 700 Showing file: /usr/NX/share/documents/server/install-notices
NX> 700 Bye.

ANY help would be greatly appreciated...
I have SSH installed and working so I have no idea why I am getting the above
thanks

Just to note, that is NOT FreeNX, but NX Free Edition.  It is very different than FreeNX.  However, if you follow the posting above that is the forum that I setup for those desiring FreeNX:
[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)

---

