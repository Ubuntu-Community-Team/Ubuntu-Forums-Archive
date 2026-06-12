---
title: "Synaptic crash"
date: 2008-12-17
forum: General Help
---

### Post by Docaltmed on 2008-12-17
I have an ongoing problem with Synaptic that I hope someone can help me with. Hardware is an HP TX 2510us with Ubuntu 8.10.

For a couple of weeks, to run Synaptic, I have to do the following:

Go the System > Administration menu, click on Synaptic Package Manager. Synaptic will then boot up, and before loading any packages, will just sit there. It will not respond to any clicks, I have to force quit.

Restart Synaptic. This time,nothing will happen. I brief whir, no Synaptic screen appears, nothing.

Restart Synaptic. This time, it works as advertised.

Without following that procedure first, none of the other related programs, Add/Remove Software, Update Manager, Software Sources, will work. After following the above procedure, they work as normally. 

Here is what I've done to remedy the situation:

run "dpkg --configure -a". No problems.

reviewed sources.list for errors; I couldn't find any, in addition, when I run apt-get from the command line, the program seems happy with the repositories. In fact, I can update and upgrade from the command line, apparently with no difficulty.

run "apt-get --reinstall install synaptic". No change in the situation.

Obviously, this is not a critical problem. But I would still like to know why this is happening, and how I can fix it.

Any ideas?

---

### Post by philinux on 2008-12-17
Run it from the terminal so as to display the errors it's getting

```
gksu synaptic
```

---

### Post by Docaltmed on 2008-12-17
Ok, when I opened a terminal and started Synaptic with gksu, Synaptic started with it's usual hang-up, and there were no error messages on the terminal. I had to force quit, as usual. After doing so, I went back to the terminal, and it had not returned to the system prompt. It was just hanging there, as if the synaptic process were still running.

In fact, that had seemed to be the case other times. Before I discovered the "three times is the charm" rule, after I would start synaptic package manager once, and force quit it, if I went to another related program, for example Add/Remove Programs, and tried to start it, that program would report that another synaptic process was already running.

I don't know if that is important, but I don't know enough to know what would be important, so I'm trying to provide as much data as possible.

---

### Post by philinux on 2008-12-17
Ok I'd try these then.

sudo apt-get update && sudo apt-get upgrade

sudo apt-get check

sudo apt-get autoclean

sudo apt-get autoremove

---

### Post by Kevbert on 2008-12-17
Do you get any messages with
```
sudo apt-get install -f
```
?

---

### Post by Docaltmed on 2008-12-17
Thanks for the suggestions. I ran all of the commands, there's been no change in behavior. 

Here's what I get:

> avery@arran:~$ sudo apt-get update
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US  
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US            
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US 
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                    
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages                        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources            
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Sources
Fetched 3B in 5s (1B/s)  
Reading package lists... Done

> avery@arran:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



> avery@arran:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

> avery@arran:~$ sudo apt-get check
[sudo] password for avery: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
avery@arran:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-zopeinterface python-twisted-core ttf-wqy-zenhei libgda3-common
  python-gnome2-extras python-gamin ttf-kannada-fonts streamripper
  python-pyogg libtre4 python-pyvorbis ruby1.8 python-serial python-ogg
  python-pam python-openssl python-editobj ruby python-mutagen python-cddb
  ttf-telugu-fonts python-cerealizer python-pyopenssl libtunepimp5 libifp4
  libcal3d12 python-soya python-tofu libavahi1.0-cil libgda3-bin
  ttf-oriya-fonts libgda3-3 libruby1.8 libode0debian1 ttf-bengali-fonts
  python-gpod python-twisted-bin libnjb5 libgdl-1-0 libgdl-1-common
The following packages will be REMOVED:
  libavahi1.0-cil libcal3d12 libgda3-3 libgda3-bin libgda3-common libgdl-1-0
  libgdl-1-common libifp4 libnjb5 libode0debian1 libruby1.8 libtre4
  libtunepimp5 python-cddb python-cerealizer python-editobj python-gamin
  python-gnome2-extras python-gpod python-mutagen python-ogg python-openssl
  python-pam python-pyogg python-pyopenssl python-pyvorbis python-serial
  python-soya python-tofu python-twisted-bin python-twisted-core
  python-zopeinterface ruby ruby1.8 streamripper ttf-bengali-fonts
  ttf-kannada-fonts ttf-oriya-fonts ttf-telugu-fonts ttf-wqy-zenhei
0 upgraded, 0 newly installed, 40 to remove and 0 not upgraded.
After this operation, 47.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 160564 files and directories currently installed.)
Removing libavahi1.0-cil ...
Removing libavahi1.0-cil from Mono
Removing python-soya ...
Removing libcal3d12 ...
Removing python-gnome2-extras ...
Removing libgda3-bin ...
Removing libgda3-3 ...
Removing libgda3-common ...
Removing libgdl-1-0 ...
Removing libgdl-1-common ...
Removing libifp4 ...
Removing libnjb5 ...
Removing libode0debian1 ...
Removing ruby ...
Removing ruby1.8 ...
Removing libruby1.8 ...
Removing streamripper ...
Removing libtre4 ...
Removing libtunepimp5 ...
Removing python-cddb ...
Removing python-cerealizer ...
Removing python-editobj ...
Removing python-gamin ...
Removing python-gpod ...
Removing python-mutagen ...
Removing python-pyvorbis ...
Removing python-pyogg ...
Removing python-ogg ...
Removing python-pyopenssl ...
Removing python-openssl ...
Removing python-pam ...
Removing python-serial ...
Removing python-tofu ...
Removing python-twisted-core ...
Removing python-twisted-bin ...
dpkg - warning: while removing python-twisted-bin, directory `/usr/lib/python2.5/site-packages/twisted' not empty so not removed.
Removing python-zopeinterface ...
Removing ttf-bengali-fonts ...
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-bengali-fonts
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for ZenHei, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
Removing ttf-kannada-fonts ...
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-kannada-fonts /usr/share/fonts/truetype/ttf-indic-fonts-core
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for ZenHei, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
Removing ttf-oriya-fonts ...
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-oriya-fonts
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for ZenHei, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
Removing ttf-telugu-fonts ...
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-telugu-fonts
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for ZenHei, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
Removing ttf-wqy-zenhei ...
Updating fontconfig cache for /usr/share/fonts/truetype/wqy
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
Processing triggers for python-support ...
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for hal ...
Regenerating hal fdi cache ...
 * Restarting Hardware abstraction layer hald                            [ OK ] 

avery@arran:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done

---

### Post by philinux on 2008-12-17
We better have a look at the sources.

```
cat /etc/apt/sources.list
```

Wrap code tags around the output.

---

### Post by Docaltmed on 2008-12-17
```
avery@arran:~$ cat /etc/apt/sources.list
## deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
## See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
## newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
## deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner
deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
## deb hppt://ppa.lauhchpad.net/banshee-team/ubuntu intrepid main

