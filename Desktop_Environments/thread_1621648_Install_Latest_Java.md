---
title: "Install Latest Java"
date: 2010-11-14
forum: Desktop Environments
---

### Post by shadowfax1 on 2010-11-14
Can't get an applet to initiate on a gaming site...is their a simple terminal command to install the latest version of Java?

Thanxs

---

### Post by sikander3786 on 2010-11-14
I assume you are running 10.10.

Go to Software Center > Edit > Software Sources > Other Software Tab and make sure that Canonical Partner repositories are enable there (2 of them).

Now from terminal,

```
sudo apt-get update
```

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

---

### Post by shadowfax1 on 2010-11-14
Still didn't work...this is the reply in terminal
I also got an error downloading in 'other software sources'

mark@mark-System-Product-Name:~$ sudo apt-get install sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-plugin is already the newest version.
sun-java6-jre is already the newest version.
sun-java6-jre set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Duplicate sources.list entry [http://ppa.launchpad.net/reacocard-awn/ubuntu/](http://ppa.launchpad.net/reacocard-awn/ubuntu/) gutsy/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_reacocard-awn_ubuntu_dists_gutsy_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
mark@mark-System-Product-Name:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
mark@mark-System-Product-Name:~$

---

### Post by DeAviator on 2010-11-14
Hey you need to enable multiverse repo before you use those commands
[http://www.botskool.com/forum/computer-programming/linuxunix/install-sun-java-6-ubuntu-1004-jdk-jre](http://www.botskool.com/forum/computer-programming/linuxunix/install-sun-java-6-ubuntu-1004-jdk-jre)

use this command to change/add repositories
sudo gedit /etc/apt/sources.list

take a backup of the files before you make these changes
read more before you edit
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by sikander3786 on 2010-11-14
First of all you've got a gutsy entry in your sources.list. What is it doing there?

> W: Duplicate sources.list entry [http://ppa.launchpad.net/reacocard-awn/ubuntu/](http://ppa.launchpad.net/reacocard-awn/ubuntu/) gutsy/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_reacocard-awn_ubuntu_dists_gutsy_main_binary-i386_Packages)

Please post the output of

```
cat /etc/apt/sources.list
```

Secondly this error,

> E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

It suggests that some other application like Synaptic, Software Center or Update Manger or even apt-get in another terminal is running and you cannot use any of them simultaneously. If anyother is running, close that. If no other is running, reboot and post the output of the above mentioned command.

Which version of Ubuntu are you running actually?

---

### Post by shadowfax1 on 2010-11-14
mark@mark-System-Product-Name:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main
mark@mark-System-Product-Name:~$

---

### Post by shadowfax1 on 2010-11-14
Version 10.10...
I tried installing it from synaptic earlier and it did install the three files needed but still didn't work.  I'm guessing but the 'gutsy' probably came from an earlier command someone gave me in this forum...

---

### Post by sikander3786 on 2010-11-14
Edit your sources.list by

```
gksudo gedit /etc/apt/sources.list
```

and put a comment # in the beginning of these 2 lines. They are just near the end of the file. 3rd and 4th last lines in that file.

```
deb http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main
deb http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main
```

So that they look like this,

```
#deb http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main
#deb http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main
```
Save and close. Go to terminal and now,

```
sudo apt-get update
```

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

---

### Post by shadowfax1 on 2010-11-14
Hmm did that exactly and...

mark@mark-System-Product-Name:~$ gksudo gedit /etc/apt/sources.list
mark@mark-System-Product-Name:~$ sudo apt-get update
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release.gpg
Ign [http://ppa.launchpad.net/reacocard-awn/ubuntu/](http://ppa.launchpad.net/reacocard-awn/ubuntu/) gutsy/main Translation-en   
Ign [http://ppa.launchpad.net/reacocard-awn/ubuntu/](http://ppa.launchpad.net/reacocard-awn/ubuntu/) gutsy/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick Release.gpg                          
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en                 
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net/reacocard-awn/ubuntu/](http://ppa.launchpad.net/reacocard-awn/ubuntu/) hardy/main Translation-en   
Ign [http://ppa.launchpad.net/reacocard-awn/ubuntu/](http://ppa.launchpad.net/reacocard-awn/ubuntu/) hardy/main Translation-en_CA
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/songbird-daily/ppa/ubuntu/](http://ppa.launchpad.net/songbird-daily/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/songbird-daily/ppa/ubuntu/](http://ppa.launchpad.net/songbird-daily/ppa/ubuntu/) maverick/main Translation-en_CA
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/) maverick/main Translation-en
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_CA       
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_CA 
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_CA 
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_CA   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates Release.gpg                  
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en_CA              
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_CA    
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_CA
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_CA           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/) maverick/main Translation-en_CA
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick Release                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates Release                      
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main i386 Packages/DiffIndex                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources/DiffIndex            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main i386 Packages/DiffIndex      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/main Sources               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/restricted Sources         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/universe Sources           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/multiverse Sources         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/main i386 Packages         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/restricted i386 Packages   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages             
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main i386 Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
  404  Not Found
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main i386 Packages
W: Failed to fetch [http://ppa.launchpad.net/songbird-daily/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/songbird-daily/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/songbird-daily/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/songbird-daily/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
mark@mark-System-Product-Name:~$ sudo apt-get install sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-plugin is already the newest version.
sun-java6-jre is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mark@mark-System-Product-Name:~$

---

### Post by sikander3786 on 2010-11-14
Ahhh. Sorry. I was lazy to spot some more offensive lines in that file.

You need to edit it again using the same command and comment these lines as well.

```
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
```

They are the last 3 on the list. Comment them all.

There is another error in your output but I couldn't find an entry for them in sources.list. :confused: These two,

```
Err http://ppa.launchpad.net maverick/main Sources
Err http://ppa.launchpad.net maverick/main i386 Packages
```

I hope they are under custom software. Go to Software Center > Edit > Software Sources > Other Software Tab and uncheck anything except Canonical Partners and again post the output of

```
sudo apt-get update
```

However your output for installation of java prompts that it has been installed.

---

### Post by shadowfax1 on 2010-11-14
I've obviously corrupted something along the way....I'll re-install the os and run your original commands... want to thankyou for your time on this...very much appreciated!

---

### Post by sikander3786 on 2010-11-14
You are Welcome :-)

If you want to reinstall Ubuntu, you can go for it but most of the problems in Linux are solve-able without reinstall.

And if you are going to reinstall, I'll advise you not to follow any commands from any untrusted sources. As you added those entries in your sources.list following some website or whatever.

UF is the greates place with almost all the answers. Community Docs are another way to learn anything.

You don't need to go to those un-related websites or blogs to find something.

And after a fresh install, what I myself do to install java, flash, fonts, codecs etc is just a signle command.

```
sudo apt-get install ubuntu-restricted-extras
```

It does all that work itself without me needing to find codecs and correct version of flash and java and plug-ins and all that. If you follow this command, you won't need to install java separately.

Good Luck and Happy Ubuntu-ing!

---

### Post by lykeion on 2010-11-15
You don't need to reinstall at all. You have already fixed all the errors, deleting the wrong entries in sources.list as suggested by sikander.

Note that external PPA:s (like the reocard you had) is dependant on single persons or sometimes a small team to keep them updated and working. 
Reocard seem to have stopped updating his PPA long time ago, see [here]("http://nancib.wordpress.com/2009/03/29/are-you-using-reacocards-ppa-for-updating-awn-if-so-you-need-to-make-a-change-in-your-settings/").
To add a PPA repository use the *add-apt-repository* command. This will make sure you get the right version (Maverick in your case). 
For example, if you would like to add a PPA to get the latest testing version of AWN you can use these commands:
```
sudo add-apt-repository ppa:awn-testing/ppa
sudo apt-get update
sudo apt-get install avant-window-navigator-trunk
```
But I'd recommend you to use the official repositories in first hand and only add external PPA:s in exceptional cases. So to install the official AWN version use this command (make sure Universe repositories are enabled):
```
sudo apt-get install avant-window-manager
```
Just one final note about the ubuntu-restricted-extras package:
> **sikander3786 said:**
> It does all that work itself without me needing to find codecs and correct version of flash and java and plug-ins and all that. If you follow this command, you won't need to install java separately.
The ubuntu-restricted-extras includes the browser plugins for Flash and Java, that's true. But it should be noted that it's the OpenJDK version of the Java plugin (icedtea6-plugin) not the latest Sun Java browser plugin.

---

