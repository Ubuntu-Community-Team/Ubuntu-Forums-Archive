---
title: "FreeNX user login issue"
date: 2009-02-15
forum: General Help
---

### Post by DomainReseller on 2009-02-15
I installed FreeNX on a remote Ubuntu server after installing Gnome. The datacenter originally provided the root login information rather than access to an account with admin privileges. The installation appeared to work properly, but I'm having trouble logging in using the NoMachine client. I created another user via SSH using adduser, but neither the root account or the new account are allowing logins.

Error message received:

```
Authentication failed for user root
```

Any assistance would be greatly appreciated.

---

### Post by DomainReseller on 2009-02-15
The root user was created before Gnome was installed. Perhaps the root account isn't enabled in Gnome? At the moment I don't have access to Gnome until I have a way to remote connect. Is there a way to enable a user account to access Gnome via SSH?

---

### Post by DomainReseller on 2009-02-28
Bump

---

### Post by seppl82 on 2009-03-03
Hi,

i have the same issue on my installation of freenx.
(If i install the package from the repository)

Try the following
[FONT="Courier New"]
wget [http://datakeylive.com/ubuntu/pool/main/f/freenx-server/freenx-server_0.7.2-1hardy2_i386.deb](http://datakeylive.com/ubuntu/pool/main/f/freenx-server/freenx-server_0.7.2-1hardy2_i386.deb)

sudo dpkg -i freenx-server_0.7.2-1hardy2_i386.deb[/FONT]

Please tell me if it works

---

### Post by DomainReseller on 2009-03-03
I tried installing from the .deb package. Same error.

---

### Post by ene_dene on 2009-03-03
Login as an ordinary user, and then use sudo, or su root to do the task you want to do.

---

### Post by DomainReseller on 2009-03-03
As I mentioned in the first post, the issue exists when logging in as a regular user as well.

---

### Post by ene_dene on 2009-03-03
NXclient always writes some log of what went wrong, could you paste it here?

---

### Post by DomainReseller on 2009-03-03
The details button is faded for this issue. No additional information is provided.

---

### Post by ene_dene on 2009-03-03
Darn...

Connect to remote comp via ssh. Then:
```
cd /usr/NX/bin
sudo ./nxserver --userlist
```
If your user is not listed then:
```
sudo ./nxserver --useradd your_username
```
then list the users again, to see if you succeeded. If so, try connecting through NX again. If it fails, I don't know what could it be. Maybe the X forwarding is disabled or something like that.

---

### Post by DomainReseller on 2009-03-03
It's still not working. Another really odd factor is that I used an identical server setup with NX from NoMachine.com, and the login worked. There were a few issues with Gnome, but otherwise everything was successful. NXserver from NoMachine isn't a logical alternative, since sudo/su isn't allowed, making remote administration practically impossible from the GUI. Additionally, the 2 user limit for the free edition is something I'm trying to avoid.

I'm going to test a few modifications to the default configuration. I'll let you know if I figure anything out.

---

### Post by seppl82 on 2009-03-04
Hey, 

another idea try this tutorial... It worked for me

[http://www.drtek.ca/freenx-server-ubuntu-hardy](http://www.drtek.ca/freenx-server-ubuntu-hardy)

Ensure that you remove your current packages of the nx-server before you start with this tutorial

/Regards
Seppl

---

