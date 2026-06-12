---
title: "NXClient CUPs Printing help"
date: 2008-12-16
forum: General Help
---

### Post by _UsUrPeR_ on 2008-12-16
Hey, guys. Trying to get CUPS printing to work with NXclient.

Here's how it should work: I log a client on to an NXserver with NXclient (known as FreeNX or !M (nomachine). From there, the server should be able to see any shared CUPS printers on the client that th client has specified as a shared printer. The server should then be able to print to the client's shared printer.

I am running in to a problem when I start NXclient and try to connect to the server.

While NX client connects and works fine, NX client pops a window showing the following error:

```
Can't launch CUPS server
```

Here's the error that pops in /var/log/messages:

```
Dec 16 14:55:39 ltsp kernel: [1308448.013516] audit(1229457339.536:66): type=1503 operation="inode_permission" requested_mask="r::" denied_mask="r::" name="/home/<user>/.nx/cups/cupsd.conf" pid=13845 profile="/usr/sbin/cupsd" namespace="default"
```

I have tried chmodding cupsd.conf to 755 with no luck. Strangely enough, the CUPS server is up and running:

```
root@ltsp:/usr/lib/cups/backend# /etc/init.d/cupsys start
 * Starting Common Unix Printing System: cupsd                        [ OK ]
```

---

### Post by Ricardo.Diaz on 2009-10-08
Try to disable apparmor

I've got the same problem and disbling apparmor service it woks.

To do this: sudo service apparmor stop

then, try to connect

---

