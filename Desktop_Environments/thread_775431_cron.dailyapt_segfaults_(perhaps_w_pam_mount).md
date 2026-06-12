---
title: "cron.daily/apt segfaults (perhaps /w pam_mount)"
date: 2008-04-30
forum: Desktop Environments
---

### Post by der_hede on 2008-04-30
I'm running Hardy, 8.04, and I get daily mail from cron:

[INDENT]Subject: Anacron job 'cron.daily' on [computername]

/etc/cron.daily/apt:
Segmentation fault
Segmentation fault
Segmentation fault
[/INDENT]

The segfaults happen while running:

sudo -u "$admin_user" gconftool ...

in the following script region:
#set the proxy based on the admin users gconf settings

I tried running sudo -u [username] (as root) manually and it segfaults independent of the started program:
[INDENT][username]@[computername]:~$ sudo su -
[sudo] password for [username]: 
root@[computername]:~# sudo -u [username] less
Segmentation fault[/INDENT]

I tried to debug it, but I have no experience with gdb so far:

[INDENT]root@[computername]:~# gdb sudo
GNU gdb 6.8-debian
[...]
(no debugging symbols found)
(gdb) run -u [username] gconftool --get /system/http_proxy/use_http_proxy
Starting program: /usr/bin/sudo -u [username] gconftool --get /system/http_proxy/use_http_proxy
(no debugging symbols found)
[17 more lines deleted]
(no debugging symbols found)

Program received signal SIGSEGV, Segmentation fault.
---Type <return> to continue, or q <return> to quit---
0x0805299e in ?? ()
(gdb) 
(gdb) backtrace
#0  0x0805299e in ?? ()
#1  0x08082ac0 in ?? ()
#2  0x00000008 in ?? ()
#3  0xbf8f2e98 in ?? ()
#4  0xb7c14ea4 in ?? () from /lib/security/pam_mount.so
#5  0x080844d0 in ?? ()
#6  0xb7c1c5ee in ?? () from /lib/security/pam_mount.so
#7  0x00000008 in ?? ()
#8  0xb7f5b89f in pam_get_item () from /lib/libpam.so.0
#9  0xb7c16381 in ?? () from /lib/security/pam_mount.so
#10 0x00000001 in ?? ()
#11 0xbf8f2ee8 in ?? ()
#12 0xbf8f2ee4 in ?? ()
#13 0x00000000 in ?? ()
(gdb) quit
The program is running.  Exit anyway? (y or n) y
[/INDENT]

Maybe it's because I'm using pam_mount to mount my LUKS encrypted home-dir while user-login?
But why I can use sudo as a normal user but not as root to get normal user rights?

---

### Post by bowmasters on 2008-07-29
I get the same daily cron email and it is starting to be a problem because the way we have our setup, it gets forwarded to the other admins and I think they might be getting tired of receiving the emails too.

If cron daily is seg faulting every day, does that mean it isn't doing its daily maintenance? I'm sure this will have some serious negative consequences sometime down the line.

---

### Post by bowmasters on 2008-07-29
Looking into it, is it probably a hardware problem on my end.

---

### Post by 68Spider on 2008-07-30
I get the same thing. Any kind of "sudo -u userid cmd..." from root gives me the SEGV. I do have common-pammount set up to mount my home directory when logging in.

---

### Post by elesueur on 2008-09-11
I've also got this problem...

My machine is setup for LDAP authentication, and also to mount home directories using NFS.

The problem seems to be with the script trying to find the admin user. It finds it from the local admin group. If that user is not currently logged in, then a home directory doesn't exist.

doing and strace on sudo -s -u <adminusername> shows that immediately before the SIGSEGV, sudo tries to stat /home/<adminusername> and then on my machine, it also tries to open /usr/share/locale-gen/en_AU.UTF-8/LC_MESSAGES/Linux-PAM.mo which fails with ENOENT (no such file or directory). It then tries various other locations for Linux-PAM.mo, all failing before the final SIGSEGV.

Linux-PAM.mo exists on my machine in /usr/share/locale-langpack/en/LC_MESSAGES and copying that file into did not solve the problem...

However, creating a home directory for the admin user somewhere other than /home (because this is automounted) and modifying /etc/passwd to use this home directory, solves the problem.

Edit: Another solution is to change the user in the admin group... edit /etc/group, find the line which starts with admin, and change the username to root.

---

### Post by EmptyCinema on 2009-02-20
A bug has been filed on this: [https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/234727](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/234727)

---

