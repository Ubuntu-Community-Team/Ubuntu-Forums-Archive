---
title: "Desktop is gone?"
date: 2014-06-13
forum: Desktop Environments
---

### Post by bekirs on 2014-06-13
Hi all,

as clearly stated in the title, I have no access to my desktop when I minimize or close all other windows. Could you help me recovering this simple functionality?

Thanks in advance,

---

### Post by Elfy on 2014-06-13
Try Alt+F2 and running xfdesktop --reload

Possibly need to add it to autostart apps in settings - session and startup

---

### Post by bekirs on 2014-06-13
Output:

Failed to execute child process "xfdesktop" (No such file or directory).

> **Elfy said:**
> Try Alt+F2 and running xfdesktop --reload

Possibly need to add it to autostart apps in settings - session and startup

---

### Post by Elfy on 2014-06-14
Run this in a terminal please 

```
dpkg -l xfdesktop4 && echo $DESKTOP_SESSION
```

Moved thread

---

### Post by bekirs on 2014-06-14
```

dpkg -l xfdesktop4 && echo $DESKTOP_SESSION
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name Version Description
+++-==============-==============-============================================
rc xfdesktop4 4.8.3-2ubuntu7 xfce desktop background, icons and root menu
xubuntu

```



> **Elfy said:**
> Run this in a terminal please 

```
dpkg -l xfdesktop4 && echo $DESKTOP_SESSION
```

Moved thread

---

### Post by Elfy on 2014-06-14
Try 

```
sudo apt-get install xfdesktop4 
```

Then Alt+F2 and then xfdesktop --reload again

---

### Post by bekirs on 2014-06-14
```

sudo apt-get install xfdesktop4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 xfdesktop4 : Depends: libxfce4ui-1-0 (>= 4.11.0) but 4.8.1-1 is to be installed
              Depends: libxfce4util6 (>= 4.9.0) but it is not installable
E: Unable to correct problems, you have held broken packages.

```

then after pressing Alt+F2, I tried ```
xfdesktop --reload
``` the output is

```
Failed to execute child process "xfdesktop" (No such file or directory).
```

> **Elfy said:**
> Try 

```
sudo apt-get install xfdesktop4 
```

Then Alt+F2 and then xfdesktop --reload again

---

### Post by Toz on 2014-06-14
Are you still on Xubuntu 12.04?

Did you try using one of the 4.10/4.12 PPAs and reverted?

What does the following return?
```
apt-cache policy xfdesktop4
```
...and
```
sudo apt-get update
```

---

### Post by bekirs on 2014-06-14
1st output: 

```
apt-cache policy xfdesktop4xfdesktop4:
  Installed: (none)
  Candidate: 4.11.2-0ubuntu1~ppa0.12.04.1
  Version table:
     4.11.2-0ubuntu1~ppa0.12.04.1 0
        500 http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu/ precise/main amd64 Packages
     4.8.3-2ubuntu7 0
        500 http://archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages
        100 /var/lib/dpkg/status

```

2nd output:

