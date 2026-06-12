---
title: "DRAC and Ubuntu 7.04"
date: 2007-07-18
forum: Dell  Ubuntu Support
---

### Post by scorgie on 2007-07-18
Anyone get Dell DRAC working with Ubuntu 7.04? 
If so, how did you do it?

Cheers

---

### Post by sr20ve on 2007-07-18
The drac should work independent of the OS.

---

### Post by Robstarusa on 2008-01-29
> **sr20ve said:**
> The drac should work independent of the OS.

Unfortunately, it does not.  Neither remote console or remote media work and I have a working java install.

Anyone else get this working?  My problems are in 7.10 though, not 7.04

---

### Post by jetole on 2008-02-05
Update: Ignore this and skim to my post at the bottom.

the DRAC 5 works fine when ubuntu is the guest operating system on any Dell server. I have three PowerEdge 2950 III all running ubuntu 7.10 x86_64 and the DRAC does it's job. 

Now that we have that cleared up lets move to the real probems. DRAC basically does not, I repeat does not work with firefox. You can connect to the DRAC via firefox and do most things however the two most important ones for "end of the world" recovery, remote screen, and virtual media do not work. Now dell does have tools that can be installed on the guest OS that allow you to manage it as part of the OpenManage group or whatever the hell Dell calls it. These tools will run on Red Hat and NoOSE, I mean SuSE if it is a i386 system. Basically me trying to get OpenManage to function properly on a x86_64 computer (laptop, desktop or servers) all running different versions of ubuntu just doesn't want to work.

Also before anyone tells me otherwise, I have had a dell tech in my office and spoken with several senior analysts at Dell, they all seem to have the same general consensus that Dell remote screen and virtual media do not work on firefox despite the firefox plugins existing on the card already.

---

### Post by Robstarusa on 2008-02-06
> **jetole said:**
> the DRAC 5 works fine when ubuntu is the guest operating system on any Dell server. I have three PowerEdge 2950 III all running ubuntu 7.10 x86_64 and the DRAC does it's job. 

Now that we have that cleared up lets move to the real probems. DRAC basically does not, I repeat does not work with firefox. You can connect to the DRAC via firefox and do most things however the two most important ones for "end of the world" recovery, remote screen, and virtual media do not work. Now dell does have tools that can be installed on the guest OS that allow you to manage it as part of the OpenManage group or whatever the hell Dell calls it. These tools will run on Red Hat and NoOSE, I mean SuSE if it is a i386 system. Basically me trying to get OpenManage to function properly on a x86_64 computer (laptop, desktop or servers) all running different versions of ubuntu just doesn't want to work.

Also before anyone tells me otherwise, I have had a dell tech in my office and spoken with several senior analysts at Dell, they all seem to have the same general consensus that Dell remote screen and virtual media do not work on firefox despite the firefox plugins existing on the card already.

Any other browsers that are available in ubuntu that it DOES work in?

---

### Post by jetole on 2008-04-11
Forget what I said, the DRAC 5 works for me on Ubuntu 7.10 running the 32 bit browser by using this tecgnique I just discovered. It claims to work on the Dell default browser and I made some changes since I have a 64 bit system with 32bit firefox install in /opt and I just got it to work so now I am gonna go change my underwear. Holy hell I am happy about this.

[http://blog.wazollc.com/Lists/Posts/Post.aspx?ID=10](http://blog.wazollc.com/Lists/Posts/Post.aspx?ID=10)

---

