---
title: "NX service unavailable or access is disabled"
date: 2008-12-15
forum: General Help
---

### Post by Musicalmidget on 2008-12-15
I've got a spare machine in the house that I'm hoping to setup as a server.  For the most part it should be fine to leave the machine headless and control it via SSH, but there will be the odd occasion when I need to use a remote desktop session.

At the moment, SSH is installed and working fine.  I can connect to the server from any machine in the house and control it remotely.  I'm having problems connecting to the server with NX Client however.  I've setup nxserver on the server machine but I just can't seem to start a remote desktop session with NX Client from anywhere else.  Doing so produces an error which reads as follows.

> The NX service is not available or the NX access was disabled on host <server ip>.

I suspect the problem may be related to the public/private key authentication as this is displayed in the error details area.

```
NX> 203 NXSSH running with pid: 4564
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.15 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.
```

As yet I've been unable to find a solution to this problem myself, so any suggestions would be welcomed.

Thanks.

---

### Post by therealbrewer on 2008-12-27
bump

---

### Post by RaygionsSumta on 2009-01-29
Did you ever find the cause of this?  After a fresh installation of Ubuntu Intrepid Ibex (I have done 5 or 6 fresh OS installs in the last week on various machines), the windows NX client works a few times, then returns the message, "the nx service is not available or the NX access was disabled on host [IPAddress]" Its inexplicable, but I would really like to explick it.

---

### Post by Musicalmidget on 2009-01-29
No, I'm afraid I've never found a solution to my problem.

---

### Post by saerdna on 2009-02-07
Whenver I have this problem, I do the following.  So far, it has always fixed this error:

1 - uninstall NX

2 - remove all NX files, particularly /usr/NX/*.  This is the real key step

3 - just to be safe, the .nx directory in my home directory.

4 - reinstall

5 - Check the log files (/usr/NX/var/log) for any errors.  Repeat if anything shows up.

After that, I've always had that error message go away.

---

### Post by lokalhost on 2009-03-27
Just had this problem in centos; turns out nx was not using the client dsa key in /etc/nxserver but the one in the nx user home directory.

cat /etc/passwd | grep ^nx
 [INDENT]```
nx:x:102:103::/var/lib/nxserver/home:/usr/bin/nxserver
``` [/INDENT]


Use this key in the nx client:
[INDENT]cat /var/lib/nxserver/home/.ssh/client.id_dsa.key[/INDENT]

---

### Post by andrewfn on 2009-04-05
Yup, that was my problem as well. Thanks for a quick fix!
--Andrew

---

### Post by g0bez on 2009-07-28
Ok, so I realize that this isn't the most active thread... but I felt like after all that I went through the past hour or so demands that I post here.

My setup:
LAN (gigbit)
MacBook Pro (NX client)
Ubuntu 9.04 desktop (NX server)


My Ubuntu box has a public facing address, so I have it locked down pretty well. I'm running ssh on a non-standard port, restrict access to a set of IPs, and allow only keys (no passwords). I'm very familiar with ssh keys and am not extremely advanced, but I know my way around linux. 

That said, I made an error that I'm kicking myself for. 

I used the standard authorized_keys file, pasted in the ssh-key, and saved the file. The connection kept failing at authentication! I triple-checked all of the settings and paths, only to discover that the copy from my Mac translated incorrectly onto Ubuntu -- it put line breaks where there should've wrapped at the end of each line. 

I went thru and delete the breaks, saved the file, and it worked as expected.


Just goes to show that the devil is in the details. I'm VERY thankful for Nomachine NX free -- this is *exactly* the solution that I've been looking for, and when I take my MacBook Pro on the road, I'm able to connect without the lag of ssh -X (even with compression). 

Good luck getting this going... it is worth the work!

---

### Post by Stacktrace on 2009-11-27
Hi,
I just had this problem but it was due to my own changes to the SSH server config.

I recently added the "AllowUsers" option. But I only added my own local user. This gives the exact same error. To correct this just add "nx" user to it aswell.

The problem was that I did this a couple of days ago so I had forgot about. Gave me an hour or so of lovely troubleshooting. 

Cheers!

---

### Post by satosh on 2009-12-16
Stacktrace, thank you!

---

### Post by tylercollier on 2011-05-17
In my case, I tried the two different DSA keys (one from /etc/nxserver and one from/var/lib/nxserver/home/.ssh) but neither worked.  Instead of using one of those keys, I used the "default" key.  When you are given the chance to specify the DSA key, there is a button that says "Default".  I clicked that which changes the text in the DSA key field, and tada, it worked.  Good enough for now.

---

### Post by Stvnx7 on 2012-02-24
> **Stacktrace said:**
> Hi,
I just had this problem but it was due to my own changes to the SSH server config.

I recently added the "AllowUsers" option. But I only added my own local user. This gives the exact same error. To correct this just add "nx" user to it aswell.

The problem was that I did this a couple of days ago so I had forgot about. Gave me an hour or so of lovely troubleshooting. 

Cheers!

This is the **exact** same thing I did. Thank you so much for coming back and posting your solution. It saved me so much time.

---

### Post by oldos2er on 2012-02-24
Old thread needs its rest. Closed.

---

