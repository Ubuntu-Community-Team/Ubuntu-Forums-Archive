---
title: "Default permissions for file creation"
date: 2020-05-07
forum: Desktop Environments
---

### Post by entropy1 on 2020-05-07
I am running Ubuntu 20.04. When I create a new file, say with LibreOffice Calc, the permissions of that file are
```
-rw-rw-r--
```
What can I do so that the file is automatically created with the permissions being
```
-rw-------
```

---

### Post by Holger_Gehrke on 2020-05-07
The search term to find what you're looking for is 'umask'.

Holger

---

### Post by entropy1 on 2020-05-07
Thank you. **Where** should this be set? I already set it to 077 in
.bashrc
.gnomerc
.profile
but this does not affect the behavior of LibreOffice when creating files.

---

### Post by entropy1 on 2021-04-23
I am still wondering about this in standard Ubuntu. It's still an issue in 21.04. Specifically, in which file should the desired umask 077 be set so that all new files created will have permissions set to
```
-rw-------
```
As I mentioned before, setting the umask in
.bashrc
.gnomerc
.profile
does not work even after logging out and logging back in.

---

### Post by SeijiSensei on 2021-04-24
I changed the umask in ~/.profile overriding the default 022 with 077. Then I ran
```

seiji@Linux:~$ source .profile
seiji@Linux:~$ touch test
seiji@Linux:~$ ls -l test
-rw------- 1 seiji seiji 0 Apr 24 10:28 test

```
Seems to work as advertised.

---

### Post by entropy1 on 2021-06-05
I get the same result as SeijiSensei when I create a new file with touch.

But if I create the file with gedit, I still get
```
-rw-rw-r--
```

So my question still stands.

---

### Post by TheFu on 2021-06-05
That's clearly a bug in gedit and has been for years.  Open a bug with the Gnome guys for ignoring a proper umask set in the files which should be run at login, BEFORE any GUI session begins.

[https://ubuntuforums.org/showthread.php?t=2364921](https://ubuntuforums.org/showthread.php?t=2364921)

---

### Post by Morbius1 on 2021-06-06
The bug is in [s]Poettering[/s] ... erm ... systemd.

If Nautilus and gedit is the issue do this - but note that it will not do jack for LibreOffice so it does not answer the original question. And don't forget to logoff and log back in again: 

[URL="https://askubuntu.com/questions/1322628/how-to-set-umask-to-u-rwx-g-rwx-o-rx-for-all-ways-of-logging-in-without-root-pri"]https://askubuntu.com/questions/1322628/how-to-set-umask-to-u-rwx-g-rwx-o-rx-for-all-ways-of-logging-in-without-root-pri

[/URL]

---

### Post by philhughes on 2021-06-06
See the link below for a discussion of this.

For Ubuntu >= 20.04, you need to edit /etc/login.defs.

You will need to edit two entries:

UMASK 077

USERGROUPS_ENAB no

As noted in the file, if you do not change USERGROUPS_ENAB from the default "yes", then user permissions will be used as group permissions, eg 077 will become 007.

However, again as noted in the file, changing USERGROUPS_ENAB has other consequences.

You need to reboot for this to take effect

This works for gedit and LibreOffice on 21.04 at least.

[https://askubuntu.com/questions/929439/how-to-set-default-umask-in-ubuntu-17-04](https://askubuntu.com/questions/929439/how-to-set-default-umask-in-ubuntu-17-04)

---

### Post by entropy1 on 2021-06-11
Thank you, philhughes. This worked for me. Thread marked as solved.

---

### Post by TheFu on 2021-06-11
> For Ubuntu >= 20.04, you need to edit /etc/login.defs.

This is wrong (not incorrect) on so many levels. This is a complaint that Canonical allowed it to happen at all. 

Users of Unix systems should have complete control over their settings and not need admin rights to modify those. It is a core part of The Unix Philosophy.  The only times when locking down end users is appropriate, is when in a highly restricted, closed, environment.  Certainly not a default setting.  Some fundamental things need to be part of Linux. This is one.

A bug report is necessary.

---

### Post by philhughes on 2021-06-13
If you want to avoid the consequences on useradd and userdel of changing the USERGROUPS_ENAB entry *and* make the change on a per user basis, you can use the GECOS method described in the askubuntu article.

However, there is no need to edit /etc/pam/d/login as described there and in "man pam_umask", since pam_umask.so is loaded from /etc/pam.d/common-session (at least in Ubuntu >= 20.04). So:

Make sure that /etc/pam.d/common-session contains the line:

session optional                        pam_umask.so

Then:

```
sudo chfn --other='umask=077' <username>
```

(This assumes there are no existing "other" field entries.)

A reboot is required.

This still requires superuser permissions, since changing the GECOS "other" field requires that.

---

