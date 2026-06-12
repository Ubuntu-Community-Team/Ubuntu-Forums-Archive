---
title: "Dell CERC 6 SATA"
date: 2007-07-03
forum: Dell  Ubuntu Support
---

### Post by jnusa on 2007-07-03
Hi

I currently using a Dell CERC 6 SATA Raid controller (aka. Adaptec 2610sa) on Ubuntu 7.04. I administrate the controller with afacli, but the tool is very limited. Does anyone know how to get the Storman utility to work under Ubuntu or is there any other 3rd. part software to manage these controllers? I've tried both dell, adaptec and Hp's tools for this controller, however none worked. No Debian packages exists and I had to use Alien to convert them. Some scripts probably failed due to the convertion. 

Any information is greatly appriciated!

Regards jnusa

---

### Post by sr20ve on 2007-07-03
What kind of a system is it?

Have you tried Server Administrator?

Dell OpenManage Server Administrator Managed Node, Multi OS, Multi Language, Multi System, v.5.1, A00
[http://ftp.us.dell.com/sysman/OM_5.1_ManNode_LIN_A00.tar.gz](http://ftp.us.dell.com/sysman/OM_5.1_ManNode_LIN_A00.tar.gz) (89MB)

---

### Post by jnusa on 2007-07-04
Hi sr20ve

It's just a basement server, hosting source code svn, my master thesis project and normal pictures, videos etc. Runs on a P-M platform with ubuntu 7.04 - nothing fancy. The 2610sa was $85 on ebay and I could resists the hw raid compared to sw raid. 

Thanks for the link - I'll try it out today.

/jnusa

---

### Post by jnusa on 2007-07-04
Hmm  - doesn't seem that the setup.sh script supports debian distribution. A couple of '(' errors and a signal error - perhaps I could just use some of the RPM packages and use Alien to convert?

---

### Post by neptho on 2007-07-04
> **jnusa said:**
> Hmm  - doesn't seem that the setup.sh script supports debian distribution. A couple of '(' errors and a signal error - perhaps I could just use some of the RPM packages and use Alien to convert?

Everybody uses bash.  Debian and Ubuntu use dash.

Try this:

```
%sudo dpkg-reconfigure dash
```

Then choose 'No' to allow bash to take over the symlink for /bin/sh - or just run 'sudo ln -sf /bin/bash /bin/sh'.

---

### Post by jnusa on 2007-07-08
I've tried at run reconfigure bash - Now i get a "Unsupported system (sysid=)" - You probably can't install the utilities noname server. Too bad.

---

### Post by neptho on 2007-07-08
That's bizarre.  It's probably trying to run some other embedded tool.

---

### Post by jnusa on 2007-09-12
Problem solved - Adaptec Storage Manager Software 4909 works like a charm. :guitar: 
Follow this howto:
[http://lists.us.dell.com/pipermail/linux-poweredge/2006-October/028050.html](http://lists.us.dell.com/pipermail/linux-poweredge/2006-October/028050.html)
Still no spindown option though :confused:

---

### Post by himey on 2007-10-19
I have the storagemanager installed, but I get the error that no controllers are found "no controllers were found in this system". I am running the same dell raid card, with 4.30.01 of storagmanager (couldnt find the one listed in the link) I did find one reference that said that the default aacraid driver wouldnt work.

[http://ask.adaptec.com/cgi-bin/adaptec_tic.cfg/php/enduser/std_adp.php?p_sid=c71yn6Rh&p_lva=&p_faqid=13711](http://ask.adaptec.com/cgi-bin/adaptec_tic.cfg/php/enduser/std_adp.php?p_sid=c71yn6Rh&p_lva=&p_faqid=13711)

Any help would be appreciated.

---

