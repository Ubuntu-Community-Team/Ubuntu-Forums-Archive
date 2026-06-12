---
title: "Samba mount takes system down"
date: 2006-03-19
forum: Desktop Environments
---

### Post by bmgz on 2006-03-19
I have numurous windows/ubuntu clients, so I just use Samba for all of them.
I was using Samba and NFS but NFS permissions became a nightmare.
I mount a share on all the clients during boot via an fstab entry.

My only problem is if my server reboots or I restart the Samba service on the
server (slackware 9.1), all the ubuntu clients just start hanging indefinately.

I have to actually totally reboot them. Is their a way to make a samba mount as robust as NFS?

---

### Post by heywire on 2006-03-20
Just to add to this, I basically see the same thing.  I have a Network Attached Storage that uses SMB.  I mount the shares during startup in fstab, but if for some reason I hit my "/media" folder at the wrong time, I might as well reboot.

Sorry that I could not he helpful, other than to say I feel your pain :)

---

### Post by Dragineez on 2006-03-20
You can connect to your Linux shares with smb, but should you? Including the "hard,intr" directives in fstab for an NFS connect will take care of your clients hanging when the server is rebooted. NFS is also very tunable for performance.

I feel your pain on the permissions configuration for NFS, but if this is your own small home network and it's behind a firewall, it is possible to configure it very insecurely. The advantage is that connecting becomes very easy. This disadvantage is that - well, its very insecure.

---

### Post by bmgz on 2006-03-21
I resorted to NFS again for Linux clients. Much better!
The major thing to remember with NFS is imagine it has
NOTHING to do with network and everything is local.

This will help you alot sorting out permissions etc.

---

