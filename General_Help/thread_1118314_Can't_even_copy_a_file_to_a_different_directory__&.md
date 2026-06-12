---
title: "Can't even copy a file to a different directory:  &quot;omitting directory `filenamehere'&quot;"
date: 2009-04-06
forum: General Help
---

### Post by Linuxwho? on 2009-04-06
**root@ubuntu:/tmp#** cp zcs-5.0.6_GA_2314.UBUNTU8.FRANKLIN /dev
cp: omitting directory `zcs-5.0.6_GA_2314.UBUNTU8.FRANKLIN'

I want to copy this pain in the bbutt "fraklin" file that does not even execute to a differnt directory for trouble-shooting but it wont even let me copy it.  Any ideas?

---

### Post by Linuxwho? on 2009-04-06
Now it worked but it says no space left!  :mad::mad:  I have 15 gigs on this disk so it makes NO sense!

"root@ubuntu:/dev/damit# tar -xzf zc*
tar: zcs-5.0.6_GA_2314.UBUNTU8.FRANKLIN/packages/zimbra-store_5.0.6_GA_2314.UBUNTU8_i386.deb: Wrote only 8192 of 10240 bytes
tar: zcs-5.0.6_GA_2314.UBUNTU8.FRANKLIN/install.sh: Cannot write: No space left on device
tar: zcs-5.0.6_GA_2314.UBUNTU8.FRANKLIN/util/modules/postinstall.sh: Cannot write: No space left on device
tar: zcs-5.0.6_GA_2314.UBUNTU8.FRANKLIN/util/modules/getconfig.sh: Cannot write: No space left on device
tar: zcs-5.0.6_GA_2314.UBUNTU8.FRANKLIN/util/modules/packages.sh: Cannot write: No space left on device
tar: zcs-5.0.6_GA_2314.UBUNTU8.FRANKLIN/util/addUser.sh: Cannot write: No space left on device
tar: zcs-5.0.6_GA_2314.UBUNTU8.FRANKLIN/util/globals.sh: Cannot write: No space left on device
tar: zcs-5.0.6_GA_2314.UBUNTU8.FRANKLIN/util/utilfunc.sh: Cannot write: No space left on device
tar: Error exit delayed from previous errors
root@ubuntu:/dev/damit# ls

---

### Post by cdwillis on 2009-04-06
You probably shouldn't be trying to stick stuff in /dev. If you want to copy the directory try: cp -r source /whatever/destination/is

What are you trying to do anyway, maybe I can help you out?

---

### Post by Linuxwho? on 2009-04-06
> **cdwillis said:**
> You probably shouldn't be trying to stick stuff in /dev. If you want to copy the directory try: cp -r source /whatever/destination/is

What are you trying to do anyway, maybe I can help you out?

Thanks CD.  I created it in etc and it worked.  I have no idea why it that directory said out of space.  Apparently the command tar -xzf zc*  creates a directory with the same EXACT name as the tar file itself.  I was not smart enough yet to figure that out.  Ultimately I am trying to install zimbra.

---

### Post by cdwillis on 2009-04-06
If you can extract it then it should be simple to install. Change to the directory it creates and you should be able to type this to install it:

./configure
./make
./install

---

### Post by Linuxwho? on 2009-04-06
It worked.  However it seems I get stopped at each step on this.  Now it says it can't find packages.  The directions for installing zimbra says next step is:

"It's not going to work the first time, but it'll give you a list of missing dependencies. Write down all the package names it says are missing. Your list may be slightly different than mine, but whatever it is, load them. Just separate each package name with a space like this:

apt-get install libpcre3 libgmp3c2 libstdc++5"

In my case it can't even find the first package - "zimbra-ldap."  :confused:

---

### Post by cdwillis on 2009-04-06
There aren't any applications in the repositories with zimbra in them (I just checked). Can you paste the list in here?

---

### Post by Linuxwho? on 2009-04-06
> **cdwillis said:**
> There aren't any applications in the repositories with zimbra in them (I just checked). Can you paste the list in here?

Sure.  

"**root@ubuntu:/home/owner#** a[COLOR="Navy"]pt-get install zimbra-ldap zimbra-logger zimbra-mta zimbra-snmp zimbra-store zimbra-apache zimbra-spell zimbra-proxy zimbra-archiving zimbra-cluster zimbra-core[/COLOR]
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package zimbra-ldap
**root@ubuntu:/home/owner#**"

---

### Post by cdwillis on 2009-04-06
That looks like the packages that should be installing from the package you downloaded. If you go into the directory it extracted to and type "sudo ./install.sh" what happens?

---

### Post by Linuxwho? on 2009-04-07
Hmmm..  seems it wants me to fix the hosts file first..I am not sure exactly how to syntax that host file?

**root@ubuntu:/etc/zcs-5.0.6_GA_2314.UBUNTU8.FRANKLIN#** ./install.sh

Operations logged to /tmp/install.log.4376
Checking for existing installation...
    zimbra-ldap...NOT FOUND
    zimbra-logger...NOT FOUND
    zimbra-mta...NOT FOUND
    zimbra-snmp...NOT FOUND
    zimbra-store...NOT FOUND
    zimbra-apache...NOT FOUND
    zimbra-spell...NOT FOUND
    zimbra-proxy...NOT FOUND
    zimbra-archiving...NOT FOUND
    zimbra-cluster...NOT FOUND
    zimbra-core...NOT FOUND


PLEASE READ THIS AGREEMENT CAREFULLY BEFORE USING THE SOFTWARE.
ZIMBRA, INC. ("ZIMBRA") WILL ONLY LICENSE THIS SOFTWARE TO YOU IF YOU
FIRST ACCEPT THE TERMS OF THIS AGREEMENT. BY DOWNLOADING OR INSTALLING
THE SOFTWARE, OR USING THE PRODUCT, YOU ARE CONSENTING TO BE BOUND BY
THIS AGREEMENT. IF YOU DO NOT AGREE TO ALL OF THE TERMS OF THIS
AGREEMENT, THEN DO NOT DOWNLOAD, INSTALL OR USE THE PRODUCT.

License Terms for the Zimbra Collaboration Suite:
  [http://www.zimbra.com/license/zimbra_public_eula_2.1.html](http://www.zimbra.com/license/zimbra_public_eula_2.1.html)


Press Return to continue


  [COLOR="Sienna"]ERROR: Installation can not proceeed.  Please fix your /etc/hosts file
  to contain:[/COLOR]

  <ip> <FQHN> <HN>

  Where <IP> is the ip address of the host,
  <FQHN> is the FULLY QUALIFIED host name, and
  <HN> is the (optional) hostname-only portion

[email]root@ubuntu:/etc/zcs-5.0.6_GA_2314.UBUNTU8.FRANKL[/email]IN#

---

### Post by Linuxwho? on 2009-04-07
Here is what it looks like right now..the hosts file that is..

---

### Post by cdwillis on 2009-04-07
I wish I could be more help. I found a guide for you, maybe it can help:

[http://wiki.zimbra.com/index.php?title=Ubuntu_8.04_LTS_Server_(Hardy_Heron)_Install_Guide](http://wiki.zimbra.com/index.php?title=Ubuntu_8.04_LTS_Server_(Hardy_Heron)_Install_Guide)

---

### Post by Linuxwho? on 2009-04-07
Thanks.  That's the one I am using.  Its a bit ambiguous to me - for beginners I mean.

---