```
sudo apt-get update
Get:1 http://dl.google.com stable Release.gpg [198 B]
Get:2 http://dl.google.com stable Release [1,347 B]                            
Hit http://archive.ubuntu.com precise Release.gpg                              
Get:3 http://archive.ubuntu.com precise-updates Release.gpg [198 B]            
Get:4 http://archive.ubuntu.com precise-security Release.gpg [198 B]           
Get:5 http://archive.ubuntu.com precise-proposed Release.gpg [198 B]           
Get:6 http://archive.ubuntu.com precise-backports Release.gpg [198 B]          
Get:7 http://archive.canonical.com precise Release.gpg [198 B]                 
Hit http://archive.ubuntu.com precise Release                                  
Get:8 http://archive.ubuntu.com precise-updates Release [49.6 kB]              
Get:9 http://archive.canonical.com precise Release [7,078 B]                   
Get:10 http://archive.ubuntu.com precise-security Release [49.6 kB]            
Get:11 http://archive.ubuntu.com precise-proposed Release [49.6 kB]            
Get:12 http://archive.canonical.com precise/partner amd64 Packages [7,892 B]   
Get:13 http://archive.ubuntu.com precise-backports Release [49.6 kB]           
Get:14 http://archive.canonical.com precise/partner i386 Packages [8,931 B]    
Hit http://archive.ubuntu.com precise/restricted Sources                       
Hit http://archive.ubuntu.com precise/main Sources                             
Hit http://archive.ubuntu.com precise/multiverse Sources                       
Hit http://archive.ubuntu.com precise/universe Sources                         
Hit http://archive.ubuntu.com precise/main amd64 Packages                      
Hit http://archive.ubuntu.com precise/restricted amd64 Packages                
Hit http://archive.ubuntu.com precise/universe amd64 Packages                  
Hit http://archive.ubuntu.com precise/multiverse amd64 Packages                
Hit http://archive.ubuntu.com precise/main i386 Packages                       
Ign http://archive.canonical.com precise/partner TranslationIndex              
Get:15 http://linux.dropbox.com precise Release.gpg [489 B]                    
Hit http://archive.ubuntu.com precise/restricted i386 Packages                 
Hit http://archive.ubuntu.com precise/universe i386 Packages                   
Hit http://archive.ubuntu.com precise/multiverse i386 Packages                 
Hit http://archive.ubuntu.com precise/main TranslationIndex                    
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex              
Hit http://archive.ubuntu.com precise/restricted TranslationIndex              
Hit http://archive.ubuntu.com precise/universe TranslationIndex                
Get:16 http://archive.ubuntu.com precise-updates/restricted Sources [8,056 B]  
Get:17 http://archive.ubuntu.com precise-updates/main Sources [460 kB]         
Get:18 http://linux.dropbox.com precise Release [2,603 B]                      
Get:19 http://dl.google.com stable/main amd64 Packages [1,225 B]               
Get:20 http://dl.google.com stable/main i386 Packages [1,217 B]                
Ign http://dl.google.com stable/main TranslationIndex                          
Get:21 http://archive.ubuntu.com precise-updates/multiverse Sources [8,909 B]  
Get:22 http://archive.ubuntu.com precise-updates/universe Sources [107 kB]     
Get:23 http://linux.dropbox.com precise/main amd64 Packages [1,143 B]          
Ign http://archive.canonical.com precise/partner Translation-en_US             
Get:24 http://archive.ubuntu.com precise-updates/main amd64 Packages [789 kB]  
Ign http://archive.canonical.com precise/partner Translation-en                
Get:25 http://linux.dropbox.com precise/main i386 Packages [1,143 B]           
Ign http://linux.dropbox.com precise/main TranslationIndex                     
Get:26 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:27 http://ppa.launchpad.net precise Release [11.9 kB]                      
Ign http://dl.google.com stable/main Translation-en_US                         
Get:28 http://extras.ubuntu.com precise Release.gpg [72 B]                     
Hit http://ppa.launchpad.net precise Release                                   
Get:29 http://archive.ubuntu.com precise-updates/restricted amd64 Packages [13.7 kB]
Get:30 http://archive.ubuntu.com precise-updates/universe amd64 Packages [241 kB]
Ign http://dl.google.com stable/main Translation-en                            
Hit http://extras.ubuntu.com precise Release                                   
Get:31 http://ppa.launchpad.net precise/main Sources [1,211 B]                 
Get:32 http://ppa.launchpad.net precise/main amd64 Packages [2,803 B]          
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Get:33 http://ppa.launchpad.net precise/main i386 Packages [2,803 B]           
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:34 http://archive.ubuntu.com precise-updates/multiverse amd64 Packages [15.3 kB]
Get:35 http://archive.ubuntu.com precise-updates/main i386 Packages [822 kB]   
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:36 http://archive.ubuntu.com precise-updates/restricted i386 Packages [13.7 kB]
Get:37 http://archive.ubuntu.com precise-updates/universe i386 Packages [247 kB]
Get:38 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]
Get:39 http://archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:40 http://archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:41 http://archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:42 http://archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Get:43 http://archive.ubuntu.com precise-security/restricted Sources [2,494 B] 
Get:44 http://archive.ubuntu.com precise-security/main Sources [106 kB]        
Get:45 http://archive.ubuntu.com precise-security/multiverse Sources [1,795 B] 
Get:46 http://archive.ubuntu.com precise-security/universe Sources [30.7 kB]   
Get:47 http://archive.ubuntu.com precise-security/main amd64 Packages [401 kB] 
Get:48 http://archive.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]
Get:49 http://archive.ubuntu.com precise-security/universe amd64 Packages [93.5 kB]
Get:50 http://archive.ubuntu.com precise-security/multiverse amd64 Packages [2,434 B]
Get:51 http://archive.ubuntu.com precise-security/main i386 Packages [427 kB]  
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Get:52 http://archive.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:53 http://archive.ubuntu.com precise-security/universe i386 Packages [98.7 kB]
Get:54 http://archive.ubuntu.com precise-security/multiverse i386 Packages [2,647 B]
Get:55 http://archive.ubuntu.com precise-security/main TranslationIndex [74 B] 
Get:56 http://archive.ubuntu.com precise-security/multiverse TranslationIndex [72 B]
Get:57 http://archive.ubuntu.com precise-security/restricted TranslationIndex [72 B]
Get:58 http://archive.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:59 http://archive.ubuntu.com precise-proposed/restricted amd64 Packages [755 B]
Get:60 http://archive.ubuntu.com precise-proposed/main amd64 Packages [185 kB] 
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://linux.dropbox.com precise/main Translation-en_US                    
Get:61 http://archive.ubuntu.com precise-proposed/multiverse amd64 Packages [583 B]
Get:62 http://archive.ubuntu.com precise-proposed/universe amd64 Packages [20.0 kB]
Get:63 http://archive.ubuntu.com precise-proposed/restricted i386 Packages [743 B]
Get:64 http://archive.ubuntu.com precise-proposed/main i386 Packages [206 kB]  
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Get:65 http://archive.ubuntu.com precise-proposed/multiverse i386 Packages [590 B]
Get:66 http://archive.ubuntu.com precise-proposed/universe i386 Packages [25.1 kB]
Get:67 http://archive.ubuntu.com precise-proposed/main TranslationIndex [3,564 B]
Ign http://linux.dropbox.com precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en                
Get:68 http://archive.ubuntu.com precise-proposed/multiverse TranslationIndex [2,605 B]
Get:69 http://archive.ubuntu.com precise-proposed/restricted TranslationIndex [2,461 B]
Get:70 http://archive.ubuntu.com precise-proposed/universe TranslationIndex [2,850 B]
Get:71 http://archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]
Get:72 http://archive.ubuntu.com precise-backports/main amd64 Packages [6,412 B]
Get:73 http://archive.ubuntu.com precise-backports/multiverse amd64 Packages [5,206 B]
Get:74 http://archive.ubuntu.com precise-backports/universe amd64 Packages [41.4 kB]
Get:75 http://archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:76 http://archive.ubuntu.com precise-backports/main i386 Packages [6,420 B]
Get:77 http://archive.ubuntu.com precise-backports/multiverse i386 Packages [5,178 B]
Get:78 http://archive.ubuntu.com precise-backports/universe i386 Packages [41.2 kB]
Get:79 http://archive.ubuntu.com precise-backports/main TranslationIndex [72 B]
Get:80 http://archive.ubuntu.com precise-backports/multiverse TranslationIndex [72 B]
Get:81 http://archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]
Get:82 http://archive.ubuntu.com precise-backports/universe TranslationIndex [73 B]
Hit http://archive.ubuntu.com precise/main Translation-en
Hit http://archive.ubuntu.com precise/multiverse Translation-en
Hit http://archive.ubuntu.com precise/restricted Translation-en
Hit http://archive.ubuntu.com precise/universe Translation-en
Get:83 http://archive.ubuntu.com precise-updates/main Translation-en [352 kB]
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en
Get:84 http://archive.ubuntu.com precise-updates/universe Translation-en [140 kB]
Get:85 http://archive.ubuntu.com precise-security/main Translation-en [184 kB]
Hit http://archive.ubuntu.com precise-security/multiverse Translation-en
Hit http://archive.ubuntu.com precise-security/restricted Translation-en
Get:86 http://archive.ubuntu.com precise-security/universe Translation-en [57.5 kB]
Get:87 http://archive.ubuntu.com precise-proposed/main Translation-en [70.2 kB]
Hit http://archive.ubuntu.com precise-proposed/multiverse Translation-en
Hit http://archive.ubuntu.com precise-proposed/restricted Translation-en
Get:88 http://archive.ubuntu.com precise-proposed/universe Translation-en [11.3 kB]
Hit http://archive.ubuntu.com precise-backports/main Translation-en 
Hit http://archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://archive.ubuntu.com precise-backports/restricted Translation-en
Get:89 http://archive.ubuntu.com precise-backports/universe Translation-en [32.9 kB]
Fetched 5,585 kB in 6s (897 kB/s)                                              
Reading package lists... Done



```





> **Toz said:**
> Are you still on Xubuntu 12.04?

Did you try using one of the 4.10/4.12 PPAs and reverted?

What does the following return?
```
apt-cache policy xfdesktop4
```
...and
```
sudo apt-get update
```

---

### Post by Toz on 2014-06-14
Did you enable the 4.12 PPA then delete it? 

What does this return:
```
ls /etc/apt/sources.list.d
```
...and
```
cat /etc/apt/sources.list
```

Do you want to use the default Xfce 4.8 that shipped with Precise 12.04, or do you want to use the newer Xfce 4.12 (its not really 4.12, but the PPA is calling it 4.12)?

---

### Post by bekirs on 2014-06-14
I'm not sure and I don't remeber what I've done; it has happened already some months ago... I'd like to use the newest version among the safest ones.. Here are the outputs:

```
ls /etc/apt/sources.list.dconnectionmanager.list              texlive-backports-ppa-precise.list.save
connectionmanager.list.save         texworks-stable-precise.list
dropbox.list                        texworks-stable-precise.list.save
dropbox.list.save                   webupd8team-java-precise.list
google-chrome.list                  webupd8team-java-precise.list.save
google-chrome.list.save             xubuntu-dev-xfce-4_12-precise.list
texlive-backports-ppa-precise.list  xubuntu-dev-xfce-4_12-precise.list.save

```

```
cat /etc/apt/sources.list
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/


# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/multiverse/binary-i386/
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/universe/binary-i386/
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main multiverse restricted universe


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu precise main restricted
deb-src http://archive.ubuntu.com/ubuntu precise restricted main multiverse universe #Added by software-properties


## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-updates restricted main multiverse universe #Added by software-properties


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise universe
deb http://archive.ubuntu.com/ubuntu precise-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu precise multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


deb http://archive.ubuntu.com/ubuntu precise-security main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu precise-security universe
deb http://archive.ubuntu.com/ubuntu precise-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://archive.ubuntu.com/ubuntu precise-proposed restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu precise-backports restricted main multiverse universe

```




> **Toz said:**
> Did you enable the 4.12 PPA then delete it? 

What does this return:
```
ls /etc/apt/sources.list.d
```
...and
```
cat /etc/apt/sources.list
```

