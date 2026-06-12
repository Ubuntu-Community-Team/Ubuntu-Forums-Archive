---
title: "Series of Errors that seem connected I think"
date: 2009-05-05
forum: General Help
---

### Post by Orca_ Kuhn on 2009-05-05
So, I installed Ubuntu(8.04 + updates) on a friends computer.  However, they have had a series of errors which I feel are connected, but unfortunately, am too inexperienced to figure out how or communicate to them how to fix them properly.
Keep in mind this is a fresh install of 8.04 with nothing on it so far cept what comes with it.
1) Mouse.  Freezes at random, won't work until a restart. Even if unplugged and replugged it requires a restart to work.
2) Videos Online.  Won't appear, shows only a blackbox with no interaction buttons either.  Seems like it should be there, but isn't. 
3) Skype. Tried to download the version for Linux. Instead got: "
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."  Of course, the updates didn't work.
4)Dual booting with Windows XP.  Hah, that worked well. I had to destroy XP to let Unbuntu on even after giving XP 90% paritition space, it wouldn't allow Ubuntu.  Now that computer has 1 operating system and it's nto Windows.

I much appreciate any help, I myself am fairly new to Linux, though I run it quite fine and read as much of the guides as I can but I can't understand what's going wrong for my friend.
Many thanks in advance.

---

### Post by Orca_ Kuhn on 2009-05-05
Update, tried to update and errors:
Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 56 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'

and 

me@me-desktop:~$ sudo apt-get install
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

Please tell em what I'm doing wrong?

---

### Post by zvacet on 2009-05-05
For videos online you probably need flash.Go to the applications>accessories>terminal and in terminal type

```
sudo apt-get install ubuntu-restricted-extras
```

That will give you flash,java,multimedia plugins...

For Skype you have to add medibunru repo to your source list.Do it this way

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

When you are done go to the system>admin>synaptic and in search box type skype and synaptic will find package.Mark it for install and install it.

---

### Post by zvacet on 2009-05-05
Run in terminal 

```
cat /etc/apt/sources.list
```

and post output here.

---

### Post by Orca_ Kuhn on 2009-05-06
This:


```
allie@allie-desktop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for allie: 
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
```and this:

```

allie@allie-desktop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list--output-document=/etc/apt/sources.list.d/medibuntu.list](http://www.medibuntu.org/sources.list.d/hardy.list--output-document=/etc/apt/sources.list.d/medibuntu.list)
[sudo] password for allie: 
--16:33:51--  [http://www.medibuntu.org/sources.list.d/hardy.list--output-document=/etc/apt/sources.list.d/medibuntu.list](http://www.medibuntu.org/sources.list.d/hardy.list--output-document=/etc/apt/sources.list.d/medibuntu.list)
           => `medibuntu.list'
Resolving [www.medibuntu.org]("http://www.medibuntu.org")... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.24]("http://www.medibuntu.org%7C87.98.24") 2.110|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
16:33:51 ERROR 404: Not Found.
```
all happened when they tried each part.

---

### Post by Orca_ Kuhn on 2009-05-06
```
allie@allie-desktop:~$ sudo apt-get update
[sudo] password for allie: 
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
allie@allie-desktop:~$ sudo apt-get install medibuntu-keyring
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
```

as for the sources list:

```
allie@allie-desktop:~$ cat /etc/apt/sources.list
bash: cat /etc/apt/sources.list: No such file or directory
```

---

### Post by zvacet on 2009-05-06
```
gksudo gedit /etc/apt/sources.list
```

Post output here.

---

### Post by Orca_ Kuhn on 2009-05-06
Output:
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid


Please tell me the problem/  Thank you very very much for your continued help.

---

### Post by lisati on 2009-05-06
I notice the mouse problem hasn't been mentioned so far. It could be that it will be fixed once the challenges the OP has experienced with the updates are sorted out. If not, and it's a USB mouse, the solution at [http://ubuntuforums.org/showthread.php?t=854684](http://ubuntuforums.org/showthread.php?t=854684) might be worth a shot.

---

### Post by CatKiller on 2009-05-06
> **Orca_ Kuhn said:**
> deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid

This is line 56. You probably want one or many of main, restricted, universe or multiverse on the end there, so that it reads something like 

```
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main
```

---

### Post by zvacet on 2009-05-07
It is not recommended to have mixed repos.Can you find what you need in Hardy repos?

---

### Post by colau on 2009-05-07
> **zvacet said:**
> For videos online you probably need flash.Go to the applications>accessories>terminal and in terminal type

```
sudo apt-get install ubuntu-restricted-extras
```

That will give you flash,java,multimedia plugins...

For Skype you have to add medibunru repo to your source list.Do it this way

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

When you are done go to the system>admin>synaptic and in search box type skype and synaptic will find package.Mark it for install and install it.

Thanks.

---

### Post by Orca_ Kuhn on 2009-05-09
Change implemented.  Tried to update, got:

```

allie@allie-desktop:~$ sudo apt-get update
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security Release.gpg
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security/main Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security/restricted Translation-en_US
Get:1 [http://ppa.launchpad.net]("http://ppa.launchpad.net/") intrepid Release.gpg [307B]           
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") intrepid/main Translation-en_US         
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy Release.gpg                   
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy/main Translation-en_US        
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy/restricted Translation-en_US  
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security Release                
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates/universe Translation-en_US
Get:2 [http://ppa.launchpad.net]("http://ppa.launchpad.net/") intrepid Release [46.7kB]
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates/multiverse Translation-en_US
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") intrepid Release                         
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy Release                        
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security/main Packages                    
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") intrepid/main Packages                  
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates Release
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security/restricted Packages              
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security/main Sources           
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security/restricted Sources     
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security/universe Packages      
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") intrepid/main Packages                  
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy/main Packages                 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy/restricted Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy/main Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy/restricted Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy/universe Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security/universe Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security/multiverse Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy/universe Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates/multiverse Sources
Fetched 308B in 0s (457B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net]("http://ppa.launchpad.net/") intrepid Release: 
```


Now for videos:
```

sudo apt-get install ubuntu-restricted-extras
...Seems to give full install....
 The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9423A34CCA967634
W: You may want to run apt-get update to correct these problems
allie@allie-desktop:~$ 
```

So looks like the two problems may have something related.  She can watch videos, but only so far the ones on WikiHow. Not YouTube or Hulu videos.  I know Firefox isn't blocking it either.


Thanks for all the help so far, much appreciated.

---

### Post by Orca_ Kuhn on 2009-05-10
Bump, since I have the feeling this will be solved shortly.

---

### Post by Orca_ Kuhn on 2009-05-10
Sorry >.>

Bump though.  My recent post detailed the recent problem.  Something happens in the updating process and from there the other install doesn't work and requires the update.

---

### Post by CatKiller on 2009-05-11
You've still got mixed sources in there. Pick hardy or intrepid and use that; don't use both.

The error message you're getting is because you haven't added the key for that repository. There are probably instructions wherever you found the instructions to add that repository in the first place. Otherwise, comment out the line for the PPA repository.

---

### Post by Orca_ Kuhn on 2009-05-11
I want to stick with Hardy I believe.
I don't understand though quite how to get rid of Intrepid and make it fully Hardy without messing it up.

---

### Post by CatKiller on 2009-05-11
> **Orca_ Kuhn said:**
> I want to stick with Hardy I believe.
I don't understand though quite how to get rid of Intrepid and make it fully Hardy without messing it up.

Just comment out (put a # at the beginning) the line with intrepid in. I think you've just got the one.

---