## PulseAudio Fixes - http://ubuntuforums.org/showthread.php?t=789578
deb http://ppa.launchpad.net/psyke83/ubuntu intrepid main
deb-src http://ppa.launchpad.net/psyke83/ubuntu intrepid main
deb http://ppa.launchpad.net/banshee-team/ubuntu intrepid main
```

---

### Post by Kevbert on 2008-12-18
Looks like software sources are OK. Maybe the packages list has been corrupted. The solution for this would be (in terminal):
```
cd /var/lib/dpkg
sudo mv status status-bad
sudo cp status-old status
sudo apt-get update

```
Normally you'd get an error like 'the package status could not be parsed'.

---

### Post by Docaltmed on 2008-12-19
I ran the commands through the terminal, and all of them were completed without any error messages. Synaptic behavior remains unchanged, though.

---

### Post by Docaltmed on 2008-12-22
Anybody else have any ideas? I'm still open for suggestions.

---

### Post by Docaltmed on 2008-12-23
Fresh data:

Synaptic will run fine the first time out, if I go to the terminal and type "sudo synaptic." Thereafter, it will boot correctly from the GUI.

If I type "synaptic" at the terminal prompt, it will boot into non-administrative mode with no problem.

So the problem doesn't seem to be with synaptic itself, or with the sources.list file, but synaptic's relationship with the GUI.

How might I explore this further?

---

### Post by coiske on 2009-03-06
I can confirm this bug, docaltmed.  It affects my Intrepid box too.  Starting synaptic from the GUI (via gksu) leads to a frozen synaptic.  Starting it from the command line via gksu yields the same behavior.  However, starting it from the command line via sudo works fine.  So it's either a gksu bug or a synaptic bug (or both).

Did you ever file a bug report?

---

### Post by forger on 2009-03-06
1) 
Close synaptic.
Execute:
```
sudo rm -rfv $HOME/.synaptic
sudo rm -rfv /root/.synaptic
```
Log out and log back in, then run synaptic.
Does it work now?

2) Create a new user, test your problem from there

---

### Post by coiske on 2009-03-06
Your first suggestion seems to help!  (Though I needed to restart, not just log out/in, to see the benefit.)

---

### Post by coiske on 2009-03-07
Nevermind.  The problem is back.  I got one good use out of synaptic, and that was it.

When I start synaptic via the gnome menu item, it spawns two processes.  "ps aux | grep synaptic" reveals:

dave     11260  4.1  1.6  46328 17524 ?        S    23:06   0:01 gksu /usr/sbin/synaptic
root     11261  3.7  2.1  53136 22024 ?        Ss   23:06   0:01 /usr/sbin/synaptic

If I kill the first process, synaptic itself unfreezes!  So it seems like gksu is hanging around and mucking things up.

PS There's a bug report at [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/236426](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/236426)

---

### Post by macabro22 on 2009-03-09
This happens very frequently here as well

---

### Post by davidryder on 2009-03-09
Have you tried reinstalling gksu?

---

### Post by forger on 2009-03-09
OK, let's try again:

1) reconfigure gksu and synaptic:
```

sudo killall -9 -r -I synaptic
sudo dpkg-reconfigure -phigh gksu synaptic

```

2) Try to create a NEW user with administrator privileges and see if it works :) (System > Administration > Users and Groups)

The very first time (and only once), **before** trying anything kill all hanging processes:
```
sudo killall -9 -r -I synaptic
```

Let me know of the results when you finish.

---

### Post by coiske on 2009-03-09
I tried reinstalling gksu and rebooting, with no luck.  I also tried reconfiguring gksu and synaptic and rebooting, with no luck.

Finally, I tried rebooting and logging in as a different user, and running synaptic.  It worked from the other user's account.

But I still can't get it to work under my primary account!

I don't see anything synaptic or gksu-related in my home directory (except empty .gksu.lock and .sudo_as_admin_successful files, which are also in the other user's directory, and deleting them doesn't solve the problem).  And gconf-editor didn't reveal any differences between the the two accounts' gconf settings for gksu.  (They don't have any gconf settings for synaptic.)

I DON'T want to trash all the configuration files in my home directory.  (Reconfiguring all my apps is not an appealing prospect.)  So is there anything else I can do?

---

### Post by davidryder on 2009-03-09
Well we know it's in the /home directory, so I would probably start there. You could try process of elimination by copying one directory at a time. I know it's a pain but unless you get any more suggestions, that might be your best bet.

---

