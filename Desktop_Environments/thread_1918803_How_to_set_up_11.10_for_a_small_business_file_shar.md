---
title: "How to set up 11.10 for a small business file shareing server."
date: 2012-02-01
forum: Desktop Environments
---

### Post by Cclips on 2012-02-01
So, basically my work includes setting up a ubuntu server on one of our old ancient desktops. It is a small company with very modest needs, my question is one more of processes. 

The server itself won't really be used to log into/use, but the employees need to have access to the combined shared folder. Which is then mirrored to the cloud using Ubuntu one.

That is done already.

What we now want to do is set permissions so that the president can see everything, but the finance person can see only finance stuff, and the marketing person can see only marketing stuff. 

My thought was to go in and set up user/accounts for everyone with predefined groups. I.e. make a finance user group, then limit a finance subfolder to only allow groups XYZ, or in this case president/finance. Likewise, marketing would only allow groups president/marketing. 

I could then assign said user accounts to said user groups so that they can simply log in, and have access/denial to whatever groups they need to.

My question, how do I basically copy edit a basic user group, and simply add/leave access to certain folders. I've looked into the group Id and privilege, but the only thing I get is an arbitrary and obtuse privilege or group number. 

Additionally, they want to mirror this same permission setup to Ubuntu one, which I'm not even sure is possible at the moment.

Any help is appreciated.

---

### Post by jayshomebrew on 2012-02-02
you're going to have to set up users and/or groups on your server. Please read up on samba:
[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

and also:
[https://help.ubuntu.com/11.10/serverguide/C/samba-fileprint-security.html](https://help.ubuntu.com/11.10/serverguide/C/samba-fileprint-security.html)

finally read up:
[https://help.ubuntu.com/11.10/ubuntu-help/user-accounts.html](https://help.ubuntu.com/11.10/ubuntu-help/user-accounts.html)

This is assuming you are connecting to your ubuntu server from windows clients, or do you use macs, or other linux clients?

---

### Post by Cclips on 2012-02-03
> **jayshomebrew said:**
> you're going to have to set up users and/or groups on your server. Please read up on samba:
[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

and also:
[https://help.ubuntu.com/11.10/serverguide/C/samba-fileprint-security.html](https://help.ubuntu.com/11.10/serverguide/C/samba-fileprint-security.html)

finally read up:
[https://help.ubuntu.com/11.10/ubuntu-help/user-accounts.html](https://help.ubuntu.com/11.10/ubuntu-help/user-accounts.html)

This is assuming you are connecting to your ubuntu server from windows clients, or do you use macs, or other linux clients?

The server is already setup with Samba, and so far we've got a few windows clients all running different versions, and my ubuntu 10.04 laptop. They all connect and play nice pretty easily. I'm just trying to figure out the easiest ways to get permissions done.

The links you posted are great for everything I need on this side. The real problem is trying to mirror said things in a cloud service.

---

