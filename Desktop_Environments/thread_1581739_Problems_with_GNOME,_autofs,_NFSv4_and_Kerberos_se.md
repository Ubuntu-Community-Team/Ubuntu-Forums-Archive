---
title: "Problems with GNOME, autofs, NFSv4 and Kerberos security"
date: 2010-09-25
forum: Desktop Environments
---

### Post by infestator on 2010-09-25
Hi all,

I've configured a server on Ubuntu 10.04 which serves NFSv4, LDAP, and Kerberos.
Autofs configuration is exposed via LDAP so I can simply configure autofs-ldap to turn on my autofs. Kerberos is for NFSv4 security and network authentication. Together this make a SSO and single home per network user. But I've met the following problems:
[LIST=1]
[*]Ubuntu 10.10 with GNOME UI works unstable when I use network user to authenticate and NFS home. The problems were in the following:
[LIST=1]
[*]on login into GNOME screen the .ICEAuthority problem appears (message "Could not update ICEauthority file /home/<username>/.ICEauthority"). But it does not appear every time I log in, and I could not dete&#1089;t any regularity
[*]the Empathy says that it cannot connect to dconf service and this issue prevents it to store any configuration except accounts
[*]Evince does not run at all. It just tells nothing except "Killed" in console (I don't know real message because I use Russian translation, but suppose that it says "Killed")
[/LIST]
I understand that Ubuntu 10.10 is unstable now, but I am not sure that these problems are the Ubuntu problems but not GNOME and/or NFSv4/Kerberos misconfiguration.
[*]Ubuntu 10.04 which runs on my laptop does not start gssd daemon automatically so I cannot use my NFSv4 shares from server until manually restart gssd (/etc/default/nfs-common file is configured properly, I've checked it few times)
[/LIST]

The main problem is Ubuntu 10.10. If it is a bug I will submit it to bug tracker. I've checked manually that my NFS works with all special file types and allows all operations, also I tried to mount with nolock option. Nothing helped.

Please advice what to do. I can perform additional tests if they will provide any information.


--
Thanks,
Alexander

---

### Post by infestator on 2010-10-13
Problem still exists in stable release.
I have noticed that dconf establishes a connection to my NFSv4:
```
tcp        0      0 192.168.1.10:59879      192.168.1.1:389         ESTABLISHED 18641/dconf-service
```
Also I had found a [bug](https://bugs.launchpad.net/ubuntu/+source/d-conf/+bug/645448?comments=all) related to Empathy problem.
Evince also began to say that it cannot connect to dconf, but now it launches.
```
$ LANG=C evince

(evince:19067): EggSMClient-WARNING **: Failed to connect to the session manager: None of the authentication protocols specified are supported


** (evince:19067): CRITICAL **: Unable to contact dconf service
```
The problem with .XAuthority remains.

The problem with GSSD was because of GSSD starts before LDAP which was on the same machine. I have solved it placing GSSD daemon start after LDAP.

---

### Post by esposj on 2010-10-15
I'm seeing similar issues on the boxes we upgraded to 10.10

Evince is returning with "killed".
ICEauthority errors from time to time.
Occational Firefox issues (not sure if its related or not yet).

Kerberos / Winbind authenticating over Active Directory NFS provided via drbd cluster for home directories..

My initial plan will be rolling the 10 machines that we upgraded to 10.10 back to 10.04

---

### Post by valentijnsessink on 2010-10-20
> **infestator said:**
> 
on login into GNOME screen the .ICEAuthority problem appears (message "Could not update ICEauthority file /home/<username>/.ICEauthority"). But it does not appear every time I log in, and I could not dete&#1089;t any regularity

Hi, the "could not update ICEauthority" message only comes up on first login; or if you lost your kerberos ticket. So logging in with ssh; then logging in with GDM will not show the message, as you have acquired your ticket with the ssh shell session.

I'm not sure why this is; currently looking into it. Did you file a bug already?

---

### Post by infestator on 2010-10-20
Hi all, thanks for replies!

> **valentijnsessink said:**
> Hi, the "could not update ICEauthority" message only comes up on first login; or if you lost your kerberos ticket. So logging in with ssh; then logging in with GDM will not show the message, as you have acquired your ticket with the ssh shell session.

I'm not sure why this is; currently looking into it. Did you file a bug already?
I am not sure that kerberos ticket is lost at the moment I log in. It should be acuired vice versa, because if it was not so I would not be able to login at all. E.g. if a local user does not have a krb ticket he cannot even "cd" into nfs home dir. But after login I have full access to my NFS home dir. May be the issue is in that the ticket is acquired after .XAuthority file is tried to be written by GDM or GNOME?

I did not submitted any bugs yet. I really don't know if this is misconfiguration issue or a bug. There is already [_the bug_](https://bugs.launchpad.net/ubuntu/+source/d-conf/+bug/645448?comments=all) which relates to dconf+NFS issue (my Empathy and Evince problems).

---

### Post by samjam on 2010-10-29
I also have this with ubuntu 10.10, NFS4 and autofs but I don't use kerberos.

I also get this in dmesg every time it happens:
[   47.451378] non-accessible hardlink creation was attempted by: gnome-session (fsuid 1001)

I just pkill -u $USER and login again and it works.

Very annoying though.

---

### Post by chimney on 2010-11-03
I'm also experiencing this problem while using NFSv4, Ubuntu 10.10, automounter and LDAP for authentication.  The error, "Could not update ICEauthority file /home/<username>/.ICEauthority" doesn't appear on the first login (after the workstation has booted), but will appear on the second login using the SAME userid.  Any further logins using the same userid appear to produce the error randomly. Has anyone else heard anything about this issue?

Chimney

---

### Post by samjam on 2010-11-04
I think it is a race condition made worse with slow file systems.

It seems that by stracing /usr/lib/gdm/gdm-session-worker (with -fp option) the error always happens. Here is the strace result.

I can't work out why these various system calls are all "unfinished". (I know what it means, but did the calls ever finished? And yet the .ICEauthority-c was eventually made.

Below is strace of a session that failed, grep'd for .ICEauthority

```

[pid  3624] stat64("/home/anne/.ICEauthority-c",  <unfinished ...>
[pid  3624] creat("/home/anne/.ICEauthority-c", 0666 <unfinished ...>
[pid  3624] link("/home/anne/.ICEauthority-c", "/home/anne/.ICEauthority-l" <unfinished ...>
[pid  3624] open("/home/anne/.ICEauthority", O_RDWR <unfinished ...>
[pid  3624] access("/home/anne/.ICEauthority", F_OK <unfinished ...>
[pid  3624] unlink("/home/anne/.ICEauthority-c" <unfinished ...>
[pid  3624] unlink("/home/anne/.ICEauthority-l" <unfinished ...>

```

^C was hit on the strace -fp after the error about failing /ICEauthority was shown.

---

### Post by wapsi on 2010-12-15
Hi,

I'm having exactly the same problem. I'm using NFSv4 (/home) and NIS for authentication.

Here is my dmesg:
[16050.814763] nautilus[26957] general protection ip:7f01d8b5a07d sp:7fffa4e77460 error:0 in libgobject-2.0.so.0.2600.0[7f01d8b2b000+49000]
[16073.802079] non-accessible hardlink creation was attempted by: gnome-session (fsuid 1000)

and I'm getting those .ICEauthority errors too. When I login first time the error appears, but it doesn't at the next time I login.

I've noticed that there appears a file .ICEauthority-c too when the error appears. That .ICEauthority-c file is mapped first like this:

-rw-r--r--   1 4294967294 4294967294        0 2010-12-15 21:51 .ICEauthority-c

after few seconds it will be mapped:

-rw-r--r--   1 myusername myusername       0 2010-12-15 21:51 .ICEauthority-c

This issue appears only with Ubuntu 10.10. I've same NFS and NIS configs in my Ubuntu 10.04 and I've no troubles like this. Maybe this is bug?

---

### Post by wapsi on 2010-12-17
Okay, for your information: this bug doesn't appear when mounting home directories with OpenAFS (+krb+openldap).

[http://www.openafs.org/](http://www.openafs.org/)

---

### Post by Artemus on 2011-03-15
Has any progress been made on this? I just upgraded a number of machines to Maverick and have the same problem. I'm running NFSv3 and NIS with IPSEC-tools plus Racoon for security. I get the .ICEauthority error rather randomly.

---

### Post by staticd on 2011-03-16
I too have noticed the same error on meerkat with NFS4 home.

message:  "Could not update ICEauthority file  /home/<username>/.ICEauthority"
this error seems to occur every alternate login.
after this error occurs, programs fail to connect to the session manager and are force quit on logout(i.e: they crash without saving their state).

```

**Failed to connect to the session manager: None of the authentication protocols specified are supported 

```I noticed that the file .ICEauthority-c was absent in the home directory on the times before the error occured.
removing the file manually ensured that the error happened the next time.

The following workaround helped me: creating .ICEauthority-c on every login ensures that the next login is smooth.

```

$cat .profile
touch .ICEauthority-c

```

---

### Post by Artemus on 2011-03-17
> **Artemus said:**
> Has any progress been made on this? I just upgraded a number of machines to Maverick and have the same problem. I'm running NFSv3 and NIS with IPSEC-tools plus Racoon for security. I get the .ICEauthority error rather randomly.

What I ended up doing (after spending a *long* time searching is adding the following to every users .gnomerc file

export ICEAUTHORITY=/tmp/.ICEauthority-$(id -un)$

That causes the .ICEauthority file to be written on the local /tmp directory rather than across the NFS mounted directory.

I've also added it to /etc/skel/.gnomerc on the NIS master server.

---

### Post by wapsi on 2011-03-17
> **Artemus said:**
> What I ended up doing (after spending a *long* time searching is adding the following to every users .gnomerc file

export ICEAUTHORITY=/tmp/.ICEauthority-$(id -un)$

That causes the .ICEauthority file to be written on the local /tmp directory rather than across the NFS mounted directory.

I've also added it to /etc/skel/.gnomerc on the NIS master server.

Yeah, that is something like I did too: I wrote 'fixnfs.sh' file, which contains following lines:

```

#!/bin/bash

# Ugly "/home over NFSv4" fix
mkdir -p /tmp/$USER.ICE
export ICEAUTHORITY=/tmp/$USER.ICE/.ICEauthority
mkdir -p /tmp/$USER.ICE/.cache
export XDG_CACHE_HOME=/tmp/$USER.ICE/.cache

```

and I put this 'fixnfs.sh' file in /etc/profile.d directory thru Puppet in all NFS client computers (Puppet is Linux central management tool).

There is no need to put something in every users' home directories, only one file per computer. :)

Hopefully this helps somebody to fix (temperarily) this issue too.

---

### Post by jalvesaq on 2011-03-18
> **infestator said:**
> on login into GNOME screen the .ICEAuthority problem appears (message "Could not update ICEauthority file /home/<username>/.ICEauthority").

I was having this problem with NIS and NFS. The problem wasn't limited to .ICEauthority. Other files with permissions 600 were also affected.

The home directories at /home had the user as owner and "users" as group. The problem was that the group "users" is common to both server and client. The solution was to create a new group in the server and change the group of the users directories to the newly created group.

---

### Post by bronger on 2011-04-12
> **jalvesaq said:**
> I was having this problem with NIS and NFS. The problem wasn't limited to .ICEauthority. Other files with permissions 600 were also affected.

The home directories at /home had the user as owner and "users" as group. The problem was that the group "users" is common to both server and client. The solution was to create a new group in the server and change the group of the users directories to the newly created group.

Could you explain more?  I mean, the group of the home directory normally is the user's own group (which shares the same name as the user). And then, why is it problematic if server and client share the same group?

By the way: Is there a Launchpad ticket for this?

---

### Post by jalvesaq on 2011-04-12
> **bronger said:**
> Could you explain more?  I mean, the group of the home directory normally is the user's own group (which shares the same name as the user). And then, why is it problematic if server and client share the same group?

The group of home directory normally is the user's own group, but I changed this by editing the /etc/adduser.conf file. Anyway, it seems that my "solution" doesn't really work. The .ICEauthority message appeared again, and I don't know what to do.

> **bronger said:**
> By the way: Is there a Launchpad ticket for this?

I think that nobody opened one yet.

---

### Post by bronger on 2011-04-14
> **jalvesaq said:**
> [...] Other files with permissions 600 were also affected.


Which other files have you seen being affected?

I'll open a ticket today or tomorrow.

---

### Post by jalvesaq on 2011-04-14
> **bronger said:**
> Which other files have you seen being affected?

I'll open a ticket today or tomorrow.

Other file affected is ~/.viminfo. The file is created by vim with no warning, but latter it can't be updated. That is, when vim is used for the first time by a new user, ~/.viminfo is created, but when a second file is edited, vim can't write to the file again. By default, vim automatically registers in this file information like what was copied into the clipboard and what was the cursor position when the file was closed.

---

### Post by bronger on 2011-04-15
I reported the bug (well, at least in the form I experience it) here: [https://bugs.launchpad.net/ubuntu/+bug/761991](https://bugs.launchpad.net/ubuntu/+bug/761991)

---

### Post by apalacheno on 2011-09-16
I spent quite some time on the net looking for useful hints that may point to the root of the problem. The problem is, there are so many different use cases and reasons why these errors appear, it's like the search for the needle in the haystack.

Alexander, I would like to come back to your offer. Even if you could propably workaround the issue, could you provide the configuration of:

**NFS (server-side):**
/etc/exports
/etc/fstab
/etc/default/nfs-kernel-server
/etc/default/nfs-common
/etc/idmapd.conf

**NFS (client-side):**
/etc/default/nfs-common
/etc/idmapd.conf

**Autofs:**
/etc/default/autofs
/etc/autofs_ldap_auth.conf
/etc/auto.*
.ldif data of the autofs LDAP tree

**NSS:**
/etc/nsswitch.conf

...these are the most important ones. To get a bigger picture the following would be helpful as well:

**LDAP:**
/etc/ldap.conf
/etc/ldap/ldap.conf

**Kerberos:**
/etc/krb5.conf

**PAM:**
/etc/pam.d/common-auth
/etc/pam.d/common-account
/etc/pam.d/common-session

Cheers,
Robert

---

### Post by apalacheno on 2011-09-18
What I found out so far is that the problem seems not to be with .ICEauthority, but with .ICEauthority-c.

If the .ICEauthority-c file is missing, I get the error message upon login complaining about a missing .ICEauthority file ('Could not update ICEauthority file /home/<username>/.ICEauthority'), althought the .ICEauthority is present. I can check this before login:

```
root@example:/home# ls -al user/ | grep ICE
-rw-------  1 user user 3940 2011-09-18 19:36 .ICEauthority
```

During login, the .ICEauthority-c file is somehow created automatically, so this file is present after login:

```
root@example:/home# ls -al user/ | grep ICE
-rw-------  1 user user 3940 2011-09-18 19:36 .ICEauthority
-rw-------  1 user user 3940 2011-09-18 19:36 .ICEauthority-c
```

No error message on the next login. But this time, the .ICEauthority-c file gets somehow removed again *during login*:

```
root@example:/home# ls -al user/ | grep ICE
-rw-------  1 user user 3940 2011-09-18 19:36 .ICEauthority
```

The error message appears again on the subsequent login. This game can be repeated infinitely.

**So, here's another solution:**

Open */home/<user>/.gnomerc* and paste the following line:

```
touch .ICEauthority-c
```

Save the file and you should be good. This will create an .ICEauthority-c file just in time upon login, so the error isn't triggered. Interestingly enough, this file gets removed again during the login process. But it does the trick nevertheless.

Could somebody confirm if this solution is working on his/her system?

Cheers,
Robert

---

