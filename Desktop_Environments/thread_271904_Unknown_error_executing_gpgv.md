---
title: "Unknown error executing gpgv"
date: 2006-10-05
forum: Desktop Environments
---

### Post by Hi-Teck on 2006-10-05
On a recent new install of Xubuntu i have been getting the following error when running apt-get update: ](*,) 

```
W: GPG error: http://archive.canonical.com dapper-commercial Release: Unknown error executing gpgv
W: GPG error: http://security.ubuntu.com dapper-security Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com dapper Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com dapper-updates Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com dapper-backports Release: Unknown error executing gpgv
W: You may want to run apt-get update to correct these problems

```

I know it is something to do with the GPG Key for that sites. I have been trying to add the new keys with the following commands:

```
gpg –keyserver subkeys.pgp.net –recv KEY
```
```
gpg –export –armor KEY | sudo apt-key add -
```

I know to replace "KEY" with the real key but how do you find the key?

I have also the following questions:

Is there any other sites I can use in instead of the ones giveing me the error?
Do the errors affect anything...if not can I just ignore the error and continue using the sites to install packages?

---

### Post by crouton on 2006-10-17
Check your system date.  I just installed Dapper from the LiveCD and found I was getting same errors, and then saw the 'blah is 27012980s in the future' message when installing the openssh-server package.  Changing the date/time fixed the issue.

---

