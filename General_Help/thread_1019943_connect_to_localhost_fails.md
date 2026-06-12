---
title: "connect to localhost fails"
date: 2008-12-23
forum: General Help
---

### Post by bjdk on 2008-12-23
Hi,
I'm a bit of a novice in Ubuntu, but running Ubuntu 8.04 (64 bit), on which I installed VMWareServer, which I need to access by [http://localhost:8222/ui](http://localhost:8222/ui). Having updated my computer, including a new version of Firefox (3.0.5) I suddenly could not access [http://localhost](http://localhost) - getting "Firefox can't establish a connection to the server at localhost" (127.0.0.1 does not work either). I have searched the net, but until now without success.
First line of my /etc/hosts-file is 127.0.0.1 localhost.
When I call "ping localhost" it works fine, and before the update it worked.

Does anyone have a suggestion to what's wrong?

Thank you.

Bjorn

---

### Post by ibutho on 2008-12-23
Hi and welcome to the forum.

I think you can only access [http://localhost](http://localhost) if you are running some sort of webserver e.g. apache. If you need to access any other service running on the local machine, you would need to enter the port number e.g. [http://localhost:8222/ui](http://localhost:8222/ui) .

---

### Post by HermanAB on 2008-12-23
Re-install VMware.  Once it is working again, don't update the system.  Unless you don't mind re-installing VMware everytime...

---

### Post by bjdk on 2008-12-23
Hi,

Thank you. You may be right, but my problem is, that this call give me the same error - meaning I cannot access my VMWareServer. (which I did before the update)

Thanks
Bjorn

---

### Post by bjdk on 2008-12-23
So you think browser-updates destroys the VMWare-installation? You may be right - I'll try to reinstall.
Thank you.

Bjorn

---

### Post by bjdk on 2008-12-24
I executed the "sudo vmware-config.pl" again, and it solved the problem.

Thank you 

Bjorn

---

### Post by digital_sabine on 2009-10-22
After doing updates today, I was having this same issue.  Running the vmware-config.pl resolved it for me, too.

Thanks,
sandra

---

