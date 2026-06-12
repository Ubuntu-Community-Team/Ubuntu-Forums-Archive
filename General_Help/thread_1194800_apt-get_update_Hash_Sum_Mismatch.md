---
title: "apt-get update: Hash Sum Mismatch"
date: 2009-06-23
forum: General Help
---

### Post by mattpwest on 2009-06-23
Hi all,

I've got Ubuntu 8.04 (Hardy) running on a webserver I manage and I'm trying to **apt-get update** and **apt-get upgrade** to get the security patches for Apache that were released on 12 June ([http://www.ubuntu.com/usn/usn-787-1](http://www.ubuntu.com/usn/usn-787-1)).

Unfortunately I'm getting the following error on the update:
```
apt-get update

... <snip - all good except for> ...

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.bz2  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.

```I know from previous experience that there are problems with some bad proxies here at work, so I already have apt on all my servers configured with:
```
Acquire::http::No-Cache=True;
```I'm kinda stumped, because it was working fine 2 weeks ago before I went on leave (I usually update & upgrade weekly - last one was on 8 June - don't know if the 2 week lapse in updating could've caused a problem). Is anybody else having this problem or does anybody have any ideas on what I can try to solve it?

Any assistance would be appreciated!

Regards,
Matt

---

### Post by mattpwest on 2009-06-24
Problem solved.

I found a list of mirrors at [https://wiki.ubuntu.com/Mirrors](https://wiki.ubuntu.com/Mirrors) and switched the security lines in Apt's sources.list from:

```
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```to 

```
deb http://za.archive.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://za.archive.ubuntu.com/ubuntu hardy-security main restricted
deb http://za.archive.ubuntu.com/ubuntu hardy-security universe
deb-src http://za.archive.ubuntu.com/ubuntu hardy-security universe
deb http://za.archive.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://za.archive.ubuntu.com/ubuntu hardy-security multiverse
```So I guess there must've been a temporary problem with the default package repository? I've switched back to the original after the update and will see if it's back to normal next week.

---

