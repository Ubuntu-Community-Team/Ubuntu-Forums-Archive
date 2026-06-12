---
title: "User with uid 201 not visible in lightdm login (14.04)"
date: 2014-05-05
forum: Desktop Environments
---

### Post by jmarin on 2014-05-05
I need to set my uid to 201 because I'm using NFS and I have this uid on all other computers of my network.  I used usermod to change my uid - so far, so good.
 
The lightdm login window no longer shows my username and I have to select "Other" and then type in my username and password every time the screen is locked and I find this annoying.  I tried setting "minimum-uid=100" in /etc/lightdm/users.conf but it didn't help.  Any ideas?

---

### Post by brainwash on 2014-05-05
Did you read the note in /etc/lightdm/users.conf?

[I]# NOTE: If you have AccountsService installed on your system, then LightDM will
# use this instead and these settings will be ignored[/I]

So, removing accountsservice might be one option to get it working.

---

### Post by jmarin on 2014-05-05
I removed AccountsService using Ubuntu Software Center and rebooted, but it didn't help.

---

### Post by macachuto on 2014-05-05
As long as I know you can use "-o uid=...,gid=..." with mount command.

---

### Post by jmarin on 2014-05-06
I googled for NFS uid remapping, but it seemed that only nobody and root can be remapped, not regular uids.

Anyway, it should be easy to make the login window display users with any given uids, right?

---

### Post by bapoumba on 2014-05-06
Looked for that the other day, I need to find the file again, but I think LightDM does not show users with UID < 1000.

Edit : UID < 500 :
/etc/lightdm/users.conf
```
UserAccounts]
minimum-uid=500
hidden-users=nobody nobody4 noaccess
hidden-shells=/bin/false /usr/sbin/nologin
```
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1283407](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1283407)

---

### Post by jmarin on 2014-05-06
As I said, I have set "[COLOR=#000000]minimum-uid=100", but uid 201 still doesn't show up.  Is there a hard-coded limit in lightdm or what's wrong?  Is there a keyword to manually add my username to list of users displayed?

[/COLOR]

---

### Post by bapoumba on 2014-05-06
> **jmarin said:**
> As I said, I have set "[COLOR=#000000]minimum-uid=100", but uid 201 still doesn't show up.  Is there a hard-coded limit in lightdm or what's wrong?  Is there a keyword to manually add my username to list of users displayed?

[/COLOR]
From memory, I'll check : is there an "other" or similar option ? You should be able to give a username and password even if not on the displayed list.

---

### Post by jmarin on 2014-05-06
Yes, I can type username and pw, but first I have to select Other from menu and doing all this N+1 times a day is annoying.

---

### Post by steeldriver on 2014-05-06
I'm not on 14.04 yet so apologies if this turns out to be unhelpful but the options to switch from listing the known users to providing a traditional username entry box *used to be *

```

greeter-hide-users=true
greeter-show-manual-login=true

```

in the [SeatDefaults] section of the lightdm.conf file

---

### Post by bapoumba on 2014-05-06
Hey steeldriver :)

On 14.04 :
/etc/lightdm/lightdm.conf.d/20-lubuntu.conf
```
[SeatDefaults]
user-session=Lubuntu

```

/etc/lightdm/users.conf
```
# User accounts configuration
#
# NOTE: If you have AccountsService installed on your system, then LightDM will
# use this instead and these settings will be ignored
#
# minimum-uid = Minimum UID required to be shown in greeter
# hidden-users = Users that are not shown to the user
# hidden-shells = Shells that indicate a user cannot login
#
[UserAccounts]
minimum-uid=500
hidden-users=nobody nobody4 noaccess
hidden-shells=/bin/false /usr/sbin/nologin
```

Now my search fu is failing on me to find some of these strings in files..

---

### Post by jmarin on 2014-05-06
I looked at the lightdm source code and found this:

minimum_uid = g_key_file_get_integer (config, "UserList", "minimum-uid", NULL);

The "UserList" is name of a parameter group.  However, in /etc/lightdm/user.conf, there's a section called "UserAccounts".  I created a new section "UserList" and duplicated the parameters under it - and now it works.  So, either the default config file should be fixed or the group/section name in lightdm should be changed.  As it is, the parameters in user.conf are quietly ignored.

---

### Post by steeldriver on 2014-05-06
... I don't know if it helps, but in 12.04 there was a 'sample' conf file at /usr/share/doc/lightdm that listed all the current option strings

```
less /usr/share/doc/lightdm/lightdm.conf.gz
```

If 14.04 has the same, the info there *may* be more up-to-date than elsewhere

---

### Post by bapoumba on 2014-05-06
> **jmarin said:**
> I looked at the lightdm source code and found this:

minimum_uid = g_key_file_get_integer (config, "UserList", "minimum-uid", NULL);

The "UserList" is name of a parameter group.  However, in /etc/lightdm/user.conf, there's a section called "UserAccounts".  I created a new section "UserList" and duplicated the parameters under it - and now it works.  So, either the default config file should be fixed or the group/section name in lightdm should be changed.  As it is, the parameters in user.conf are quietly ignored.

I'm now going into unkown waters.
/etc/login.defs ?

---

### Post by bapoumba on 2014-05-06
> **steeldriver said:**
> ... I don't know if it helps, but in 12.04 there was a 'sample' conf file at /usr/share/doc/lightdm that listed all the current option strings

```
less /usr/share/doc/lightdm/lightdm.conf.gz
```

If 14.04 has the same, the info there *may* be more up-to-date than elsewhere

Yes, it's there. I had a look the other day for some other reason.

---

