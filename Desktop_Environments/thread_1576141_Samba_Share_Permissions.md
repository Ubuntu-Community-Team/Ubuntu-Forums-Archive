---
title: "Samba Share Permissions"
date: 2010-09-16
forum: Desktop Environments
---

### Post by Ow3n on 2010-09-16
I'm currently using Ubuntu 8.10 Desktop as a network share host at our small office.

All of the users are mapped to the shared folder on Ubuntu and for the most part, everything is working well.

The problem is with folder permissions. We have one folder, HR, that should only be accessible by our HR person, Sue. I'm not familiar with LDAP, but I've installed Likewise Open and it appears the machine has joined the domain. I can access the network share with my Windows domain credentials, but for whatever reason, when I try to dedicate the HR folder to Sue, nobody on the domain can access it.

I've tried:

sudo chown -R sue:domain^users /media/L/hr
sudo chmod -R 700 /media/L/hr

Everything except for chmod 777 locks everyone out of the folder. I'm really stuck on this one. ](*,)

---

### Post by SeijiSensei on 2010-09-18
> **Ow3n said:**
> The problem is with folder permissions. We have one folder, HR, that should only be accessible by our HR person, Sue.

I'm confused by your later comment that "nobody on the domain can access it."  Presumably no one other than Sue should be able to access it, correct?

> I'm not familiar with LDAP, but I've installed Likewise Open and it appears the machine has joined the domain.

OK, let's start from scratch.  You have an Ubuntu host that is running Samba and a bunch of Windows clients, yes?  Did you try setting up simple authentication for Samba on the Linux host using smbpasswd?  (See "man smbpasswd" for details.) Unless you have a large number of users, or use Windows Active Directory for authentication, this is probably the simplest solution.

With smbpasswd auth, Samba maintains its own parallel authentication system.  Once you've created the smbpasswd file and populated it with the users that require access to this machine, you can define a share in smb.conf that looks like this:

[HR]
path = /path/to/the/hr/directory
valid users = sue
browseable = yes
writable = yes

(You may want to set browseable to "no" so other users can't see the share at all.)

Now Samba also allows you to designate which Unix user to run as when the share is accessed.  If you want the Unix user "sue" to also own this share, the easiest thing is to add "force user = sue" to the directives above.  This tells Samba that it should use Sue's Unix identity when it accesses the shared directory.

You might also want to use the "create mask" to control the permissions on files created via Samba.  If you only want Sue to be able to see the directory in Unix as well, you'll want an 077 mask to create 700 permissions on files created in /path/to/the/hr/directory.

I realize it's a very long file, but "man smb.conf" is your friend.  Also there are a number of sample configurations in smb.conf that may give you some insights into how to set things up the way you want.

This probably belongs in the Networking forum rather than here.  Perhaps a moderator can move it for you.

---

### Post by Ow3n on 2010-09-27
Thanks for the response. 

I do not have smbpasswd configured. Right now, I have a folder shared (it auto-configured Samba) in the /media section of an Ubuntu Desktop machine. Everyone connects as Guest and can drag/drop/execute files. We've had no need for any sort of permissions, until now.

We would like to use Active Directory integration for our Ubuntu machine. Ideally, the same username/password used to log into the user's work machine would be used to log into our network share folder. If we could do that, it seems like it would be easy to assign folder permissions.

I tried to use LikewiseOpen as the "easy" AD-integration, but maybe that's not the way to accomplish what I want.

---

### Post by luvshines on 2010-09-28
Samba + AD. Well this might help:
[http://ubuntuforums.org/showthread.php?t=1580505](http://ubuntuforums.org/showthread.php?t=1580505)

---

