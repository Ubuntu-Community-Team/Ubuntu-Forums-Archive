---
title: "NFS &amp; NIS: permission denied"
date: 2006-02-26
forum: Desktop Environments
---

### Post by dgermann on 2006-02-26
Hi--

Hope you can help me--I've got a good 25-30 hours in on this so far and feel like I am getting close, but still going in circles.

The network I am setting up will be about 4 desktop users and a server. The server is Red Hat 9.0 and the desktops are Ubuntu 5.10.

I am able to mount an nfs drive, but when I do an ls -alh, all the directories beyond the directory mounted say "Permission denied." (In other words, the mountpoint is /sam and the directoy mounted is  vol22. I can list all the files and directories at /sam/vol22 (and even open some files there), but if I do ls -alh /sam/vol22/data, all its directories and files are "permission denied.")

Here is how far I have gotten after this saga:
```

root@doug2:/home/doug # rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp    858  status
    100024    1   tcp    861  status
    100007    2   udp    869  ypbind
    100007    1   udp    869  ypbind
    100007    2   tcp    872  ypbind
    100007    1   tcp    872  ypbind
    100021    1   udp  32874  nlockmgr
    100021    3   udp  32874  nlockmgr
    100021    4   udp  32874  nlockmgr
    100021    1   tcp  32776  nlockmgr
    100021    3   tcp  32776  nlockmgr
    100021    4   tcp  32776  nlockmgr
root@doug2:/home/doug #


root@doug2:/home/doug # rpcinfo -p samba1
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  32768  status
    100024    1   tcp  32768  status
    391002    2   tcp  32769  sgi_fam
    100009    1   udp    742  yppasswdd
    100011    1   udp    929  rquotad
    100011    2   udp    929  rquotad
    100011    1   tcp    932  rquotad
    100011    2   tcp    932  rquotad
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100021    1   udp  33223  nlockmgr
    100021    3   udp  33223  nlockmgr
    100021    4   udp  33223  nlockmgr
    100005    1   udp  33224  mountd
    100005    1   tcp  32959  mountd
    100005    2   udp  33224  mountd
    100005    2   tcp  32959  mountd
    100005    3   udp  33224  mountd
    100005    3   tcp  32959  mountd
    100004    2   udp    765  ypserv
    100004    1   udp    765  ypserv
    100004    2   tcp    768  ypserv
    100004    1   tcp    768  ypserv
    100007    2   udp    995  ypbind
    100007    1   udp    995  ypbind
    100007    2   tcp    998  ypbind
    100007    1   tcp    998  ypbind
 600100069    1   udp   1020  fypxfrd
 600100069    1   tcp   1022  fypxfrd
root@doug2:/home/doug #

```

samba1 is the server, doug2 is the client.

The /etc/fstab for this directory is:

```

samba1:/vol22   /sam/vol22      nfs     rw,hard,intr              0       0

```

On doug2, id returns a uid=1000(doug) (among other things, and on samba1, it returns uid=500(doug). I thought NIS made them see it as the same uid....

So, what suggestions do you have to help me? Thanks, many, many thanks!

---

