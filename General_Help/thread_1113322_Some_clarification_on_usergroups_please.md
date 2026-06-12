---
title: "Some clarification on usergroups please"
date: 2009-04-01
forum: General Help
---

### Post by PaganImmolator on 2009-04-01
I notice that on my system which is a fresh install, Ubuntu has assigned each of my users to a user group named after that individual user. Is that normal?

In otherwords:

user1 > group "user1"
user2 > group "user2" 

and so on. 

Correct me if I am wrong but shouldn't user1 (who is SU) be part of usergroup admin and all others should be part of usergroup "users"?

---

### Post by kpatz on 2009-04-01
Yes this is normal.

The user you created on install is also assigned to the admin group, but as an additional group, not the primary.

---

### Post by ibuclaw on 2009-04-01
Administrators **are** part of the admin group, and users **are** part of the users group, though, feel free to prove me wrong :)

Open up a terminal, and type in:
```
groups
```
to see what groups you are a part of.

This is what mine looks like
```
iain adm dialout cdrom plugdev lpadmin **admin** sambashare vboxusers libvirtd
```

Regards
Iain

---

### Post by PaganImmolator on 2009-04-01
So it sounds like the user=usergroup was done by design. 

But is that the ideal way to do it? Windows has generally two groups Admin and Normal users. There are some other choices but those are the most common.

---

### Post by ibuclaw on 2009-04-01
> **PaganImmolator said:**
> So it sounds like the user=usergroup was done by design. 

But is that the ideal way to do it? Windows has generally two groups Admin and Normal users. There are some other choices but those are the most common.

Wrong ...

Windows has 9 distinct groups:
[LIST]
[*]Administrators - Full Control
[*]Backup Operators - Backups/Restores files
[*]Guests - Very Limited Access
[*]Network Configuration Operators - Manages some aspect of the network configuration
[*]Power Users - Performs many management tasks, does not have full control.
[*]Remote Desktop Users - Grants the right to log onto the computer from remote.
[*]Replicator - Facilitates directory and file replication
[*]Users - Has limited permissions
[*]HelpServices - The user that all MS Help & Diagnostic apps are ran as.
[/LIST]

And all are common, except Replicator, and HelpServices (which, as I mentioned above, is just the group permission that all MS Help and Diagnostic programs run as, and it should never be used to assign users to). Finally, Guests are usually disabled as a security feature.
Infact, contrary to what you say, the Administrators group should be the **least** used group in Windows.

You should only be looking to assign **Users** or **Power Users** permissions to people.
Remember, you always always always want to go for the least amount of administrative effort.


-------------------------------------------------------------


OK, lets just put this a simple way to show the full effectiveness of UNIX permissions (This is not just Linux, but Mac, UNIX, BSD, BeOS and many many others use permissions this way).

Every file and every directory has three permission bits assigned to them.

1) **Owner**
2) **Group**
3) **Other** (Everyone else).

and as such in any environment, the Owner has the least restrictive permissions, and Everyone else has has the most restrictive.

Scenario:
There is a user, **fred**. Fred's home folder permissions are setup by default like this:
```

**/home/fred**
owner: **fred**  rwx
group: **fred**  r-x
other:       r-x

```
**fred** has full permissions on his home folder, all user accounts that are assigned to the **fred** group have read and execute permissions, everyone else has read and execute permissions too.

Now, lets say **fred** wants to restrict access to his personal files to only himself and the people he trusts?
To achieve this, you remove all permissions for the other group, which in effect denies them access.
```
chmod o-xr /home/fred
```
The permissions on the directory now look like this:
```

**/home/fred**
owner: **fred**  rwx
group: **fred**  r-x
other:       ---

```
**fred** has full permissions on his home folder, all user accounts that are assigned to the **fred** group have read and execute permissions, everyone else is denied access.

By default, no one is assigned to your group account, so it is pretty safe to say that **fred**'s data/personal files are safe from external users from reading/taking them.
But for example purposes, lets say **fred** has a girlfriend, **bethan** (I'm great with names).
**fred** wants to give his girlfriend access to access his home folder, which contains his music collection, but doesn't trust her enough to give her permissions to edit files.

Since the permissions of the direct are already setup, nothing further is need to be done with **chmod**, and we'll just add bethan to the **fred** group.
```
sudo usermod -a -G fred bethan
```
And now **bethan** is part of the group **fred**!

So, **fred** has full read/write/execute permissions, **bethan** can now list and read/execute the contents of **fred**'s home folder, whereas everyone else is denied, as they aren't part of the **fred** group. (Yeah, lots of repetition in my little scenario, I know :))

I hope this shed's some light on permissions. It's not at all an overly complex system in place, but it is absolutely effective (and makes alot more sense than the obfuscated Windows groups/permissions scheme).

Regards
Iain

---

### Post by paradigm2 on 2009-04-01
> **PaganImmolator said:**
> So it sounds like the user=usergroup was done by design. 

But is that the ideal way to do it? Windows has generally two groups Admin and Normal users. There are some other choices but those are the most common.

Ideal varies.  But as far as more options, *nix has windows beat hands down in this regard.  Its highly configurable and having a user and group named the same can be quite beneficial.  For instance with the Polipo proxy I installed, by default the disk cache files are owned by PROXY:PROXY.  In order to allow a user to remove files from the cache all I have to do is:

"adduser <USER> PROXY"

and then they can work with all these files -- and more importantly I can still keep the permissions "chmod o-rwx" for security.  This scheme can come in very handy sometimes.

---

### Post by PaganImmolator on 2009-04-02
> Windows has 9 distinct groups:

Yes, I know. However I still am of the opinion that most home users of XP will only have admins and users because they don't know any better. I doubt most XP users are going to go dig around in the security features in the System Tools panel. But frankly thats neither here nor there for what I am after. 

Tinivole: Your explanation was appreciated and did help. Unfortunately what I am concerned with is the obfuscated Windows permissions system and translating that into Linux permissions. I think I have a pretty good handle on it now.

However, I still don't understand the need for having a user group named after each user.

---

