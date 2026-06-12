---
title: "VPN Client Recommendation"
date: 2006-01-19
forum: General Help
---

### Post by ronmarley1 on 2006-01-19
Hi,
Can anyone recommend a VPN client for a Cisco VPN?  I would prefer one with a GUI.  I tried VPNC in Synaptic and could not get it to work.
Thanks in advance.

---

### Post by spin2cool on 2006-01-19
I used to use vpnc successfully on Ubuntu.  What are your specific problems?  Are they addressed in this forum anywhere?

Check out this thread first, it's a good guide:
[http://ubuntuforums.org/showthread.php?t=80798](http://ubuntuforums.org/showthread.php?t=80798)

It also details how to apply a patch that may solve your problem.

Also try searching these forums for vpnc - there are lots of threads on it

---

### Post by ronmarley1 on 2006-01-23
Hi Spin,
Thanks for the reply.  I'll go back and play with it.  Looks like it's workable.

---

### Post by ronmarley1 on 2006-01-23
Hi Spin,
When I run VPNC, i get: (what I entered is in blue)
rgoodwin@ubuntu2112:~$ vpnc
Enter IPSec gateway address: [COLOR="Navy"]xxx.xxx.xxx.xxx (the ip address of our pix box)[/COLOR]
Enter IPSec ID for xxx.xxx.xxx.xxx: [COLOR="Navy"]I'm not sure what to put here.[/COLOR]
Enter IPSec secret for @xxx.xxx.xxx.xxx: [COLOR="Navy"]I'm not sure what to put here either.[/COLOR]
Enter username for xxx.xxx.xxx.xxx: [COLOR="Navy"] I entered my VPN username[/COLOR]
Enter password for [email]My VPN username@xxx.xxx.xxx.xxx[/email]: [COLOR="Navy"]I entered my VPN password[/COLOR]
vpnc: binding to port 500: Permission denied
rgoodwin@ubuntu2112:~$

Any ideas?
Thanks

---

### Post by Tichondrius on 2006-01-23
I think you should install the cisco vpn client

[http://www.bol.ucla.edu/services/vpn/](http://www.bol.ucla.edu/services/vpn/)

Download, unpack the archive and run vpn_install.sh script.

You will need to have the build tools and the kernel source installed (install build-essential, gcc-3.4 and linux-source in synaptic) because the cisco vpn client installation script actually builds a kernel module.

---

### Post by johnnymac on 2006-01-24
Use pptpconfig...it's pretty easy to install and setup.

---

### Post by hajk on 2006-01-25
The OP should ask the IT people at the site he wants to connect to for the groupID and groupSecret as responses to the IPSec ID and IPSec secret questions. (At my university they're just "ipsec" and "ipsec"...). He should also make a <dest>.conf file for that connection, there is already an example in the /etc/vpnc/ directory -- saves a lot of typing when establishing the connection.
Note also: you must run "sudo vpnc <dest>.conf", and afterwards "sudo vpnc-disconnect" with "sudo" privileges.  

[Note: replace <dest> with a catchy name for the connection.]

---

