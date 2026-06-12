---
title: "Trouble with Medibuntu's GPG Key?"
date: 2009-01-26
forum: General Help
---

### Post by simucal on 2009-01-26
Something screwed up while I was in the process of adding the Medibuntu repository to my Sources.list and now, no matter what I do, I can't seem to to get the security key for Medibuntu installed on my keyring and properly snag packages from them.


Originally I typed:
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
``` 

I can verify that the contents of this file is correct:
```
## Medibuntu - Ubuntu 8.10 "intrepid ibex"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ intrepid free non-free
#deb-src http://packages.medibuntu.org/ intrepid free non-free

```

Then, I type: 
```
**simucal@simucal-desktop:/etc/apt$ sudo apt-get install medibuntu-keyring**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  medibuntu-keyring
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3448B of archives.
After this operation, 49.2kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Install these packages without verification [y/N]? y 
Selecting previously deselected package medibuntu-keyring.
(Reading database ... 130895 files and directories currently installed.)
Unpacking medibuntu-keyring (from .../medibuntu-keyring_2008.04.20_all.deb) ...
Setting up medibuntu-keyring (2008.04.20) ...
OK


```

While this step seems like it goes fine, I suspect it does not.  Because now when I type apt-get update.. all repositories will update fine except it will hang at:

91% [Connecting to packages.medibuntu.org (2a01:e0b:1:82:21c:c0ff:fe27:9561)]

For a long time... eventually it times out and I get this error:
```
Fetched 3228kB in 2min1s (26.5kB/s)
Reading package lists... Done
W: GPG error: http://packages.medibuntu.org intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

```

Why is it doing this and how can I resolve it?  You saw above I installed the medibuntu-keyring, and I have attempted to update after that?  What else can I do?

---

### Post by adult swim on 2009-01-26
try running this from terminal
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

---

### Post by simucal on 2009-01-26
> **adult swim said:**
> try running this from terminal
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

Ok, I ran:

```
simucal@simucal-desktop:/etc/apt$ **wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -**

OK

```

And I get this message after it sat at 91% for packages.medibuntu.org again (and waited for a long time).
```

Get:1 http://packages.medibuntu.org intrepid Release.gpg [197B]                
Ign http://packages.medibuntu.org intrepid/free Translation-en_US
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_US
Get:2 http://packages.medibuntu.org intrepid Release [11.7kB]
Hit http://packages.medibuntu.org intrepid/free Packages
Hit http://packages.medibuntu.org intrepid/non-free Packages
Fetched 198B in 2min0s (2B/s)
Reading package lists... Done

```


So, looks like no explicit error.  However, if I rerun apt-get update.. it takes forever on 91% packages.medibuntu.org.  Something still feels wrong with it?'

Also, if I try to install packages from [packages.medibuntu.org]... it takes me forever.  I've been sitting at 0% for w32codecs for a loooooong time.  All other repositories go snappy.

---

### Post by adult swim on 2009-01-26
that is strange, i just ran it on my computer and it worked.  i dont know if you being in /etc/apt when you ran it has something to do with it not working or not.  try going to system>administration>software sources and then go to the authentication tab and see if there is a medibuntu key in there.

---

### Post by simucal on 2009-01-26
> **adult swim said:**
> that is strange, i just ran it on my computer and it worked.  i dont know if you being in /etc/apt when you ran it has something to do with it not working or not.  try going to system>administration>software sources and then go to the authentication tab and see if there is a medibuntu key in there.

I looked and saw it there.  Is there a way to manually wipe my keyring?

---

### Post by sci50514 on 2009-02-07
> **simucal said:**
> I looked and saw it there.  Is there a way to manually wipe my keyring?

in terminal:

dpkg --purge medibuntu-keyring

follows medibuntu instruction to add back the key.

---

