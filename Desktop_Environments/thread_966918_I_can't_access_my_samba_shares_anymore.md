---
title: "I can't access my samba shares anymore"
date: 2008-11-01
forum: Desktop Environments
---

### Post by uknowho008 on 2008-11-01
It might be because of an update but when I first install ubuntu 8.04 or 8.10 I have access to my samba shares, then later on down the line I suddenly can't access my shares. They work fine from windows which really annoys me. Can anybody tell me whats going on here?

This is the message I get...

> Error: Failed to mount Windows share
Please select another viewer and try again.

Thanks.

---

### Post by uknowho008 on 2008-11-02
Nobody else has this problem? My networking completely stops working too if I don't use it for 10min or so. /etc/ini.d/networking restart doesn't help either. infact I don't think I get a IP address when I restart the network. But if I restart the whole computer it works. This all works just fine on my windows machine.

---

### Post by drrob1 on 2008-11-02
I have found Ubuntu samba hard to configure.  Make sure that synaptic shows the following installed: libsmbclient, nautilus-share, samba, samba common, smbclient, smbfs, libsmbpass

And I found it useful to do this:
smbclient -NL <network name>
smbclient -L <network name> -U <user name>

If these commands work, you may have a password problem.  Doing
smbclient -L <network name> -U <user name> for each of my networked computers from my ubuntu box cleared this up for me.

---

