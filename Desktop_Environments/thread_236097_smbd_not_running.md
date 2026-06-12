---
title: "smbd not running"
date: 2006-08-14
forum: Desktop Environments
---

### Post by Dave S on 2006-08-14
Hi guys,

I am still having problems getting samba up and running. 

Nmbd and smbd are not running. My windows xp pcs cannot see the ubuntu box yet the ubuntu box can see and access them.

I checked what is running on ubuntu and smbd and nmbd are not running.

I have done the whole apt-get thing, and keep getting back a reference to samba not found similar package running samba-common.

Package manager tells me samba-common and sambaclient are installed.

can someone please advise on how to get smbd running, or tell me whats wrong. 

I am not into compiling or anything, so if you are to direct be to a different samba package, can you please give me a link to one that will inable me to install it without any hassle. 

Thanks

Dave

---

### Post by az on 2006-08-14
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

The samba client packages are installed by default so that you can see other networks.  To share your computer with the network, you need to install the rest of the samba packages (the samba daemon)  Install the samba package.

If you are not able to find it, you do not have any repositories enabled. See the installing software link in the wiki page above.

---

### Post by Dave S on 2006-08-14
Hi,

Thanks for the reply.

When I try to install samba, it says similar package found (samba-common) it then stops any installation.

Is there a link to a samba.deb instalation package that I can download and simply uninstall the others, and reinstall a new samba package that will work. 

Sorry, but I have very poor internet access and am in a remote location so have a serious problem getting internet time.

Thank you


Dave

---

