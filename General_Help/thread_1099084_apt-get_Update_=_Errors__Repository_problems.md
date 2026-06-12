---
title: "apt-get Update = Errors / Repository problems ?"
date: 2009-03-17
forum: General Help
---

### Post by Devi 710 on 2009-03-17
Hi,

I wanted to update to the latest version of Gnome-Do. I removed the current version via Synaptic, removed the 3rd party repositories for Gnome-Do from the list. Then started over from scratch.

I am still stuck with the old version of Gnome-Do 0.4.2.0 but now I get this error when I try to refresh the repositories:

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7

When I run 'sudo apt-get update' I get the following:

> Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_CA
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_CA
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [197B]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_CA                 
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [189B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_CA
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release.gpg [307B]              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Translation-en_CA            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_CA   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_CA   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_CA
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Translation-en_CA
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release.gpg 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Translation-en_CA
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release.gpg 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Translation-en_CA
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release                           
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_CA                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_CA       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_CA
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Sources                           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Sources                       
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release [46.7kB]                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Sources  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Sources
Fetched 47.0kB in 2s (20.6kB/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7
W: You may want to run apt-get update to correct these problems

:( So I guess I messed up my Repositories along the way. I am still running Gutsy 7.10 (haven't felt the need to upgrade with the last two releases, but I am looking forward to 9.04)

Anyone able to help me out?

Devi

---

### Post by Nano_ext3 on 2009-03-17
This most likely means you added the Repo to your Software Sources, but you did not add the Authentication Key.  This must be added so the Repo is properly identified.  The website where you got the PPA or Repo should have the authentication key somewhere.  Make a basic file by do "nano myrepo" in any directory you want, preferably a safe one, and paste in the garbled numbers and letters that they list when you click on the key.  Then go to Software Sources and to the "Authentication" tab , click import key , and find the file you just made.

Example.

```

Nano myRepo

```

Contents of myRepo file:

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXS1/wEEALis4to4JdgrkdRunmSTfB2tYRq99Cdcgdh9up4HzAf1yTZU1EtmETPP1Uy2
vnAFf/cCunL5VRywNJB3QOxiHdvNlijbdsa0H/fT/ulq+A4iDljUEfsaJug+dAB5uEJE0BzZ
agRjgLbFvRYtsKf3BwZizbo4XtWSAm3JSjZCGZKTABEBAAG0IkxhdW5jaHBhZCBQUEEgZm9y
IEF3biBUZXN0aW5nIFRlYW2IRgQQEQIABgUCSXqnWgAKCRBBf7ZCSCH+JPZMAJ4xW7gbpuA+
yedehvDQWdJHHUgseQCgy6NOmAyXqRKrIXWERkXw6h9TsRuItgQTAQIAIAUCSXS1/wIbAwYL
CQgHAwIEFQIIAwQWAgMBAh4BAheAAAoJEH0seiO/gQzVpSID/0FXxTSLtxPHrT7IE9eif5qJ
vjOjzcmOCXe9/3G0ctV8IfYHx0VynddjxgTqJ9WuEjMLVHRgXvK1Rw1XMlik+MeyyHrr9EWQ
DUFbUs+Yc2usRyZY8pVe2Uwy2x7lFsi6VBfo0k9jVsu1l1qBU9BhANJDUTHjR15aPYiUJiZa
13CZ
=a6Gh
-----END PGP PUBLIC KEY BLOCK-----

* This is known as the public key, and is usually located on the same page as the PPA or Repo

```



**See this website if you have more trouble:**

[]("https://help.launchpad.net/Packaging/PPA#Activating%20a%20PPA")

---

### Post by forger on 2009-03-17
try and use this perl script:
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by Nano_ext3 on 2009-03-17
As much as It might help you, I have to say I discourage scripts, because if it fails, then you might be in more hot water.  Try what I said first.

Thanks,

-Nano

---

### Post by fieroboom on 2009-03-17
> **Nano_ext3 said:**
> As much as It might help you, I have to say I discourage scripts, because if it fails, then you might be in more hot water.  Try what I said first.

Thanks,

-Nano

:agree:
Also, have a look at [this thread](http://ubuntuforums.org/showthread.php?t=1053126).
You can run the same commands:

```
gpg --keyserver subkeys.pgp.net --recv <**THE_LONG_NUMBER_FROM_YOUR_ERROR**>

gpg --export --armor <**THE_LONG_NUMBER_FROM_YOUR_ERROR**> | sudo apt-key add -

sudo apt-get update


```
This way there's no chance of error from text editor formatting that might occur.
:D
-Paul

---

### Post by Devi 710 on 2009-03-18
Thanks Guys!,

I tired Nano's method of creating an Authentication Key and adding it. It all went fine, but didn't solve the problem.

The method that Fieroboom added and linked to worked great.

:D Thanks so much for all the help. I will mark the thread solved.

Devi

---

### Post by Devi 710 on 2009-03-18
Man it's been a while. How do you mark this 'Solved" again?? I thought it was in the 'Thread Tools'. 

Still a forum noob I guess...

---

### Post by plucky on 2009-03-18
> **Devi 710 said:**
> Man it's been a while. How do you mark this 'Solved" again?? I thought it was in the 'Thread Tools'. 

Still a forum noob I guess...

That feature has been disabled in the Forums for a number of weeks,because it was causing uptime problems.Also the thanks feature.Hopefully it will come back sometime in the future,but don't hold your breath.


Good Luck


p.s use the tag feature on your original post to mark as solved.

---

### Post by Devi 710 on 2009-03-18
Thanks for the info. I've tagged it solved.

---

