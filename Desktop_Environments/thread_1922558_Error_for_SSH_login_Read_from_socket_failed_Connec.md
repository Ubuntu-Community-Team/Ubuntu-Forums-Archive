---
title: "Error for SSH login: Read from socket failed: Connection reset by peer"
date: 2012-02-09
forum: Desktop Environments
---

### Post by avimanyu786 on 2012-02-09
While logging in via ssh:

sudo ssh user@ip

I got the following error: Read from socket failed: Connection reset by peer

I went through many google search results. But I could not find an appropriate solution.

Then I uninstalled ssh and openssh-server using(Mark for Removal) Synaptic Package Manager and reinstalled it.

Still the same error. I noticed that the config files in /etc/ssh remained after uninstallation.

Now I selected "Mark for Complete Removal" in Synaptic Package Manager.

New configuration files were created while reinstalling ssh and openssh-server. 

Login successful :) !

---