Do you want to use the default Xfce 4.8 that shipped with Precise 12.04, or do you want to use the newer Xfce 4.12 (its not really 4.12, but the PPA is calling it 4.12)?

---

### Post by Toz on 2014-06-14
Okay, you need the 4.10 PPA installed before you can use the 4.12 PPA (see: [https://launchpad.net/~xubuntu-dev/+archive/xfce-4.12]("https://launchpad.net/~xubuntu-dev/+archive/xfce-4.12")).

So lets try this:
```
sudo add-apt-repository ppa:xubuntu-dev/xfce-4.10
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by bekirs on 2014-06-14
Output 1
```
sudo add-apt-repository ppa:xubuntu-dev/xfce-4.10You are about to add the following PPA to your system:
 Xfce 4.10 packages for Xubuntu 12.04 LTS (Precise Pangolin), Xubuntu 12.10 (Quantal Quetzal) and Xubuntu 13.10 (Saucy Salamander).


Currently: Xfce 4.10.1 for all releases.
 More info: https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10
Press [ENTER] to continue or ctrl-c to cancel adding it


gpg: keyring `/tmp/tmp2QQDPL/secring.gpg' created
gpg: keyring `/tmp/tmp2QQDPL/pubring.gpg' created
gpg: requesting key 142986CE from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp2QQDPL/trustdb.gpg: trustdb created
gpg: key 142986CE: public key "Launchpad PPA for Xubuntu Developers" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK

```

Output2:
```
sudo apt-get update
Hit http://dl.google.com stable Release.gpg
Hit http://dl.google.com stable Release                                        
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://archive.ubuntu.com precise Release.gpg                              
Get:1 http://archive.ubuntu.com precise-updates Release.gpg [198 B]            
Get:2 http://archive.ubuntu.com precise-security Release.gpg [198 B]           
Get:3 http://archive.ubuntu.com precise-proposed Release.gpg [198 B]           
Hit http://archive.ubuntu.com precise-backports Release.gpg                    
Hit http://archive.canonical.com precise Release                               
Hit http://archive.ubuntu.com precise Release                                  
Get:4 http://archive.ubuntu.com precise-updates Release [49.6 kB]              
Hit http://dl.google.com stable/main amd64 Packages                            
Get:5 http://archive.ubuntu.com precise-security Release [49.6 kB]             
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Get:6 http://archive.ubuntu.com precise-proposed Release [49.6 kB]             
Hit http://archive.ubuntu.com precise-backports Release                        
Hit http://archive.ubuntu.com precise/restricted Sources                       
Hit http://archive.ubuntu.com precise/main Sources                             
Hit http://archive.ubuntu.com precise/multiverse Sources                       
Hit http://archive.ubuntu.com precise/universe Sources                         
Hit http://archive.ubuntu.com precise/main amd64 Packages                      
Hit http://archive.ubuntu.com precise/restricted amd64 Packages                
Hit http://archive.ubuntu.com precise/universe amd64 Packages                  
Hit http://archive.ubuntu.com precise/multiverse amd64 Packages                
Hit http://linux.dropbox.com precise Release.gpg                               
Hit http://archive.ubuntu.com precise/main i386 Packages                       
Hit http://archive.ubuntu.com precise/restricted i386 Packages                 
Hit http://archive.ubuntu.com precise/universe i386 Packages                   
Hit http://archive.ubuntu.com precise/multiverse i386 Packages                 
Hit http://archive.ubuntu.com precise/main TranslationIndex                    
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex              
Hit http://archive.ubuntu.com precise/restricted TranslationIndex              
Hit http://archive.ubuntu.com precise/universe TranslationIndex                
Get:7 http://archive.ubuntu.com precise-updates/restricted Sources [8,056 B]   
Get:8 http://archive.ubuntu.com precise-updates/main Sources [460 kB]          
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://linux.dropbox.com precise Release                                   
Ign http://dl.google.com stable/main Translation-en                            
Get:9 http://archive.ubuntu.com precise-updates/multiverse Sources [8,909 B]   
Get:10 http://archive.ubuntu.com precise-updates/universe Sources [107 kB]     
Get:11 http://archive.ubuntu.com precise-updates/main amd64 Packages [789 kB]  
Hit http://linux.dropbox.com precise/main amd64 Packages                       
Ign http://archive.canonical.com precise/partner Translation-en_US             
Hit http://linux.dropbox.com precise/main i386 Packages                        
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://linux.dropbox.com precise/main TranslationIndex                     
Get:12 http://archive.ubuntu.com precise-updates/restricted amd64 Packages [13.7 kB]
Get:13 http://archive.ubuntu.com precise-updates/universe amd64 Packages [241 kB]
Get:14 http://archive.ubuntu.com precise-updates/multiverse amd64 Packages [15.3 kB]
Get:15 http://archive.ubuntu.com precise-updates/main i386 Packages [822 kB]   
Get:16 http://extras.ubuntu.com precise Release.gpg [72 B]                     
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:17 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Get:18 http://archive.ubuntu.com precise-updates/restricted i386 Packages [13.7 kB]
Get:19 http://archive.ubuntu.com precise-updates/universe i386 Packages [247 kB]
Hit http://ppa.launchpad.net precise Release                                   
Get:20 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex            
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex      
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex      
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex        
Get:21 http://archive.ubuntu.com precise-security/restricted Sources [2,494 B] 
Get:22 http://archive.ubuntu.com precise-security/main Sources [106 kB]        
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:23 http://archive.ubuntu.com precise-security/multiverse Sources [1,795 B] 
Get:24 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:25 http://archive.ubuntu.com precise-security/universe Sources [30.7 kB]   
Get:26 http://archive.ubuntu.com precise-security/main amd64 Packages [401 kB] 
Hit http://ppa.launchpad.net precise Release                                   
Get:27 http://archive.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]
Get:28 http://archive.ubuntu.com precise-security/universe amd64 Packages [93.5 kB]
Get:29 http://archive.ubuntu.com precise-security/multiverse amd64 Packages [2,434 B]
Get:30 http://archive.ubuntu.com precise-security/main i386 Packages [427 kB]  
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:31 http://archive.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:32 http://archive.ubuntu.com precise-security/universe i386 Packages [98.7 kB]
Get:33 http://ppa.launchpad.net precise/main Sources [22.7 kB]                 
Get:34 http://archive.ubuntu.com precise-security/multiverse i386 Packages [2,647 B]
Hit http://archive.ubuntu.com precise-security/main TranslationIndex           
Hit http://archive.ubuntu.com precise-security/multiverse TranslationIndex     
Hit http://archive.ubuntu.com precise-security/restricted TranslationIndex     
Hit http://archive.ubuntu.com precise-security/universe TranslationIndex       
Get:35 http://archive.ubuntu.com precise-proposed/restricted amd64 Packages [755 B]
Get:36 http://archive.ubuntu.com precise-proposed/main amd64 Packages [185 kB] 
Get:37 http://ppa.launchpad.net precise/main amd64 Packages [23.6 kB]          
Get:38 http://archive.ubuntu.com precise-proposed/multiverse amd64 Packages [583 B]
Get:39 http://archive.ubuntu.com precise-proposed/universe amd64 Packages [20.0 kB]
Get:40 http://archive.ubuntu.com precise-proposed/restricted i386 Packages [743 B]
Get:41 http://archive.ubuntu.com precise-proposed/main i386 Packages [206 kB]  
Get:42 http://archive.ubuntu.com precise-proposed/multiverse i386 Packages [590 B]
Get:43 http://archive.ubuntu.com precise-proposed/universe i386 Packages [25.1 kB]
Hit http://archive.ubuntu.com precise-proposed/main TranslationIndex           
Get:44 http://ppa.launchpad.net precise/main i386 Packages [23.6 kB]           
Hit http://archive.ubuntu.com precise-proposed/multiverse TranslationIndex     
Hit http://archive.ubuntu.com precise-proposed/restricted TranslationIndex     
Hit http://archive.ubuntu.com precise-proposed/universe TranslationIndex       
Hit http://archive.ubuntu.com precise/main Translation-en                      
Hit http://archive.ubuntu.com precise-backports/restricted amd64 Packages      
Hit http://archive.ubuntu.com precise-backports/main amd64 Packages            
Hit http://archive.ubuntu.com precise-backports/multiverse amd64 Packages      
Hit http://archive.ubuntu.com precise-backports/universe amd64 Packages        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://archive.ubuntu.com precise-backports/restricted i386 Packages       
Hit http://archive.ubuntu.com precise-backports/main i386 Packages             
Hit http://archive.ubuntu.com precise-backports/multiverse i386 Packages       
Hit http://archive.ubuntu.com precise-backports/universe i386 Packages         
Hit http://archive.ubuntu.com precise-backports/main TranslationIndex          
Hit http://archive.ubuntu.com precise-backports/multiverse TranslationIndex    
Hit http://archive.ubuntu.com precise-backports/restricted TranslationIndex    
Hit http://archive.ubuntu.com precise-backports/universe TranslationIndex      
Hit http://archive.ubuntu.com precise/multiverse Translation-en                
Hit http://archive.ubuntu.com precise/restricted Translation-en                
Hit http://archive.ubuntu.com precise/universe Translation-en                  
Hit http://archive.ubuntu.com precise-updates/main Translation-en              
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en        
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en        
Hit http://archive.ubuntu.com precise-updates/universe Translation-en          
Hit http://archive.ubuntu.com precise-security/main Translation-en             
Hit http://archive.ubuntu.com precise-security/multiverse Translation-en       
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Hit http://archive.ubuntu.com precise-security/restricted Translation-en       
Hit http://archive.ubuntu.com precise-security/universe Translation-en         
Hit http://archive.ubuntu.com precise-proposed/main Translation-en             
Hit http://archive.ubuntu.com precise-proposed/multiverse Translation-en       
Hit http://archive.ubuntu.com precise-proposed/restricted Translation-en       
Hit http://archive.ubuntu.com precise-proposed/universe Translation-en         
Hit http://archive.ubuntu.com precise-backports/main Translation-en            
Hit http://archive.ubuntu.com precise-backports/multiverse Translation-en      
Ign http://extras.ubuntu.com precise/main Translation-en                       
Hit http://archive.ubuntu.com precise-backports/restricted Translation-en      
Hit http://archive.ubuntu.com precise-backports/universe Translation-en        
Ign http://linux.dropbox.com precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en_US             
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en                
Ign http://ppa.launchpad.net precise/main Translation-en_US             
Ign http://ppa.launchpad.net precise/main Translation-en                
Ign http://linux.dropbox.com precise/main Translation-en                
Fetched 4,588 kB in 7s (645 kB/s)                                              
Reading package lists... Done

```

Output 3:
```

sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  xfce4-utils
The following NEW packages will be installed:
  gstreamer0.10-ffmpeg libxfce4ui-2-0 libxfce4ui-common libxfce4ui-utils libxfce4util6 xscreensaver
The following packages will be upgraded:
  exo-utils gigolo libexo-1-0 libexo-common libexo-helpers libgarcon-1-0 libgarcon-common libthunarx-2-0 libxfce4ui-1-0 libxfce4util-bin libxfce4util-common
  libxfcegui4-4 libxfconf-0-2 orage parole thunar thunar-data thunar-volman xfburn xfce-keyboard-shortcuts xfce4-appfinder xfce4-cpugraph-plugin xfce4-datetime-plugin
  xfce4-dict xfce4-indicator-plugin xfce4-mailwatch-plugin xfce4-netload-plugin xfce4-notes xfce4-notes-plugin xfce4-notifyd xfce4-panel xfce4-places-plugin
  xfce4-power-manager xfce4-power-manager-data xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings xfce4-systemload-plugin xfce4-taskmanager
  xfce4-terminal xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfconf xfwm4 xubuntu-default-settings
47 upgraded, 6 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 17.4 MB of archives.
After this operation, 5,255 kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ precise/universe gstreamer0.10-ffmpeg amd64 0.10.13-1 [125 kB]
Get:2 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main libxfce4util-common all 4.10.1-0ubuntu1~ppa0.12.04.1 [59.3 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ precise/main xscreensaver amd64 5.15-2ubuntu1 [274 kB]
Get:4 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main libxfce4util6 amd64 4.10.1-0ubuntu1~ppa0.12.04.1 [30.5 kB]
Get:5 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main xfconf amd64 4.10.0-0ubuntu1~ppa1 [116 kB]
Get:6 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main libxfconf-0-2 amd64 4.10.0-0ubuntu1~ppa1 [33.5 kB]
Get:7 http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu/ precise/main xfce-keyboard-shortcuts all 4.11.0-0ubuntu1~ppa0.12.04.1 [4,574 B]
Get:8 http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu/ precise/main libxfce4ui-1-0 amd64 4.11.0-0ubuntu1~ppa0.12.04.1 [52.3 kB]
Get:9 http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu/ precise/main libxfce4ui-common all 4.11.0-0ubuntu1~ppa0.12.04.1 [208 kB]
Get:10 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main exo-utils amd64 0.10.2-0ubuntu1~ppa0.12.04.1 [60.0 kB]
Get:11 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main libexo-common all 0.10.2-0ubuntu1~ppa0.12.04.1 [21.8 kB]
Get:12 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main libexo-helpers amd64 0.10.2-0ubuntu1~ppa0.12.04.1 [24.9 kB]
Get:13 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main libexo-1-0 amd64 0.10.2-0ubuntu1~ppa0.12.04.1 [477 kB]
Get:14 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main libgarcon-common all 0.2.1-0ubuntu1~ppa0.12.04.1 [53.3 kB]
Get:15 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main libgarcon-1-0 amd64 0.2.1-0ubuntu1~ppa0.12.04.1 [46.2 kB]
Get:16 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main thunar amd64 1.6.3-0ubuntu1~ppa0.12.04.1 [320 kB]
Get:17 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main libthunarx-2-0 amd64 1.6.3-0ubuntu1~ppa0.12.04.1 [85.6 kB]
Get:18 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main thunar-data all 1.6.3-0ubuntu1~ppa0.12.04.1 [1,436 kB]
Get:19 http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu/ precise/main libxfce4ui-2-0 amd64 4.11.0-0ubuntu1~ppa0.12.04.1 [52.3 kB]
Get:20 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main libxfcegui4-4 amd64 4.10.0-0ubuntu1~ppa1 [240 kB]
Get:21 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main xfce4-panel amd64 4.10.1-0ubuntu1~ppa0.12.04.1 [958 kB]
Get:22 http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu/ precise/main xfce4-settings amd64 4.11.1-0ubuntu1~ppa0.12.04.1 [670 kB]
Get:23 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main xfce4-session amd64 4.10.1-0ubuntu1~ppa0.12.04.1 [788 kB]
Get:24 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main xubuntu-default-settings all 12.04.11+ppa2 [31.6 kB]
Get:25 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main gigolo amd64 0.4.2-1~ppa0.12.04.1 [180 kB]
Get:26 http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu/ precise/main libxfce4ui-utils amd64 4.11.0-0ubuntu1~ppa0.12.04.1 [48.9 kB]
Get:27 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main libxfce4util-bin amd64 4.10.1-0ubuntu1~ppa0.12.04.1 [10.3 kB]
Get:28 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main orage amd64 4.10.0-1~ppa0.12.04.1 [2,374 kB]
Get:29 http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu/ precise/main parole amd64 0.6.1-0ubuntu1~ppa0.12.04.1 [420 kB]                                           
Get:30 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main thunar-volman amd64 0.8.0-0ubuntu1~ppa1 [140 kB]                                            
Get:31 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main xfburn amd64 0.5.0-0ubuntu1~ppa0.12.04.1 [528 kB]                                           
Get:32 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main xfce4-appfinder amd64 4.10.1-0ubuntu1~ppa0.12.04.1 [126 kB]                                 
Get:33 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main xfce4-cpugraph-plugin amd64 1.0.5-0ubuntu1~ppa1 [54.4 kB]                                   
Get:34 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main xfce4-datetime-plugin amd64 0.6.2-0ubuntu1~ppa0.12.04.1 [35.9 kB]                           
Get:35 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main xfce4-dict amd64 0.7.0-1~ppa12.04.1 [195 kB]                                                
Get:36 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main xfce4-indicator-plugin amd64 0.4.0-0ubuntu2+ppa1 [26.8 kB]                                  
Get:37 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main xfce4-mailwatch-plugin amd64 1.2.0-1~ppa0.12.04.1 [199 kB]                                  
Get:38 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main xfce4-netload-plugin amd64 1.2.0-0ubuntu1~ppa1 [63.1 kB]                                    
Get:39 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main xfce4-notes amd64 1.7.7-2ubuntu1+ppa1 [109 kB]                                              
Get:40 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main xfce4-notes-plugin amd64 1.7.7-2ubuntu1+ppa1 [52.0 kB]                                      
Get:41 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main xfce4-notifyd amd64 0.2.4-2~ppa0.12.04.1 [80.3 kB]                                          
Get:42 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main xfce4-places-plugin amd64 1.6.0-1~ppa0.12.04.1 [79.4 kB]                                    
Get:43 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main xfce4-power-manager amd64 1.2.0-1ubuntu1.1~ppa1 [113 kB]                                    
Get:44 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main xfce4-power-manager-data all 1.2.0-1ubuntu1.1~ppa1 [634 kB]                                 
Get:45 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main xfce4-quicklauncher-plugin amd64 1.9.4-9+ppa1 [27.0 kB]                                     
Get:46 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main xfce4-screenshooter amd64 1.8.1-1~ppa1 [1,710 kB]                                           
Get:47 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main xfce4-systemload-plugin amd64 1:1.1.1-1ubuntu1~ppa1 [37.8 kB]                               
Get:48 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main xfce4-taskmanager amd64 1.0.1-1~ppa0.12.04.1 [103 kB]                                       
Get:49 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main xfce4-terminal amd64 0.6.3-1ubuntu1~ppa0.12.04.1 [473 kB]                                   
Get:50 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main xfce4-verve-plugin amd64 1.0.0-1+ppa1 [39.8 kB]                                             
Get:51 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main xfce4-weather-plugin amd64 0.8.3-0ubuntu1~ppa0.12.04.1 [2,349 kB]                           
Get:52 http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu/ precise/main xfce4-xkb-plugin amd64 1:0.7.0-0ubuntu1~ppa0.12.04.1 [539 kB]                               
Get:53 http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu/ precise/main xfwm4 amd64 4.11.1-0ubuntu1~ppa0.12.04.1 [536 kB]                                           
Fetched 17.4 MB in 16s (1,079 kB/s)                                                                                                                                    
Extracting templates from packages: 100%
(Reading database ... 1057196 files and directories currently installed.)
Removing xfce4-utils ...
update-alternatives: using /usr/bin/gnome-session to provide /usr/bin/x-session-manager (x-session-manager) in auto mode.
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
(Reading database ... 1057001 files and directories currently installed.)
Preparing to replace libxfce4util-common 4.8.2-1 (using .../libxfce4util-common_4.10.1-0ubuntu1~ppa0.12.04.1_all.deb) ...
Unpacking replacement libxfce4util-common ...
Selecting previously unselected package libxfce4util6.
Unpacking libxfce4util6 (from .../libxfce4util6_4.10.1-0ubuntu1~ppa0.12.04.1_amd64.deb) ...
Preparing to replace xfconf 4.8.1-1 (using .../xfconf_4.10.0-0ubuntu1~ppa1_amd64.deb) ...
Unpacking replacement xfconf ...
Preparing to replace libxfconf-0-2 4.8.1-1 (using .../libxfconf-0-2_4.10.0-0ubuntu1~ppa1_amd64.deb) ...
Unpacking replacement libxfconf-0-2 ...
Preparing to replace xfce-keyboard-shortcuts 4.8.1-1 (using .../xfce-keyboard-shortcuts_4.11.0-0ubuntu1~ppa0.12.04.1_all.deb) ...
Unpacking replacement xfce-keyboard-shortcuts ...
Preparing to replace libxfce4ui-1-0 4.8.1-1 (using .../libxfce4ui-1-0_4.11.0-0ubuntu1~ppa0.12.04.1_amd64.deb) ...
Unpacking replacement libxfce4ui-1-0 ...
Selecting previously unselected package libxfce4ui-common.
Unpacking libxfce4ui-common (from .../libxfce4ui-common_4.11.0-0ubuntu1~ppa0.12.04.1_all.deb) ...
Preparing to replace exo-utils 0.6.2-4 (using .../exo-utils_0.10.2-0ubuntu1~ppa0.12.04.1_amd64.deb) ...
Unpacking replacement exo-utils ...
Preparing to replace libexo-common 0.6.2-4 (using .../libexo-common_0.10.2-0ubuntu1~ppa0.12.04.1_all.deb) ...
Unpacking replacement libexo-common ...
Preparing to replace libexo-helpers 0.6.2-4 (using .../libexo-helpers_0.10.2-0ubuntu1~ppa0.12.04.1_amd64.deb) ...
Unpacking replacement libexo-helpers ...
Preparing to replace libexo-1-0 0.6.2-4 (using .../libexo-1-0_0.10.2-0ubuntu1~ppa0.12.04.1_amd64.deb) ...
Unpacking replacement libexo-1-0 ...
Preparing to replace libgarcon-common 0.1.11-0ubuntu1 (using .../libgarcon-common_0.2.1-0ubuntu1~ppa0.12.04.1_all.deb) ...
Unpacking replacement libgarcon-common ...
Preparing to replace libgarcon-1-0 0.1.11-0ubuntu1 (using .../libgarcon-1-0_0.2.1-0ubuntu1~ppa0.12.04.1_amd64.deb) ...
Unpacking replacement libgarcon-1-0 ...
Preparing to replace thunar 1.2.3-3ubuntu2 (using .../thunar_1.6.3-0ubuntu1~ppa0.12.04.1_amd64.deb) ...
Unpacking replacement thunar ...
Preparing to replace libthunarx-2-0 1.2.3-3ubuntu2 (using .../libthunarx-2-0_1.6.3-0ubuntu1~ppa0.12.04.1_amd64.deb) ...
Unpacking replacement libthunarx-2-0 ...
Preparing to replace thunar-data 1.2.3-3ubuntu2 (using .../thunar-data_1.6.3-0ubuntu1~ppa0.12.04.1_all.deb) ...
Unpacking replacement thunar-data ...
Selecting previously unselected package libxfce4ui-2-0.
Unpacking libxfce4ui-2-0 (from .../libxfce4ui-2-0_4.11.0-0ubuntu1~ppa0.12.04.1_amd64.deb) ...
Preparing to replace libxfcegui4-4 4.8.1-5ubuntu1 (using .../libxfcegui4-4_4.10.0-0ubuntu1~ppa1_amd64.deb) ...
Unpacking replacement libxfcegui4-4 ...
Preparing to replace xfce4-panel 4.8.6-2ubuntu2 (using .../xfce4-panel_4.10.1-0ubuntu1~ppa0.12.04.1_amd64.deb) ...
Unpacking replacement xfce4-panel ...
Preparing to replace xfce4-settings 4.8.3-1ubuntu3.1 (using .../xfce4-settings_4.11.1-0ubuntu1~ppa0.12.04.1_amd64.deb) ...
Moving obsolete conffile /etc/xdg/autostart/xfce4-settings-helper-autostart.desktop out of the way...
Unpacking replacement xfce4-settings ...
Preparing to replace xfce4-session 4.8.3-0ubuntu2 (using .../xfce4-session_4.10.1-0ubuntu1~ppa0.12.04.1_amd64.deb) ...
Unpacking replacement xfce4-session ...
Preparing to replace xubuntu-default-settings 12.04.11 (using .../xubuntu-default-settings_12.04.11+ppa2_all.deb) ...
Unpacking replacement xubuntu-default-settings ...
Preparing to replace gigolo 0.4.1-3 (using .../gigolo_0.4.2-1~ppa0.12.04.1_amd64.deb) ...
Unpacking replacement gigolo ...
Selecting previously unselected package gstreamer0.10-ffmpeg.
Unpacking gstreamer0.10-ffmpeg (from .../gstreamer0.10-ffmpeg_0.10.13-1_amd64.deb) ...
Selecting previously unselected package libxfce4ui-utils.
Unpacking libxfce4ui-utils (from .../libxfce4ui-utils_4.11.0-0ubuntu1~ppa0.12.04.1_amd64.deb) ...
Preparing to replace libxfce4util-bin 4.8.2-1 (using .../libxfce4util-bin_4.10.1-0ubuntu1~ppa0.12.04.1_amd64.deb) ...
Unpacking replacement libxfce4util-bin ...
Preparing to replace orage 4.8.3-1 (using .../orage_4.10.0-1~ppa0.12.04.1_amd64.deb) ...
Unpacking replacement orage ...
Preparing to replace parole 0.2.0.6-1 (using .../parole_0.6.1-0ubuntu1~ppa0.12.04.1_amd64.deb) ...
Unpacking replacement parole ...
Preparing to replace thunar-volman 0.6.1-0ubuntu1 (using .../thunar-volman_0.8.0-0ubuntu1~ppa1_amd64.deb) ...
Unpacking replacement thunar-volman ...
Preparing to replace xfburn 0.4.3-4ubuntu1 (using .../xfburn_0.5.0-0ubuntu1~ppa0.12.04.1_amd64.deb) ...
Unpacking replacement xfburn ...
Preparing to replace xfce4-appfinder 4.8.0-3 (using .../xfce4-appfinder_4.10.1-0ubuntu1~ppa0.12.04.1_amd64.deb) ...
Unpacking replacement xfce4-appfinder ...
Preparing to replace xfce4-cpugraph-plugin 1.0.1-2 (using .../xfce4-cpugraph-plugin_1.0.5-0ubuntu1~ppa1_amd64.deb) ...
Unpacking replacement xfce4-cpugraph-plugin ...
Preparing to replace xfce4-datetime-plugin 0.6.1-3ubuntu1 (using .../xfce4-datetime-plugin_0.6.2-0ubuntu1~ppa0.12.04.1_amd64.deb) ...
Unpacking replacement xfce4-datetime-plugin ...
Preparing to replace xfce4-dict 0.6.0-5 (using .../xfce4-dict_0.7.0-1~ppa12.04.1_amd64.deb) ...
Unpacking replacement xfce4-dict ...
Preparing to replace xfce4-indicator-plugin 0.4.0-0ubuntu2 (using .../xfce4-indicator-plugin_0.4.0-0ubuntu2+ppa1_amd64.deb) ...
Unpacking replacement xfce4-indicator-plugin ...
Preparing to replace xfce4-mailwatch-plugin 1.1.0-5 (using .../xfce4-mailwatch-plugin_1.2.0-1~ppa0.12.04.1_amd64.deb) ...
Unpacking replacement xfce4-mailwatch-plugin ...
Preparing to replace xfce4-netload-plugin 1.1.0-1 (using .../xfce4-netload-plugin_1.2.0-0ubuntu1~ppa1_amd64.deb) ...
Unpacking replacement xfce4-netload-plugin ...
Preparing to replace xfce4-notes 1.7.7-2ubuntu1 (using .../xfce4-notes_1.7.7-2ubuntu1+ppa1_amd64.deb) ...
Unpacking replacement xfce4-notes ...
Preparing to replace xfce4-notes-plugin 1.7.7-2ubuntu1 (using .../xfce4-notes-plugin_1.7.7-2ubuntu1+ppa1_amd64.deb) ...
Unpacking replacement xfce4-notes-plugin ...
Preparing to replace xfce4-notifyd 0.2.2-1 (using .../xfce4-notifyd_0.2.4-2~ppa0.12.04.1_amd64.deb) ...
Unpacking replacement xfce4-notifyd ...
Preparing to replace xfce4-places-plugin 1.2.0-3 (using .../xfce4-places-plugin_1.6.0-1~ppa0.12.04.1_amd64.deb) ...
Unpacking replacement xfce4-places-plugin ...
Preparing to replace xfce4-power-manager 1.0.11-0ubuntu2 (using .../xfce4-power-manager_1.2.0-1ubuntu1.1~ppa1_amd64.deb) ...
Unpacking replacement xfce4-power-manager ...
Preparing to replace xfce4-power-manager-data 1.0.11-0ubuntu2 (using .../xfce4-power-manager-data_1.2.0-1ubuntu1.1~ppa1_all.deb) ...
Unpacking replacement xfce4-power-manager-data ...
Preparing to replace xfce4-quicklauncher-plugin 1.9.4-9 (using .../xfce4-quicklauncher-plugin_1.9.4-9+ppa1_amd64.deb) ...
Unpacking replacement xfce4-quicklauncher-plugin ...
Preparing to replace xfce4-screenshooter 1.8.0-2 (using .../xfce4-screenshooter_1.8.1-1~ppa1_amd64.deb) ...
Unpacking replacement xfce4-screenshooter ...
Preparing to replace xfce4-systemload-plugin 1:1.0.0-1ubuntu1 (using .../xfce4-systemload-plugin_1%3a1.1.1-1ubuntu1~ppa1_amd64.deb) ...
Unpacking replacement xfce4-systemload-plugin ...
Preparing to replace xfce4-taskmanager 1.0.0-2 (using .../xfce4-taskmanager_1.0.1-1~ppa0.12.04.1_amd64.deb) ...
Unpacking replacement xfce4-taskmanager ...
Preparing to replace xfce4-terminal 0.4.8-1ubuntu1 (using .../xfce4-terminal_0.6.3-1ubuntu1~ppa0.12.04.1_amd64.deb) ...
Unpacking replacement xfce4-terminal ...
Preparing to replace xfce4-verve-plugin 1.0.0-1 (using .../xfce4-verve-plugin_1.0.0-1+ppa1_amd64.deb) ...
Unpacking replacement xfce4-verve-plugin ...
Preparing to replace xfce4-weather-plugin 0.7.4-5~ubuntu12.04.1 (using .../xfce4-weather-plugin_0.8.3-0ubuntu1~ppa0.12.04.1_amd64.deb) ...
Unpacking replacement xfce4-weather-plugin ...
Preparing to replace xfce4-xkb-plugin 0.5.4.3-1ubuntu1 (using .../xfce4-xkb-plugin_1%3a0.7.0-0ubuntu1~ppa0.12.04.1_amd64.deb) ...
Unpacking replacement xfce4-xkb-plugin ...
Preparing to replace xfwm4 4.8.3-1ubuntu1.1 (using .../xfwm4_4.11.1-0ubuntu1~ppa0.12.04.1_amd64.deb) ...
Unpacking replacement xfwm4 ...
Selecting previously unselected package xscreensaver.
Unpacking xscreensaver (from .../xscreensaver_5.15-2ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for libglib2.0-0 ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for gconf2 ...
Setting up tex-common (2.10) ...
Not replacing deleted config file /etc/texmf/texmf.d/05TeXMF.cnf
Not replacing deleted config file /etc/texmf/texmf.d/15Plain.cnf
Not replacing deleted config file /etc/texmf/texmf.d/45TeXinputs.cnf
Not replacing deleted config file /etc/texmf/texmf.d/55Fonts.cnf
Not replacing deleted config file /etc/texmf/texmf.d/65BibTeX.cnf
Not replacing deleted config file /etc/texmf/texmf.d/75DviPS.cnf
Not replacing deleted config file /etc/texmf/texmf.d/80DVIPDFMx.cnf
Not replacing deleted config file /etc/texmf/texmf.d/85Misc.cnf
Not replacing deleted config file /etc/texmf/texmf.d/90TeXDoc.cnf
Not replacing deleted config file /etc/texmf/texmf.d/95NonPath.cnf
Not replacing deleted config file /etc/texmf/updmap.d/00updmap.cfg
update-texmf: Basic configuration file /etc/texmf/texmf.d/05TeXMF.cnf missing.
Exiting.
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libxfce4util-common (4.10.1-0ubuntu1~ppa0.12.04.1) ...
Setting up libxfce4util6 (4.10.1-0ubuntu1~ppa0.12.04.1) ...
Setting up xfconf (4.10.0-0ubuntu1~ppa1) ...
Setting up libxfconf-0-2 (4.10.0-0ubuntu1~ppa1) ...
Setting up libxfce4ui-common (4.11.0-0ubuntu1~ppa0.12.04.1) ...
Installing new version of config file /etc/xdg/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml ...
Setting up xfce-keyboard-shortcuts (4.11.0-0ubuntu1~ppa0.12.04.1) ...
Setting up libxfce4ui-1-0 (4.11.0-0ubuntu1~ppa0.12.04.1) ...
Setting up libexo-common (0.10.2-0ubuntu1~ppa0.12.04.1) ...
Installing new version of config file /etc/xdg/xfce4/helpers.rc ...
Setting up libexo-helpers (0.10.2-0ubuntu1~ppa0.12.04.1) ...
Setting up libexo-1-0 (0.10.2-0ubuntu1~ppa0.12.04.1) ...
Setting up exo-utils (0.10.2-0ubuntu1~ppa0.12.04.1) ...
Setting up libgarcon-common (0.2.1-0ubuntu1~ppa0.12.04.1) ...
Installing new version of config file /etc/xdg/menus/xfce-applications.menu ...
Setting up libgarcon-1-0 (0.2.1-0ubuntu1~ppa0.12.04.1) ...
Setting up thunar-data (1.6.3-0ubuntu1~ppa0.12.04.1) ...
Installing new version of config file /etc/xdg/Thunar/uca.xml ...
Setting up libthunarx-2-0 (1.6.3-0ubuntu1~ppa0.12.04.1) ...
Setting up thunar (1.6.3-0ubuntu1~ppa0.12.04.1) ...
Setting up libxfce4ui-2-0 (4.11.0-0ubuntu1~ppa0.12.04.1) ...
Setting up libxfcegui4-4 (4.10.0-0ubuntu1~ppa1) ...
Setting up xfce4-panel (4.10.1-0ubuntu1~ppa0.12.04.1) ...
Installing new version of config file /etc/xdg/xfce4/panel/default.xml ...
Setting up xfce4-settings (4.11.1-0ubuntu1~ppa0.12.04.1) ...
Installing new version of config file /etc/xdg/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml ...
Removing obsolete conffile /etc/xdg/autostart/xfce4-settings-helper-autostart.desktop ...
Setting up xfce4-session (4.10.1-0ubuntu1~ppa0.12.04.1) ...
Installing new version of config file /etc/xdg/xfce4/xinitrc ...
Installing new version of config file /etc/xdg/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml ...
Setting up xubuntu-default-settings (12.04.11+ppa2) ...
Installing new version of config file /etc/xdg/xdg-xubuntu/menus/xfce-applications.menu ...
Setting up gigolo (0.4.2-1~ppa0.12.04.1) ...
Setting up gstreamer0.10-ffmpeg (0.10.13-1) ...
Setting up libxfce4ui-utils (4.11.0-0ubuntu1~ppa0.12.04.1) ...
Setting up libxfce4util-bin (4.10.1-0ubuntu1~ppa0.12.04.1) ...
Setting up orage (4.10.0-1~ppa0.12.04.1) ...
Setting up parole (0.6.1-0ubuntu1~ppa0.12.04.1) ...
Setting up thunar-volman (0.8.0-0ubuntu1~ppa1) ...
Setting up xfburn (0.5.0-0ubuntu1~ppa0.12.04.1) ...
Setting up xfce4-appfinder (4.10.1-0ubuntu1~ppa0.12.04.1) ...
Setting up xfce4-cpugraph-plugin (1.0.5-0ubuntu1~ppa1) ...
Setting up xfce4-datetime-plugin (0.6.2-0ubuntu1~ppa0.12.04.1) ...
Setting up xfce4-dict (0.7.0-1~ppa12.04.1) ...
Setting up xfce4-indicator-plugin (0.4.0-0ubuntu2+ppa1) ...
Setting up xfce4-mailwatch-plugin (1.2.0-1~ppa0.12.04.1) ...
Setting up xfce4-netload-plugin (1.2.0-0ubuntu1~ppa1) ...
Setting up xfce4-notes (1.7.7-2ubuntu1+ppa1) ...
Setting up xfce4-notes-plugin (1.7.7-2ubuntu1+ppa1) ...
Setting up xfce4-notifyd (0.2.4-2~ppa0.12.04.1) ...
Setting up xfce4-places-plugin (1.6.0-1~ppa0.12.04.1) ...
Setting up xfce4-power-manager-data (1.2.0-1ubuntu1.1~ppa1) ...
Setting up xfce4-power-manager (1.2.0-1ubuntu1.1~ppa1) ...
Installing new version of config file /etc/xdg/autostart/xfce4-power-manager.desktop ...
Setting up xfce4-quicklauncher-plugin (1.9.4-9+ppa1) ...
Setting up xfce4-screenshooter (1.8.1-1~ppa1) ...
Setting up xfce4-systemload-plugin (1:1.1.1-1ubuntu1~ppa1) ...
Setting up xfce4-taskmanager (1.0.1-1~ppa0.12.04.1) ...
Setting up xfce4-terminal (0.6.3-1ubuntu1~ppa0.12.04.1) ...
update-alternatives: using /usr/bin/gnome-terminal.wrapper to provide /usr/bin/x-terminal-emulator (x-terminal-emulator) in auto mode.
Setting up xfce4-verve-plugin (1.0.0-1+ppa1) ...
Setting up xfce4-weather-plugin (0.8.3-0ubuntu1~ppa0.12.04.1) ...
Setting up xfce4-xkb-plugin (1:0.7.0-0ubuntu1~ppa0.12.04.1) ...
Setting up xfwm4 (4.11.1-0ubuntu1~ppa0.12.04.1) ...
update-alternatives: using /usr/bin/metacity to provide /usr/bin/x-window-manager (x-window-manager) in auto mode.
Setting up xscreensaver (5.15-2ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 tex-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

```




> **Toz said:**
> Okay, you need the 4.10 PPA installed before you can use the 4.12 PPA (see: [https://launchpad.net/~xubuntu-dev/+archive/xfce-4.12](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.12)).

So lets try this:
```
sudo add-apt-repository ppa:xubuntu-dev/xfce-4.10
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Toz on 2014-06-14
We're getting close. You still have an issue with tex-common, but this isn't related to Xfce.

First, to fix the xfdesktop issue, go to Settings Manager >> Session and Startup >> Session tab and click on the "Clear saved sessions" button (select "Proceed" when prompted). Then log out and back in again. Does this solve the initial desktop issue? If not, can you try again:
```
apt-cache policy xfdesktop4
```

As for tex-common, we can look at fixing that later.

---

### Post by bekirs on 2014-06-14
My desktop is still not there. Here is the output after typing the command:

```
apt-cache policy xfdesktop4xfdesktop4:
  Installed: (none)
  Candidate: 4.11.2-0ubuntu1~ppa0.12.04.1
  Version table:
     4.11.2-0ubuntu1~ppa0.12.04.1 0
        500 http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu/ precise/main amd64 Packages
     4.10.2-0ubuntu1~ppa0.12.04.1 0
        500 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main amd64 Packages
     4.8.3-2ubuntu7 0
        500 http://archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages
        100 /var/lib/dpkg/status



```

> **Toz said:**
> We're getting close. You still have an issue with tex-common, but this isn't related to Xfce.

First, to fix the xfdesktop issue, go to Settings Manager >> Session and Startup >> Session tab and click on the "Clear saved sessions" button (select "Proceed" when prompted). Then log out and back in again. Does this solve the initial desktop issue? If not, can you try again:
```
apt-cache policy xfdesktop4
```

As for tex-common, we can look at fixing that later.

---

### Post by Toz on 2014-06-14
Its not installed. Try installing it now:
```
sudo apt-get install xfdesktop4
```
...then Alt+F2 and run:
```
xfdesktop --reload
```

Does it work now?

---

### Post by bekirs on 2014-06-14
It seems good; I think it worked...

Output1:

```
sudo apt-get install xfdesktop4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ttf-dejavu-extra libunistring0 po-debconf intltool-debian luatex
  libatk-wrapper-java gettext tzdata-java libatk-wrapper-java-jni
  libgettextpo0 ca-certificates-java libmail-sendmail-perl
  libsys-hostname-long-perl
Use 'apt-get autoremove' to remove them.
Suggested packages:
  menu
The following NEW packages will be installed:
  xfdesktop4
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 171 kB of archives.
After this operation, 540 kB of additional disk space will be used.
Get:1 http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu/ precise/main xfdesktop4 amd64 4.11.2-0ubuntu1~ppa0.12.04.1 [171 kB]
Fetched 171 kB in 1s (106 kB/s)     
Selecting previously unselected package xfdesktop4.
(Reading database ... 1055909 files and directories currently installed.)
Unpacking xfdesktop4 (from .../xfdesktop4_4.11.2-0ubuntu1~ppa0.12.04.1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Setting up tex-common (2.10) ...
Not replacing deleted config file /etc/texmf/texmf.d/05TeXMF.cnf
Not replacing deleted config file /etc/texmf/texmf.d/15Plain.cnf
Not replacing deleted config file /etc/texmf/texmf.d/45TeXinputs.cnf
Not replacing deleted config file /etc/texmf/texmf.d/55Fonts.cnf
Not replacing deleted config file /etc/texmf/texmf.d/65BibTeX.cnf
Not replacing deleted config file /etc/texmf/texmf.d/75DviPS.cnf
Not replacing deleted config file /etc/texmf/texmf.d/80DVIPDFMx.cnf
Not replacing deleted config file /etc/texmf/texmf.d/85Misc.cnf
Not replacing deleted config file /etc/texmf/texmf.d/90TeXDoc.cnf
Not replacing deleted config file /etc/texmf/texmf.d/95NonPath.cnf
Not replacing deleted config file /etc/texmf/updmap.d/00updmap.cfg
update-texmf: Basic configuration file /etc/texmf/texmf.d/05TeXMF.cnf missing.
Exiting.
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up xfdesktop4 (4.11.2-0ubuntu1~ppa0.12.04.1) ...
Errors were encountered while processing:
 tex-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
```]

> **Toz said:**
> Its not installed. Try installing it now:
```
sudo apt-get install xfdesktop4
```
...then Alt+F2 and run:
```
xfdesktop --reload
```

Does it work now?

---

### Post by Toz on 2014-06-14
So its working now? Do you have a desktop again?

You might also want to clean up your installation:
```
sudo apt-get autoremove
```

---

### Post by bekirs on 2014-06-14
yes, it works now. Thanks a lot!

and the output for removing other installations:

```
sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ca-certificates-java gettext intltool-debian libatk-wrapper-java
  libatk-wrapper-java-jni libgettextpo0 libmail-sendmail-perl
  libsys-hostname-long-perl libunistring0 luatex po-debconf ttf-dejavu-extra
  tzdata-java
0 upgraded, 0 newly installed, 13 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 18.6 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 1055916 files and directories currently installed.)
Removing ca-certificates-java ...
Removing po-debconf ...
Removing intltool-debian ...
Removing gettext ...
Removing libatk-wrapper-java-jni ...
Removing libatk-wrapper-java ...
Removing libgettextpo0 ...
Removing libmail-sendmail-perl ...
Removing libsys-hostname-long-perl ...
Removing libunistring0 ...
Removing luatex ...
Removing ttf-dejavu-extra ...
Removing tzdata-java ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 removed doc-base files...
Registering documents with scrollkeeper...
Processing triggers for install-info ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for fontconfig ...
Setting up tex-common (2.10) ...
Not replacing deleted config file /etc/texmf/texmf.d/05TeXMF.cnf
Not replacing deleted config file /etc/texmf/texmf.d/15Plain.cnf
Not replacing deleted config file /etc/texmf/texmf.d/45TeXinputs.cnf
Not replacing deleted config file /etc/texmf/texmf.d/55Fonts.cnf
Not replacing deleted config file /etc/texmf/texmf.d/65BibTeX.cnf
Not replacing deleted config file /etc/texmf/texmf.d/75DviPS.cnf
Not replacing deleted config file /etc/texmf/texmf.d/80DVIPDFMx.cnf
Not replacing deleted config file /etc/texmf/texmf.d/85Misc.cnf
Not replacing deleted config file /etc/texmf/texmf.d/90TeXDoc.cnf
Not replacing deleted config file /etc/texmf/texmf.d/95NonPath.cnf
Not replacing deleted config file /etc/texmf/updmap.d/00updmap.cfg
update-texmf: Basic configuration file /etc/texmf/texmf.d/05TeXMF.cnf missing.
Exiting.
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 tex-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

> **Toz said:**
> So its working now? Do you have a desktop again?

You might also want to clean up your installation:
```
sudo apt-get autoremove
```

---

### Post by Toz on 2014-06-14
Glad to hear its back up and working again.

---

### Post by lisati on 2014-06-14
> **Toz said:**
> Glad to hear its back up and working again.
Agreed.

From the error messages, it seems to me that something's not quite right with *tex*. This probably needs attention at some point, otherwise other issues could arise.

---

### Post by bekirs on 2014-06-14
maybe I need to open another thread for TeXWorks issues...

---

