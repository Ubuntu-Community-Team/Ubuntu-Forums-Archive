---
title: "Synaptic corrupted?"
date: 2009-02-04
forum: General Help
---

### Post by weedwacker on 2009-02-04
Hi, All--
Need help restoring Synaptic Package Manager.
I may have lost it due to a power surge when a power failure occured in the neighborhood.

I click to open Synaptic and the password window opens, I then enter password, click OK and then nothing.  If I try to open again the password window does not appear.  Sometimes I get a flicker in the taskbar.  I can open Add/Remove.  I have rebooted, but get the same results. Tried various suggestions I found to no avail.

I did type into Terminal: sudo synaptic and got the following:

 stanz@stanz-desktop:~$ sudo synaptic
[sudo] password for stanz: 
terminate called after throwing an instance of 'Xapian::DatabaseCorruptError'
Aborted
stanz@stanz-desktop:~$ 

Looks like corruption to me.  Suggestions on how to recover Synaptic?
Thanks.

---

### Post by gavinjb on 2009-02-04
I would try rebuilding your package database that would hopefully fix it, never done a rebuild myself but I know of people with similar issues that this has helped, if you do a google you should find how to do this.

Gavin,

---

### Post by weedwacker on 2009-02-07
Hey, All!
Thanks to all who took a look at my post.
In the meanwhile I decided to re-install my Ubuntu Ibex.  Never did figure out how to correct the corrupted Synaptic.

Now I cannot remember if I had tried to un-install Synaptic so that it could be reinstalled.  Oh, well.

---

### Post by cariboo on 2009-02-07
Instead of reinstalling why not completely remove synaptic and then reinstall it. In a Applications--Accessories-->Terminal type:

```
sudo apt-get purge synaptic
```

to completely remove it, and:

```
sudo apt-get install synaptic
```

to reinstall.

Jim

---

### Post by bayvista on 2009-02-16
Hi,

I tried that but still have no synaptic. Any other suggestions other than a reinstall?

Problem solved - I had tried to install Fingerprint Reader - fprint-demo. This totally stuffed up my password checking and Synaptic. Since removing the change to user authentication file /etc/user.d/common-auth, synaptic now works OK

---

### Post by Matoridi on 2009-05-23
I got the same problem after a system crash... On Ubuntu 9.04 64 bits.

I never installed fprint...

I tries uninstalling and reinstalling synaptic, with no improvements.

I tried to find other solutions on this forum and elsewhere (french ubuntu forum,Google) but I got nothing...

---

### Post by ridowan007 on 2009-06-14
I have a even beter problem. My synapt,apt,update manager,ubuntu-tweke nothing is working. In terminal all is saying segmant fault. I am using ubuntu 9.04 32 bit. I dont have Internet for some day. But today I take it  & getting this problem. Please help.


[B]sudo apt-get check 
Segmentation faultsts... 0%
[/B]

---

### Post by Zannax on 2009-06-16
I had a similar problem: root filesystem was completely full (some automatic backup filled it up), and the update manager failed; the errpr was:

"package database corrupted" (or something similar: it's in a different language...).
Synaptic too aborted with the same error.

After freeing up some space in the root filesystem, I issued:

sudo apt-get install -f

and everything was ok again...

---

