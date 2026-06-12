---
title: "No root terminal"
date: 2006-02-25
forum: Desktop Environments
---

### Post by dgermann on 2006-02-25
Hi--

I messed something up, and perhaps you have an idea how I can fix it.

The problem: When I go to Applications/System Tools/Root Terminal, the enter password screen comes up and when I enter it, nothing more happens. Same thing if I go to System/Administration/Services.

The clues: I have been trying to install some method of networking my Ubunut 5.10 box with my Red Hat 9 server. I have been playing with NFS, NIS, and LDAP. Someplace in the middle of all this I lost this functionality.

I decided to try to reverse my steps. When I entered the following command (yes, I can get a regular terminal) I get these results:

```

doug@doug2:~$ sudo ./rc-config netfs off
Password:
Password:
LDAP Password:
Password:

```

That is, it asked for my password 4 times, and I entered it 4 times, and then it did the command. (rc-config is a script someone posted here to do what chkconfig does on red hat).

I have disabled or removed all of these via apt-get remove and rc-config [service name] off all of these:
ldap-utils, 
libpam-ldap, 
libnss-ldap, 
nfs-common, 
netfs

My idea: there was something here about some app asking for passwords twice, and I suspect this is somehow related.

Any ideas?

Thanks!

---

### Post by gruepig on 2006-02-26
Sounds like you have a messed up pam config.  

If you want to try authenticating with local unix passwords (/etc/passwd) first and then fallback to ldap, /etc/pam.d/sudo should be a symlink to /etc/pam.d/ldap.settings (or something like that).  In this file, you'll want lines like "auth sufficient pam_unix.so", "account sufficient pam_unix.so", and "sessions sufficient pam_unix.so" before any corresponding ldap lines.

If you want to avoid ldap entirely (for sudo), /etc/pam.d/sudo should read:

```

@include common-auth
@include common-account

```

where common-auth should be "auth required pam_unix.so nullok_secure" and common-account should be "account required pam unix.so".

Hope that helps.

---

### Post by dgermann on 2006-02-26
gruepig--

Wonderful! Thanks for giving me my computer back!

Here's what I did, following your clues:
1. Commented out the lines I added yesterday to /etc/pam.d/sudo. This one fixed it.

2. Also commented-out the lines I added in common-password, common-auth, common-account, and common-session, just to make sure I covered all my tracks, at least in this directory.

(I found no ldap.settings file. I did find /etc/ldap/ldap.conf, and also commented-out the lines I had added there yesterday).

Thanks gruepig! \\:D/

---

### Post by gruepig on 2006-03-01
You're welcome.  Glad you have your computer back.

---

### Post by dgermann on 2006-03-05
gruepig and all--

Well, I did it again! :(  Or something like it. :???: 

I was uninstalling all the junk I put into the server and this client machine and again lost the ability to get root-user things in the System and other menus to come up. I was able to get a plain terminal to come up and tested it by typing "sudo apt-get -s install junk" and it returned--
```

unable to lookup doug2 via gethostbyname()

```

I was able to get my computer functionality back by renaming the /etc/nsswitch.conf file, having earlier renamed it to /etc/nsswitch.conf.disabled.

So my question is this: is there a way to clean up my computer and get rid of this nss stuff I installed, or am I best to just leave well enough alone?

Thanks!

---

### Post by dgermann on 2006-03-05
Or maybe I need the nsswitch file, but if so, I wonder what it should contain?

Anybody got a plain vanilla one, out of the box?

---

### Post by gruepig on 2006-03-11
```

$ cat /etc/nsswitch.conf
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

---

