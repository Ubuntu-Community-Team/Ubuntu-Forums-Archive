---
title: "VPNC stopped working  - resolvconf error"
date: 2009-06-21
forum: General Help
---

### Post by rugbert on 2009-06-21
This is the error Im getting when I try to VP in:

resolvconf: Error: /etc/resolv.conf must be a symlink

so even tho Im "connected" Im not actually connected, so I cant connect to my network shares.

---

### Post by rugbert on 2009-07-03
bump!

can anyone help me?

---

### Post by dcstar on 2009-07-03
> **rugbert said:**
> bump!

can anyone help me?

VPNC should be creating this itself, but if not, try:

```
sudo ln /etc/resolvconf/run/resolv.conf  /etc/resolv.conf
```

---

### Post by jorvis on 2009-07-07
This is a problem for me too after doing the latest round of updates.  The problem isn't that /etc/resolv.conf doesn't exist, the problem is that it's being created/overwritten as an actual file (rather than symlink) each time you start vpnc.  I created the symlink (as suggested above) and it was removed and overwritten by a new copy of resolv.conf when I launched vpnc.

The 'vpnc' process remains running after the error but doesn't seem to actually be connected.

---

### Post by jorvis on 2009-07-07
dcstar was nearly correct in his advice.  I fixed this by removing /etc/resolv.conf and then:

ln -s /etc/resolvconf/run/resolv.conf  /etc/resolv.conf

---

### Post by onthenarrowpath on 2009-09-22
Actually, for me it required to follow the following steps (I learned from launchpad, bug #324233):

Before:

$ ls -l /etc/resolv.conf
-rw-r--r-- 1 root root 30 2009-08-16 13:38 /etc/resolv.conf

$ sudo mkdir /etc/postfix
$ sudo touch /etc/postfix/main.cf
$ sudo rm /etc/resolv.conf
$ sudo ln -s /etc/resolvconf/run/resolv.conf /etc/resolv.conf
$ ls -l /etc/resolv.conf
lrwxrwxrwx 1 root root 31 2009-08-16 13:42 /etc/resolv.conf -> /etc/resolvconf/run/resolv.conf
$ sudo reboot

After:

$ ls -l /etc/resolv.conf
lrwxrwxrwx 1 root root 31 2009-08-16 13:42 /etc/resolv.conf -> /etc/resolvconf/run/resolv.conf

Hope it helps!

---

### Post by hackmeister on 2009-09-22
> **onthenarrowpath said:**
> Actually, for me it required to follow the following steps (I learned from launchpad, bug #324233):

Before:

$ ls -l /etc/resolv.conf
-rw-r--r-- 1 root root 30 2009-08-16 13:38 /etc/resolv.conf

$ sudo mkdir /etc/postfix
$ sudo touch /etc/postfix/main.cf
$ sudo rm /etc/resolv.conf
$ sudo ln -s /etc/resolvconf/run/resolv.conf /etc/resolv.conf
$ ls -l /etc/resolv.conf
lrwxrwxrwx 1 root root 31 2009-08-16 13:42 /etc/resolv.conf -> /etc/resolvconf/run/resolv.conf
$ sudo reboot

After:

$ ls -l /etc/resolv.conf
lrwxrwxrwx 1 root root 31 2009-08-16 13:42 /etc/resolv.conf -> /etc/resolvconf/run/resolv.conf

Hope it helps!

That worked for me as well. Finally got vpnc working and can now say buh-bye to ciscovpn :guitar:

---

### Post by fatsheldon on 2009-10-16
thanks onthenarrowpath.  your instructions worked for me.

---

### Post by onthenarrowpath on 2009-10-19
Glad I could help ;-).

---

### Post by JohnTwenty on 2010-01-14
I have the very same problem and your fix is working. I restart my system and everything is fine, BUT after the next restart my symlink is gone and nothing is working!!!

Does anyone know how this can be? Why do I lose my symlink? 

Best regards 
JohnTwenty

BTW: Ubuntu 9.10 on a Asus EEEPC 1005

---

### Post by Eric B on 2010-01-22
not working for me either. on reebot:

```
$ ls -l /etc/resolv.conf
-rw-r--r-- 1 root root 327 2010-01-22 13:28 /etc/resolv.conf

```

symlink is gone.

I found a solution. It appears the NetworkManager applet was overwriting the resolv.conf symlink.

```

sudo stop
sudo aptitude remove resolvconf
sudo aptitude purge resolvconf
sudo aptitude install resolvconf
sudo NetworkManager start
```


My whole story can be found here. [http://eric-b.net/?p=71](http://eric-b.net/?p=71)

---

### Post by timwaters on 2010-02-19
> **Eric B said:**
> n
symlink is gone.

I found a solution. It appears the NetworkManager applet was overwriting the resolv.conf symlink.


Actually, it's worth saying that this did NOT work - as detailed on his blog - 
"Unfortunately, the issue has returned after a few reboots and/or a few system updates. "

so is there a real working solution?

---

### Post by mpenda on 2010-03-07
I had the same issue, or at least a similar issue.
Re-installing worked for one time. My resolv.conf file was correct for local ISP connections, then connected via VPNC and is was correct for the remote site, but when I disconnected, my local ISP settings were gone.

My band-aid was to put my local ISP settings in the "tail" file under /etc/resolvconf/resolv.conf.d
Now, the correct files are there for being just on the local ISP, and when I'm on the VPN, the resolv.conf file has the remote settings followed by the local ones. As DNS uses them in order it works fine.

---

### Post by ashwinipn on 2011-03-01
> **onthenarrowpath said:**
> Actually, for me it required to follow the following steps (I learned from launchpad, bug #324233):

Before:

$ ls -l /etc/resolv.conf
-rw-r--r-- 1 root root 30 2009-08-16 13:38 /etc/resolv.conf

$ sudo mkdir /etc/postfix
$ sudo touch /etc/postfix/main.cf
$ sudo rm /etc/resolv.conf
$ sudo ln -s /etc/resolvconf/run/resolv.conf /etc/resolv.conf
$ ls -l /etc/resolv.conf
lrwxrwxrwx 1 root root 31 2009-08-16 13:42 /etc/resolv.conf -> /etc/resolvconf/run/resolv.conf
$ sudo reboot

After:

$ ls -l /etc/resolv.conf
lrwxrwxrwx 1 root root 31 2009-08-16 13:42 /etc/resolv.conf -> /etc/resolvconf/run/resolv.conf

Hope it helps!

It is reported as a bug.... but your suggestion worked like a charm.... Thanks ... I could not understand one command what it intends to do... that is "touch".... "main.cf" also was not present in the path specified... instead I saw master.cf. Nevertheless, I gave the command you suggested and it did not give me any error notification or otherwise.... It will be of help to me if this is explained a bit.

I was having this problem with bind9... With every install/remove I would get this and associated error messages for bind9... tried complete removal of bind9 without success... some more things I had read but luckily tried your suggestion first and glad I did before removal of resolve.conf I opened it.... it had only DNS server IDs nothing else... and why it must be symlink? Anyways... problem solved... Thanks a ton...

---

### Post by jdthood on 2012-10-30
> **rugbert said:**
> This is the error Im getting when I try to VP in:

resolvconf: Error: /etc/resolv.conf must be a symlink

To fix this, run "sudo dpkg-reconfigure resolvconf" in a terminal.

---

