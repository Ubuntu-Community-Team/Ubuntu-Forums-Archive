---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2015-10-12
forum: Desktop Environments
---

### Post by asaadirfans on 2015-10-12
I'm using ubuntu 12.04.5 and when i try to do this:

```
sudo apt-get -f install

```

I get the following error:
```

asaad@VAIO:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
libopenni-nite-dev
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 579300 files and directories currently installed.)
Removing libopenni-nite-dev ...
Failed: Error!
dpkg: error processing libopenni-nite-dev (--remove):
subprocess installed pre-removal script returned error exit status 255
No apport report written because MaxReports is reached already
Errors were encountered while processing:
libopenni-nite-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
asaad@VAIO:~$ 

```


Any help would be really appreciated.

---

### Post by Bashing-om on 2015-10-12
asaadirfans; Hello;

Per:
[http://packages.ubuntu.com/search?keywords=libopenni-nite-dev&searchon=names&suite=precise-updates&section=all](http://packages.ubuntu.com/search?keywords=libopenni-nite-dev&searchon=names&suite=precise-updates&section=all)
That " libopenni-nite-dev" is not a standard package. So where did it come from ? I can accept that as it is not standard, the package management system is not able to track it.

Let's get a bit more info;
Where did it come from (?):
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*
apt-cache policy libopenni-nite-dev

```
And what have we on the system to work with ?
```

dpkg -l libopenni-nite-dev
dpkg -L libopenni-nite-dev

``` that the package manager might be aware of .

Do we install it ( yuk) or RE-Move it from the system ?

[INDENT][INDENT]what to do, OH
[INDENT][INDENT][INDENT]what to do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by asaadirfans on 2015-10-12
the output of cat -n /etc/apt/sources.list :  (if thats what you want).
```

asaad@VAIO:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 12.04.5 LTS _Precise Pangolin_ - Release i386 (20140807.1)]/ precise main restricted
     2    
     3    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4    # newer versions of the distribution.
     5    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
     6    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise restricted main multiverse universe #Added by software-properties
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    
    11    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    12    ## team. Also, please note that software in universe WILL NOT receive any
    13    ## review or updates from the Ubuntu security team.
    14    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
    15    
    16    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    17    ## team, and may not be under a free licence. Please satisfy yourself as to 
    18    ## your rights to use the software. Also, please note that software in 
    19    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    20    ## security team.
    21    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
    22    
    23    ## N.B. software from this repository may not have been tested as
    24    ## extensively as that contained in the main release, although it includes
    25    ## newer versions of some applications which may provide useful features.
    26    ## Also, please note that software in backports WILL NOT receive any review
    27    ## or updates from the Ubuntu security team.
    28    
    29    
    30    ## Uncomment the following two lines to add software from Canonical's
    31    ## 'partner' repository.
    32    ## This software is not part of Ubuntu, but is offered by Canonical and the
    33    ## respective vendors as a service to Ubuntu users.
    34    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    35    deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    36    
    37    ## This software is not part of Ubuntu, but is offered by third-party
    38    ## developers who want to ship their latest software.
    39    deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    40    deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security restricted main multiverse universe
    41    deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security restricted main multiverse universe #Added by software-properties
    42    deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    43    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates restricted main multiverse universe
    44    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates restricted main multiverse universe #Added by software-properties
    45    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-proposed restricted main multiverse universe
    46    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-proposed restricted main multiverse universe #Added by software-properties
    47    
    48    deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) precise main unive
asaad@VAIO:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/dropbox.list <==
deb [arch=i386,amd64] [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) precise main


==> /etc/apt/sources.list.d/dropbox.list.save <==
deb [arch=i386,amd64] [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) precise main


==> /etc/apt/sources.list.d/eclipse-team-ppa-precise.list <==
deb [http://ppa.launchpad.net/eclipse-team/ppa/ubuntu](http://ppa.launchpad.net/eclipse-team/ppa/ubuntu) precise main
deb-src [http://ppa.launchpad.net/eclipse-team/ppa/ubuntu](http://ppa.launchpad.net/eclipse-team/ppa/ubuntu) precise main


==> /etc/apt/sources.list.d/eclipse-team-ppa-precise.list.save <==
deb [http://ppa.launchpad.net/eclipse-team/ppa/ubuntu](http://ppa.launchpad.net/eclipse-team/ppa/ubuntu) precise main
# deb-src [http://ppa.launchpad.net/eclipse-team/ppa/ubuntu](http://ppa.launchpad.net/eclipse-team/ppa/ubuntu) precise main


==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main


==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main


==> /etc/apt/sources.list.d/ros-latest.list <==
deb [http://packages.ros.org/ros/ubuntu](http://packages.ros.org/ros/ubuntu) precise main


==> /etc/apt/sources.list.d/ros-latest.list.save <==
deb [http://packages.ros.org/ros/ubuntu](http://packages.ros.org/ros/ubuntu) precise main


==> /etc/apt/sources.list.d/v-launchpad-jochen-sprickerhof-de-pcl-precise.list <==
deb [http://ppa.launchpad.net/v-launchpad-jochen-sprickerhof-de/pcl/ubuntu](http://ppa.launchpad.net/v-launchpad-jochen-sprickerhof-de/pcl/ubuntu) precise main
deb-src [http://ppa.launchpad.net/v-launchpad-jochen-sprickerhof-de/pcl/ubuntu](http://ppa.launchpad.net/v-launchpad-jochen-sprickerhof-de/pcl/ubuntu) precise main


==> /etc/apt/sources.list.d/v-launchpad-jochen-sprickerhof-de-pcl-precise.list.save <==
deb [http://ppa.launchpad.net/v-launchpad-jochen-sprickerhof-de/pcl/ubuntu](http://ppa.launchpad.net/v-launchpad-jochen-sprickerhof-de/pcl/ubuntu) precise main
deb-src [http://ppa.launchpad.net/v-launchpad-jochen-sprickerhof-de/pcl/ubuntu](http://ppa.launchpad.net/v-launchpad-jochen-sprickerhof-de/pcl/ubuntu) precise main


==> /etc/apt/sources.list.d/yani-iatsl-precise.list <==
deb [http://ppa.launchpad.net/yani/iatsl/ubuntu](http://ppa.launchpad.net/yani/iatsl/ubuntu) precise main
deb-src [http://ppa.launchpad.net/yani/iatsl/ubuntu](http://ppa.launchpad.net/yani/iatsl/ubuntu) precise main


==> /etc/apt/sources.list.d/yani-iatsl-precise.list.save <==
deb [http://ppa.launchpad.net/yani/iatsl/ubuntu](http://ppa.launchpad.net/yani/iatsl/ubuntu) precise main
deb-src [http://ppa.launchpad.net/yani/iatsl/ubuntu](http://ppa.launchpad.net/yani/iatsl/ubuntu) precise main
asaad@VAIO:~$ apt-cache policy libopenni-nite-dev


```

---

### Post by Bashing-om on 2015-10-12
asaadirfans; Yeah,

That is a start, and the output of the other requested commands ?
And please use "code tags" to relay the outputs .
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And what do you want to do with the app ?

[INDENT][INDENT]a process of learning
[/INDENT][/INDENT]

---

### Post by asaadirfans on 2015-10-12
output of tail -v -n +1 /etc/apt/sources.list.d/*  :


```

asaad@VAIO:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/dropbox.list <==
deb [arch=i386,amd64] http://linux.dropbox.com/ubuntu precise main


==> /etc/apt/sources.list.d/dropbox.list.save <==
deb [arch=i386,amd64] http://linux.dropbox.com/ubuntu precise main


==> /etc/apt/sources.list.d/eclipse-team-ppa-precise.list <==
deb http://ppa.launchpad.net/eclipse-team/ppa/ubuntu precise main
deb-src http://ppa.launchpad.net/eclipse-team/ppa/ubuntu precise main


==> /etc/apt/sources.list.d/eclipse-team-ppa-precise.list.save <==
deb http://ppa.launchpad.net/eclipse-team/ppa/ubuntu precise main
# deb-src http://ppa.launchpad.net/eclipse-team/ppa/ubuntu precise main


==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/ros-latest.list <==
deb http://packages.ros.org/ros/ubuntu precise main


==> /etc/apt/sources.list.d/ros-latest.list.save <==
deb http://packages.ros.org/ros/ubuntu precise main


==> /etc/apt/sources.list.d/v-launchpad-jochen-sprickerhof-de-pcl-precise.list <==
deb http://ppa.launchpad.net/v-launchpad-jochen-sprickerhof-de/pcl/ubuntu precise main
deb-src http://ppa.launchpad.net/v-launchpad-jochen-sprickerhof-de/pcl/ubuntu precise main


==> /etc/apt/sources.list.d/v-launchpad-jochen-sprickerhof-de-pcl-precise.list.save <==
deb http://ppa.launchpad.net/v-launchpad-jochen-sprickerhof-de/pcl/ubuntu precise main
deb-src http://ppa.launchpad.net/v-launchpad-jochen-sprickerhof-de/pcl/ubuntu precise main


==> /etc/apt/sources.list.d/yani-iatsl-precise.list <==
deb http://ppa.launchpad.net/yani/iatsl/ubuntu precise main
deb-src http://ppa.launchpad.net/yani/iatsl/ubuntu precise main


==> /etc/apt/sources.list.d/yani-iatsl-precise.list.save <==
deb http://ppa.launchpad.net/yani/iatsl/ubuntu precise main
deb-src http://ppa.launchpad.net/yani/iatsl/ubuntu precise main
asaad@VAIO:~$ 
```



output of [COLOR=#000000][FONT=Ubuntu Mono]apt-cache policy libopenni-nite-dev[/FONT][/COLOR]

```

asaad@VAIO:~$ apt-cache policy libopenni-nite-dev
libopenni-nite-dev:
  Installed: 1.3.1.5~precise
  Candidate: 1.3.1.5~precise
  Version table:
 *** 1.3.1.5~precise 0
        500 http://packages.ros.org/ros/ubuntu/ precise/main i386 Packages
        100 /var/lib/dpkg/status
asaad@VAIO:~$ 























```

Actually, i didnt really mean to install this very package but another one (i.e. openni) but ended up with this one.

---

### Post by asaadirfans on 2015-10-12
Here are the rest of the outputs.

```


asaad@VAIO:~$ dpkg -l libopenni-nite-dev
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ri  libopenni-nite 1.3.1.5~precis Nite development package
asaad@VAIO:~$ 





```



```

asaad@VAIO:~$ dpkg -L libopenni-nite-dev
/.
/usr
/usr/lib
/usr/lib/pkgconfig
/usr/lib/pkgconfig/nite-dev.pc
/usr/lib/libXnVFeatures.so
/usr/lib/libXnVCNITE_1_3_1.so
/usr/lib/libXnVHandGenerator_1_3_1.so
/usr/lib/libXnVFeatures_1_3_1.so
/usr/lib/libXnVHandGenerator.so
/usr/lib/libXnVNite.so
/usr/lib/libXnVNite_1_3_1.so
/usr/include
/usr/include/nite
/usr/include/nite/XnVComplexMessage.h
/usr/include/nite/XnVSelectableSlider2D.h
/usr/include/nite/XnVMultiProcessFlowClient.h
/usr/include/nite/XnVNiteLog.h
/usr/include/nite/XnVGesture.h
/usr/include/nite/XnVSessionMessage.h
/usr/include/nite/XnVMultiProcessFlowServer.h
/usr/include/nite/XnVHandPointContext.h
/usr/include/nite/XnVCircle.h
/usr/include/nite/XnVDeviceControl.h
/usr/include/nite/XnVSlider3D.h
/usr/include/nite/XnVVirtualCoordinates.h
/usr/include/nite/XnV3DVector.h
/usr/include/nite/XnVNite.h
/usr/include/nite/XnVNiteVersion.h
/usr/include/nite/XnVSelectableSlider1D.h
/usr/include/nite/XnVDepthMessage.h
/usr/include/nite/XnVMultiItemHysteresis1D.h
/usr/include/nite/XnVMessageMux.h
/usr/include/nite/XnVImageMessage.h
/usr/include/nite/XnVWaveDetector.h
/usr/include/nite/XnVNiteStatus.h
/usr/include/nite/XnVActivationMessage.h
/usr/include/nite/XnVPointTracker.h
/usr/include/nite/XnVDepthControl.h
/usr/include/nite/XnVSessionGenerator.h
/usr/include/nite/XnVBroadcaster.h
/usr/include/nite/XnVMessageGenerator.h
/usr/include/nite/XnVDepthGenerator.h
/usr/include/nite/XnVSlider1D.h
/usr/include/nite/XnVNiteEvents.h
/usr/include/nite/XnVCCMessage.h
/usr/include/nite/XnVSessionListener.h
/usr/include/nite/XnVSlider2D.h
/usr/include/nite/XnVSwipeDetector.h
/usr/include/nite/XnVPointArea.h
/usr/include/nite/XnVMathCommon.h
/usr/include/nite/XnCommon.h
/usr/include/nite/XnVNiteFramework.h
/usr/include/nite/XnVFlowRouter.h
/usr/include/nite/XnVDirection.h
/usr/include/nite/XnVPointMessage.h
/usr/include/nite/XnVDeviceMessage.h
/usr/include/nite/XnVFilter.h
/usr/include/nite/XnVSessionManager.h
/usr/include/nite/XnVNiteDefs.h
/usr/include/nite/XnVNiteControls.h
/usr/include/nite/XnVHandle.h
/usr/include/nite/XnVMultiItemHysteresis2D.h
/usr/include/nite/XnVClickableVirtualPlane.h
/usr/include/nite/XnVMessage.h
/usr/include/nite/XnVDeviceFilter.h
/usr/include/nite/XnVSteadyDetector.h
/usr/include/nite/XnVMultipleHands.h
/usr/include/nite/XnVImageGenerator.h
/usr/include/nite/XnVPushDetector.h
/usr/include/nite/XnVPointFilter.h
/usr/include/nite/XnVCircleDetector.h
/usr/include/nite/XnVDeviceGenerator.h
/usr/include/nite/XnVPointControl.h
/usr/include/nite/XnVPointDenoiser.h
/usr/include/nite/XnVMessageListener.h
/etc
/etc/openni
/etc/openni/h.dat
/etc/openni/FeatureExtraction.ini
/etc/openni/Sample-Tracking.xml
/etc/openni/Sample-Scene.xml
/etc/openni/Sample-User.xml
/etc/openni/Nite.ini
/etc/openni/s.dat




```

---

### Post by asaadirfans on 2015-10-12
This libopenni-nite-dev package isnt allowing installtion,uninstallation of any other package(s) either. Nor does it get removed itself:

```

asaad@VAIO:~$ sudo apt-get remove libopenni-nite-dev 
[sudo] password for asaad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libopenni-nite-dev
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 579300 files and directories currently installed.)
Removing libopenni-nite-dev ...
Failed: Error!
dpkg: error processing libopenni-nite-dev (--remove):
 subprocess installed pre-removal script returned error exit status 255
Errors were encountered while processing:
 libopenni-nite-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
asaad@VAIO:~$ 



```

---

### Post by Bashing-om on 2015-10-12
asaadirfans; Well, well ...

We now know the source:
> 
500 [http://packages.ros.org/ros/ubuntu/](http://packages.ros.org/ros/ubuntu/) precise/main i386 Packages

We know it is a PPA .. but we may have a serious problem:
> 
ri  libopenni-nite 1.3.1.5~precis Nite development package

Where in that 1st field is the status .. r=removed; i=still installed.

Let's TRY and see if the package manager will cope - I have my doubts as to what will transpire.
Do terminal commands:
```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:ros/ubuntu

```
Several maybes here as in the correct syntax name, and if  'ppa-purge'  incorporates from the author the ability to revert the package to what is available in our software repository .

Run the ppa-purge command, and we see where we go from here. We may have our work cut out for us.

[INDENT][INDENT]let's do this
[/INDENT][/INDENT]

---

### Post by asaadirfans on 2015-10-12
```

asaad@VAIO:~$ sudo apt-get install ppa-purge
[sudo] password for asaad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libopenni-nite-dev : Depends: libopenni-dev (>= 1.5.4.0~precise) but it is not going to be installed
 ppa-purge : Depends: aptitude but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
asaad@VAIO:~$ 

```


```

asaad@VAIO:~$ sudo ppa-purge ppa:ros/ubuntu
sudo: ppa-purge: command not found
asaad@VAIO:~$ ppa 





```

---

### Post by Bashing-om on 2015-10-12
asaadirfans; Yuk.

Can not install any new stuff 'til we get the package manager fixed.
OK ..... Let's try:
```

sudo add-apt-repository --remove ppa:ros/ubuntu

``` where maybe the repository syntax is correct .

[INDENT][INDENT]maybe Yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by asaadirfans on 2015-10-12
```


asaad@VAIO:~$ sudo add-apt-repository --remove ppa:ros/ubuntu
Cannot access PPA (https://launchpad.net/api/1.0/~ros/+archive/ubuntu) to get PPA information, please check your internet connection.
asaad@VAIO:~$ 


```

BUT, I have an internet connection which is working fine. :)

---

### Post by Bashing-om on 2015-10-12
asaadirfans; Naw...

Package manager just telling us how silly I am. Just does not accept the syntax as valid:
OK ,, once more:
```

sudo add-apt-repository "deb http://packages.ros.org/ros/ubuntu precise main"

```

See now what results. 

[INDENT][INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT][/INDENT]

---

### Post by asaadirfans on 2015-10-12
```


asaad@VAIO:~$ sudo add-apt-repository "deb http://packages.ros.org/ros/ubuntu precise main"
asaad@VAIO:~$ 

```

---

### Post by Bashing-om on 2015-10-12
asaadirfans; Hey, hey ...

Looks good so far .. a return to prompt means the system did as told, no sass - no back-talk .
Now what have we in the sources list ? Let's see if the source is removed - and if not we remove it manually .
```

cat /etc/apt/sources.list.d/ros-latest.list

```

[INDENT][INDENT]making progress
[/INDENT][/INDENT]

---

### Post by asaadirfans on 2015-10-12
```

asaad@VAIO:~$ cat /etc/apt/sources.list.d/ros-latest.list
deb http://packages.ros.org/ros/ubuntu precise main
asaad@VAIO:~$ 

```

---

### Post by Bashing-om on 2015-10-12
asaadirfans; OK,

Did not and I am not surprised. I recon the system expects us to know what we want to do, will not make up our mind for us -
Let's remove these, as we know we are not going to ever have a use for this PPA:
```

sudo rm /etc/apt/sources.list.d/ros-latest.list
sudo rm /etc/apt/sources.list.d/ros-latest.list.save

```
Now what results :
```

sudo apt-get update
sudo apt-get dist-upgrade

```
where 'dist-upgrade' will use apt's smart mode to deal with dependencies and new kernels - it has nothing to do with a release upgrade !

[INDENT][INDENT]maybe the better now 
[/INDENT][/INDENT]

---

### Post by asaadirfans on 2015-10-12
```


asaad@VAIO:~$ sudo apt-get update
Hit http://dl.google.com stable Release.gpg
Hit http://archive.canonical.com precise Release.gpg                                                                                            
Hit http://dl.google.com stable Release                                                                                                         
Hit http://packages.ros.org precise Release.gpg                                                                                                 
Hit http://extras.ubuntu.com precise Release.gpg                                                                                                
Hit http://archive.ubuntu.com precise Release.gpg                                                                                               
Hit http://archive.ubuntu.com precise-updates Release.gpg                                                                                       
Hit http://archive.ubuntu.com precise-proposed Release.gpg                                                                                      
Hit http://archive.ubuntu.com precise-backports Release.gpg                                                                                     
Hit http://us.archive.ubuntu.com precise Release.gpg                                                                                            
Hit http://dl.google.com stable/main i386 Packages                                                                                              
Hit http://security.ubuntu.com precise-security Release.gpg                                                                                     
Ign http://ppa.launchpad.net precise Release.gpg                                                                                                
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                
Hit http://archive.canonical.com precise Release                                                                                                
Hit http://linux.dropbox.com precise Release.gpg                                                                                                
Ign http://dl.google.com stable/main TranslationIndex                                                                                           
Hit http://packages.ros.org precise Release                                                                                                     
Hit http://extras.ubuntu.com precise Release                                                                                                    
Hit http://archive.canonical.com precise/partner Sources                                                                                        
Hit http://archive.ubuntu.com precise Release                                                                                                   
Hit http://security.ubuntu.com precise-security Release                                                                                         
Hit http://us.archive.ubuntu.com precise Release                                                                                                
Ign http://ppa.launchpad.net precise Release                                                                                                    
Hit http://archive.canonical.com precise/partner i386 Packages                                                                                  
Ign http://archive.canonical.com precise/partner TranslationIndex                                                                               
Hit http://extras.ubuntu.com precise/main Sources                                                                                               
Hit http://archive.ubuntu.com precise-updates Release                                                                                           
Hit http://archive.ubuntu.com precise-proposed Release                                                                                          
Hit http://security.ubuntu.com precise-security/restricted Sources                                                                              
Hit http://us.archive.ubuntu.com precise/main i386 Packages                                                                                     
Hit http://packages.ros.org precise/main Sources                                                                                                
Hit http://ppa.launchpad.net precise Release                                                                                                    
Hit http://linux.dropbox.com precise Release                                                                                                    
Hit http://extras.ubuntu.com precise/main i386 Packages                                                                                         
Ign http://extras.ubuntu.com precise/main TranslationIndex                                                                                      
Hit http://archive.ubuntu.com precise-backports Release                                                                                         
Hit http://archive.ubuntu.com precise/restricted Sources                                                                                        
Hit http://archive.ubuntu.com precise/main Sources                                                                                              
Hit http://archive.ubuntu.com precise/multiverse Sources                                                                                        
Hit http://archive.ubuntu.com precise/universe Sources                                                                                          
Hit http://archive.ubuntu.com precise/main i386 Packages                                                                                        
Hit http://security.ubuntu.com precise-security/main Sources                                                                                    
Hit http://security.ubuntu.com precise-security/multiverse Sources                                                                              
Hit http://security.ubuntu.com precise-security/universe Sources                                                                                
Hit http://security.ubuntu.com precise-security/restricted i386 Packages                                                                        
Hit http://security.ubuntu.com precise-security/main i386 Packages                                                                              
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages                                                                        
Hit http://security.ubuntu.com precise-security/universe i386 Packages                                                                          
Hit http://security.ubuntu.com precise-security/main TranslationIndex                                                                           
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex                                                                     
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex                                                                     
Hit http://ppa.launchpad.net precise Release                                                                                                    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex                                                                       
Hit http://linux.dropbox.com precise/main amd64 Packages                                                                                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                                      
Hit http://security.ubuntu.com precise-security/main Translation-en                                                                             
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                                                                       
Hit http://ppa.launchpad.net precise/main Sources                                                                                               
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                                         
Hit http://ppa.launchpad.net precise/main TranslationIndex                                                                                      
Ign http://dl.google.com stable/main Translation-en_US                                                                                          
Hit http://security.ubuntu.com precise-security/restricted Translation-en                                                                       
Hit http://linux.dropbox.com precise/main i386 Packages                                                                                         
Ign http://dl.google.com stable/main Translation-en                                                                                             
Hit http://ppa.launchpad.net precise/main Sources                                                                                               
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                                      
Hit http://security.ubuntu.com precise-security/universe Translation-en                                                                         
Hit http://ppa.launchpad.net precise/main Translation-en                                                                                        
Ign http://archive.canonical.com precise/partner Translation-en_US                                                                              
Ign http://linux.dropbox.com precise/main TranslationIndex                                                                                   
Ign http://archive.canonical.com precise/partner Translation-en                                                        
Hit http://archive.ubuntu.com precise/restricted i386 Packages                                                         
Hit http://archive.ubuntu.com precise/universe i386 Packages                                                                             
Hit http://archive.ubuntu.com precise/multiverse i386 Packages                                                                            
Hit http://archive.ubuntu.com precise/main TranslationIndex                                                                               
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex                        
Hit http://archive.ubuntu.com precise/restricted TranslationIndex                        
Hit http://archive.ubuntu.com precise/universe TranslationIndex                          
Hit http://archive.ubuntu.com precise-updates/restricted Sources                         
Hit http://archive.ubuntu.com precise-updates/main Sources                                                     
Hit http://archive.ubuntu.com precise-updates/multiverse Sources                                               
Hit http://archive.ubuntu.com precise-updates/universe Sources                                                 
Hit http://archive.ubuntu.com precise-updates/restricted i386 Packages                   
Ign http://extras.ubuntu.com precise/main Translation-en_US                              
Hit http://archive.ubuntu.com precise-updates/main i386 Packages                         
Ign http://extras.ubuntu.com precise/main Translation-en                                 
Hit http://archive.ubuntu.com precise-updates/multiverse i386 Packages                                                                          
Hit http://archive.ubuntu.com precise-updates/universe i386 Packages                                                                            
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex                                                                             
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex                                                                       
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex                                                                       
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex                                                                         
Hit http://archive.ubuntu.com precise-proposed/restricted Sources                                                                               
Hit http://archive.ubuntu.com precise-proposed/main Sources                                                                                     
Hit http://archive.ubuntu.com precise-proposed/multiverse Sources                                                                               
Hit http://archive.ubuntu.com precise-proposed/universe Sources                                                                                 
Err http://ppa.launchpad.net precise/main Sources                                                                                               
  404  Not Found
Hit http://archive.ubuntu.com precise-proposed/restricted i386 Packages                                                                         
Hit http://archive.ubuntu.com precise-proposed/main i386 Packages                                                                               
Hit http://archive.ubuntu.com precise-proposed/multiverse i386 Packages                                                                         
Hit http://archive.ubuntu.com precise-proposed/universe i386 Packages                                                                           
Hit http://archive.ubuntu.com precise-proposed/main TranslationIndex                                                                            
Err http://ppa.launchpad.net precise/main i386 Packages                                                                                         
  404  Not Found
Ign http://linux.dropbox.com precise/main Translation-en_US                                                                                     
Ign http://ppa.launchpad.net precise/main Translation-en_US                                                                                     
Ign http://linux.dropbox.com precise/main Translation-en                                                                                        
Ign http://ppa.launchpad.net precise/main Translation-en                                                                                        
Ign http://ppa.launchpad.net precise/main Translation-en_US                                                                                     
Ign http://ppa.launchpad.net precise/main Translation-en                                                                                        
Hit http://archive.ubuntu.com precise-proposed/multiverse TranslationIndex                                                                      
Hit http://archive.ubuntu.com precise-proposed/restricted TranslationIndex                                                                      
Hit http://archive.ubuntu.com precise-proposed/universe TranslationIndex                                                                        
Hit http://archive.ubuntu.com precise/main Translation-en                                                                                       
Hit http://archive.ubuntu.com precise/multiverse Translation-en                                                                                 
Hit http://archive.ubuntu.com precise/restricted Translation-en                                                                                 
Hit http://archive.ubuntu.com precise/universe Translation-en                                                                                   
Hit http://archive.ubuntu.com precise-updates/main Translation-en                                                                               
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en                                                                         
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en                                                                         
Hit http://archive.ubuntu.com precise-updates/universe Translation-en                                                                           
Hit http://archive.ubuntu.com precise-proposed/main Translation-en                                                                              
Hit http://archive.ubuntu.com precise-proposed/multiverse Translation-en                                                                        
Hit http://archive.ubuntu.com precise-proposed/restricted Translation-en                                                                        
Hit http://archive.ubuntu.com precise-proposed/universe Translation-en                                                                          
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/Release  Unable to find expected entry 'unive/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/Release  Unable to find expected entry 'unive/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/eclipse-team/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/eclipse-team/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.
asaad@VAIO:~$ 


asaad@VAIO:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libopenni-nite-dev : Depends: libopenni-dev (>= 1.5.4.0~precise) but it is not installed
E: Unmet dependencies. Try using -f.
asaad@VAIO:~$ 














```

---

### Post by asaadirfans on 2015-10-12
There's also an error sign showing up in the titlebar(i mean the topmost bar always visible), it says:

"An error occured,Please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was : 'Error: Broken Count >0'. This usually means that your installed packages have unmet dependencies. "

This error occured after i did a partial upgrade via the Software Centre 2 days back. I guess this might be relevant to the current problem.

---

### Post by Bashing-om on 2015-10-12
asaadirfans; Welp;

We back up and fix:
> 
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/Release](http://us.archive.ubuntu.com/ubuntu/dists/precise/Release)  Unable to find expected entry 'unive/binary-i386/Pack

Line 48 in /etc/apt/sources.list is not only malformed .. it is a duplicate entry of line(s) 5/14 . Remove this entry (48) from the list.

These are no longer supported for precise; per:
[http://ppa.launchpad.net/eclipse-team/ppa/ubuntu/dists/](http://ppa.launchpad.net/eclipse-team/ppa/ubuntu/dists/)
> 
W: Failed to fetch [http://ppa.launchpad.net/eclipse-team/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/eclipse-team/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/eclipse-team/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/eclipse-team/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

and need to be removed too !

Now what results:
```

sudo apt-get update

``` when 'update' runs clean we go back to work.

[INDENT][INDENT]making progress, slowly
[/INDENT][/INDENT]

---

### Post by asaadirfans on 2015-10-12
After removing line 48 from sources.list (and checking for any other duplicate entries) the output of sudo apt-get update is:

```


asaad@VAIO:/etc/apt$ sudo apt-get update
Hit http://dl.google.com stable Release.gpg
Hit http://dl.google.com stable Release                                                                                                         
Hit http://archive.canonical.com precise Release.gpg                                                                                            
Hit http://dl.google.com stable/main i386 Packages                                                                                              
Hit http://extras.ubuntu.com precise Release.gpg                                                                                                
Hit http://linux.dropbox.com precise Release.gpg                                                                                                
Hit http://archive.ubuntu.com precise Release.gpg                                                                                               
Hit http://archive.ubuntu.com precise-updates Release.gpg                                                                                       
Hit http://archive.ubuntu.com precise-proposed Release.gpg                                                                                      
Hit http://archive.ubuntu.com precise-backports Release.gpg                                                                                     
Ign http://ppa.launchpad.net precise Release.gpg                                                                                                
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                
Hit http://security.ubuntu.com precise-security Release.gpg                                                                                     
Hit http://us.archive.ubuntu.com precise Release.gpg                                                                                            
Hit http://archive.canonical.com precise Release                                                                                                
Ign http://dl.google.com stable/main TranslationIndex                                                                                           
Hit http://extras.ubuntu.com precise Release                                                                                                    
Hit http://archive.canonical.com precise/partner Sources                                                                                        
Ign http://ppa.launchpad.net precise Release                                                                                                    
Hit http://archive.ubuntu.com precise Release                                                                                                   
Hit http://us.archive.ubuntu.com precise Release                                                                                                
Hit http://security.ubuntu.com precise-security Release                                                                                         
Hit http://archive.canonical.com precise/partner i386 Packages                                                                                  
Hit http://archive.canonical.com precise/partner TranslationIndex                                                                               
Hit http://extras.ubuntu.com precise/main Sources                                                                                               
Hit http://linux.dropbox.com precise Release                                                                                                    
Hit http://ppa.launchpad.net precise Release                                                                                                    
Hit http://archive.ubuntu.com precise-updates Release                                                                                           
Hit http://archive.ubuntu.com precise-proposed Release                                                                                          
Hit http://us.archive.ubuntu.com precise/main i386 Packages                                                                                     
Hit http://security.ubuntu.com precise-security/restricted Sources                                                                              
Hit http://archive.canonical.com precise/partner Translation-en                                                                                 
Hit http://extras.ubuntu.com precise/main i386 Packages                                                                                         
Ign http://extras.ubuntu.com precise/main TranslationIndex                                                                                      
Hit http://ppa.launchpad.net precise Release                                                                                                    
Hit http://archive.ubuntu.com precise-backports Release                                                                                         
Hit http://archive.ubuntu.com precise/restricted Sources                                                                                        
Hit http://archive.ubuntu.com precise/main Sources                                                                                              
Hit http://archive.ubuntu.com precise/multiverse Sources                                                                                        
Hit http://archive.ubuntu.com precise/universe Sources                                                                                          
Hit http://archive.ubuntu.com precise/main i386 Packages                                                                             
Hit http://security.ubuntu.com precise-security/main Sources                                                                         
Hit http://security.ubuntu.com precise-security/multiverse Sources                                                                              
Hit http://security.ubuntu.com precise-security/universe Sources                                                                                
Hit http://security.ubuntu.com precise-security/restricted i386 Packages                                                             
Hit http://security.ubuntu.com precise-security/main i386 Packages                                                                   
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages                                                             
Hit http://security.ubuntu.com precise-security/universe i386 Packages                                                               
Hit http://security.ubuntu.com precise-security/main TranslationIndex                                                                
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex                                                          
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex                                                          
Hit http://linux.dropbox.com precise/main amd64 Packages                                                                                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                                      
Hit http://archive.ubuntu.com precise/restricted i386 Packages                                                                                  
Hit http://archive.ubuntu.com precise/universe i386 Packages                                                                                    
Hit http://archive.ubuntu.com precise/multiverse i386 Packages                                                                                  
Hit http://archive.ubuntu.com precise/main TranslationIndex                                                                                     
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex                                                                               
Hit http://archive.ubuntu.com precise/restricted TranslationIndex                                                                               
Hit http://archive.ubuntu.com precise/universe TranslationIndex                                                                                 
Hit http://archive.ubuntu.com precise-updates/restricted Sources                                                                                
Hit http://archive.ubuntu.com precise-updates/main Sources                                                                                      
Hit http://security.ubuntu.com precise-security/universe TranslationIndex                                                                       
Ign http://dl.google.com stable/main Translation-en_US                                                                                          
Ign http://dl.google.com stable/main Translation-en                                                                                             
Hit http://ppa.launchpad.net precise/main Sources                                                                                               
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                             
Hit http://ppa.launchpad.net precise/main TranslationIndex                                                    
Hit http://archive.ubuntu.com precise-updates/multiverse Sources                                              
Hit http://archive.ubuntu.com precise-updates/universe Sources                                                
Hit http://archive.ubuntu.com precise-updates/restricted i386 Packages                                                              
Hit http://archive.ubuntu.com precise-updates/main i386 Packages                                                                    
Hit http://archive.ubuntu.com precise-updates/multiverse i386 Packages                                                              
Hit http://archive.ubuntu.com precise-updates/universe i386 Packages                                                                
Hit http://security.ubuntu.com precise-security/main Translation-en                                                                 
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                                     
Hit http://linux.dropbox.com precise/main i386 Packages                                                       
Hit http://ppa.launchpad.net precise/main Sources                                                                                               
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                                      
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex                                                                             
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex                                                                       
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex                                                                       
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex                                                                         
Hit http://archive.ubuntu.com precise-proposed/restricted Sources                                                                               
Hit http://archive.ubuntu.com precise-proposed/main Sources                                                                                     
Hit http://archive.ubuntu.com precise-proposed/multiverse Sources                                                                               
Hit http://archive.ubuntu.com precise-proposed/universe Sources                                                                       
Hit http://archive.ubuntu.com precise-proposed/restricted i386 Packages                                                               
Hit http://security.ubuntu.com precise-security/restricted Translation-en                                                             
Hit http://archive.ubuntu.com precise-proposed/main i386 Packages                                                                     
Ign http://linux.dropbox.com precise/main TranslationIndex                                                                            
Hit http://archive.ubuntu.com precise-proposed/multiverse i386 Packages                                                               
Hit http://archive.ubuntu.com precise-proposed/universe i386 Packages                                                               
Hit http://archive.ubuntu.com precise-proposed/main TranslationIndex                                                                
Hit http://archive.ubuntu.com precise-proposed/multiverse TranslationIndex                                    
Hit http://archive.ubuntu.com precise-proposed/restricted TranslationIndex                                                           
Hit http://security.ubuntu.com precise-security/universe Translation-en                                                              
Hit http://ppa.launchpad.net precise/main Translation-en                                                                            
Hit http://archive.ubuntu.com precise-proposed/universe TranslationIndex                                       
Hit http://archive.ubuntu.com precise/main Translation-en                                                      
Hit http://archive.ubuntu.com precise/multiverse Translation-en                                                
Hit http://archive.ubuntu.com precise/restricted Translation-en                                                
Hit http://archive.ubuntu.com precise/universe Translation-en                                                  
Hit http://archive.ubuntu.com precise-updates/main Translation-en                                              
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en                  
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en                  
Hit http://archive.ubuntu.com precise-updates/universe Translation-en                                          
Hit http://archive.ubuntu.com precise-proposed/main Translation-en                                             
Hit http://archive.ubuntu.com precise-proposed/multiverse Translation-en                 
Hit http://archive.ubuntu.com precise-proposed/restricted Translation-en                 
Hit http://archive.ubuntu.com precise-proposed/universe Translation-en                   
Ign http://extras.ubuntu.com precise/main Translation-en_US                               
Ign http://extras.ubuntu.com precise/main Translation-en                                        
Err http://ppa.launchpad.net precise/main Sources                                               
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages                  
  404  Not Found
Ign http://ppa.launchpad.net precise/main Translation-en_US                                                                                     
Ign http://linux.dropbox.com precise/main Translation-en_US                                                                                     
Ign http://ppa.launchpad.net precise/main Translation-en                                                                                        
Ign http://ppa.launchpad.net precise/main Translation-en_US                                                                                     
Ign http://linux.dropbox.com precise/main Translation-en                                                                                        
Ign http://ppa.launchpad.net precise/main Translation-en                                                                                        
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/Release  Unable to find expected entry 'unive/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/Release  Unable to find expected entry 'unive/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/eclipse-team/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/eclipse-team/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.
asaad@VAIO:/etc/apt$ 




```

---

### Post by Bashing-om on 2015-10-12
asaadirfans; And

Still remaining to remove:
```

sudo rm /etc/apt/sources.list.d/eclipse-team-ppa-precise.list
sudo rm /etc/apt/sources.list.d/eclipse-team-ppa-precise.list.save

``` as the PPA is no longer supported.

Once 'update' is running clean .. we continue to address the dependency issue.

[INDENT]progress made slowly
[/INDENT]

---

### Post by asaadirfans on 2015-10-13
The sudo apt-get update works fine now. I simply followed this answer [http://askubuntu.com/questions/120621/how-to-fix-duplicate-sources-list-entry](http://askubuntu.com/questions/120621/how-to-fix-duplicate-sources-list-entry) and sudo apt-get update works alright now:

```


asaad@VAIO:~$ sudo apt-get update
Hit http://ppa.launchpad.net precise Release.gpg
Hit http://ppa.launchpad.net precise Release.gpg                      
Hit http://ppa.launchpad.net precise Release.gpg                      
Hit http://security.ubuntu.com precise-security Release.gpg           
Hit http://security.ubuntu.com precise-security Release               
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://archive.ubuntu.com precise Release.gpg                     
Hit http://archive.ubuntu.com precise-updates Release.gpg             
Hit http://archive.ubuntu.com precise-backports Release.gpg           
Hit http://linux.dropbox.com precise Release.gpg                      
Hit http://security.ubuntu.com precise-security/main i386 Packages    
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex 
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://ppa.launchpad.net precise Release                          
Hit http://ppa.launchpad.net precise Release                          
Hit http://security.ubuntu.com precise-security/main Translation-en   
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://archive.ubuntu.com precise Release                         
Hit http://archive.ubuntu.com precise-updates Release                 
Hit http://ppa.launchpad.net precise Release                          
Hit http://dl.google.com stable Release.gpg                           
Hit http://security.ubuntu.com precise-security/universe Translation-en
Hit http://linux.dropbox.com precise Release                          
Hit http://archive.ubuntu.com precise-backports Release               
Hit http://dl.google.com stable Release                               
Hit http://ppa.launchpad.net precise/main Sources                     
Hit http://ppa.launchpad.net precise/main i386 Packages               
Ign http://ppa.launchpad.net precise/main TranslationIndex            
Hit http://ppa.launchpad.net precise/main Sources                     
Hit http://ppa.launchpad.net precise/main i386 Packages               
Hit http://ppa.launchpad.net precise/main TranslationIndex            
Hit http://dl.google.com stable/main i386 Packages                    
Hit http://ppa.launchpad.net precise/main Sources                     
Hit http://ppa.launchpad.net precise/main i386 Packages               
Ign http://ppa.launchpad.net precise/main TranslationIndex            
Hit http://archive.ubuntu.com precise/main i386 Packages              
Hit http://archive.ubuntu.com precise/universe i386 Packages          
Hit http://archive.ubuntu.com precise/restricted i386 Packages        
Hit http://archive.ubuntu.com precise/multiverse i386 Packages        
Hit http://archive.ubuntu.com precise/main TranslationIndex           
Hit http://linux.dropbox.com precise/main amd64 Packages              
Ign http://dl.google.com stable/main TranslationIndex                 
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex     
Hit http://archive.ubuntu.com precise/restricted TranslationIndex     
Hit http://archive.ubuntu.com precise/universe TranslationIndex       
Hit http://archive.ubuntu.com precise-updates/universe i386 Packages  
Hit http://archive.ubuntu.com precise-updates/main i386 Packages      
Hit http://ppa.launchpad.net precise/main Translation-en              
Hit http://archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex   
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://archive.ubuntu.com precise-backports/main i386 Packages    
Hit http://archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://linux.dropbox.com precise/main i386 Packages               
Hit http://archive.ubuntu.com precise-backports/main TranslationIndex 
Hit http://archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://archive.ubuntu.com precise/main Translation-en             
Hit http://archive.ubuntu.com precise/multiverse Translation-en       
Hit http://archive.ubuntu.com precise/restricted Translation-en       
Hit http://archive.ubuntu.com precise/universe Translation-en         
Hit http://archive.ubuntu.com precise-updates/main Translation-en     
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en
Ign http://linux.dropbox.com precise/main TranslationIndex            
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://archive.ubuntu.com precise-updates/universe Translation-en                                           
Hit http://archive.ubuntu.com precise-backports/main Translation-en                                             
Hit http://archive.ubuntu.com precise-backports/multiverse Translation-en                                       
Hit http://archive.ubuntu.com precise-backports/restricted Translation-en                                       
Hit http://archive.ubuntu.com precise-backports/universe Translation-en                                               
Ign http://dl.google.com stable/main Translation-en_US                                                               
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://dl.google.com stable/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://linux.dropbox.com precise/main Translation-en_US                                                                                    
Ign http://linux.dropbox.com precise/main Translation-en                                                                                       
Reading package lists... Done                                                                                                                  
asaad@VAIO:~$ 


```

The output of sudo apt-get upgrade however is not as good:

```

asaad@VAIO:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libopenni-nite-dev : Depends: libopenni-dev (>= 1.5.4.0~precise) but it is not installed
E: Unmet dependencies. Try using -f.
asaad@VAIO:~$ 

```

Whats next now?

---

### Post by Bashing-om on 2015-10-13
asaadirfans; Hey;

Look'n good ... so far so good ..

OK, do you need these development packages ?
see:
```

apt-cache show libopenni-dev

```
I think we really want to delete "libopenni-nite-dev" from the system.
> 
sysop@1404mini:~$ apt-cache show libopenni-nite-dev
N: Unable to locate package libopenni-nite-dev
E: No packages found
sysop@1404mini:~$ 
 as this package is not standard and was installed from that PPA.
If the package manager does not have a handle on it .. may be tricky to remove .

[INDENT][INDENT]we got to make the package manager happy
[/INDENT][/INDENT]

---

### Post by asaadirfans on 2015-10-13
I need (1) OpenNI & (2) NITE.
```

asaad@VAIO:~$ apt-cache show libopenni-dev
Package: libopenni-dev
Source: openni
Priority: optional
Section: libdevel
Installed-Size: 1170
Maintainer: Debian Multimedia Maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
Architecture: i386
Version: 1.5.4.0-4+precise1
Suggests: openni-doc
Depends: libopenni0 (= 1.5.4.0-4+precise1)
Filename: pool/main/o/openni/libopenni-dev_1.5.4.0-4+precise1_i386.deb
Size: 179400
SHA256: 1b719f072bc7b44227f2a487311960ba8ed3b57ee5f05e2178ec3fc52d2393a1
SHA1: 457fa4ee96e6c8a5fb02c9c3b2d22dc4dd62c32c
MD5sum: d32d8dc39778752c7125276c6e008fd6
Description-en: headers for OpenNI 'Natural Interaction' frameworks
 OpenNI is a framework for getting data to support 'Natural Interaction',
 i.e. skeleton tracking, gesture tracking, and similar ways of getting data
 from humans. OpenNI provides the interface for physical devices and for
 middleware components. The API enables modules to be registered in the OpenNI
 framework, which then produce sensory data. OpenNI also allows selection of
 different hardware and middleware modules.


asaad@VAIO:~$ 


```

---

### Post by Bashing-om on 2015-10-13
asaadirfans; ..

I do not know what " (1) OpenNI & (2) NITE. " are. These terms give no results to find out what they are in our software repository,

Let's try and make the package manager happy:
```

sudo apt-get install libopenni-dev

```
Then perhaps - IF it installs - we can now remove " libopenni-nite-dev" . Then work toward installing the app desired.

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by asaadirfans on 2015-10-13
I was talking about these packages :

[http://wiki.ros.org/openni_launch](http://wiki.ros.org/openni_launch)

because i want to use kinect.


```

asaad@VAIO:~$ sudo apt-get install libopenni-dev
[sudo] password for asaad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libopenni-dev : Depends: libopenni0 (= 1.5.4.0-4+precise1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
asaad@VAIO:~$ 









```

---

### Post by Bashing-om on 2015-10-13
asaadirfans; Well ..

I know nothing of your end goal here. To install the PPA application ? OR a similar app that 'might' be in our software repository ?

In either event, we must make the package manager happy.

Going on down the chain.
Try:
```

sudo apt-get install libopenni0

```

I can believe we are not at the end as:
> 
sysop@1404mini:~$ apt-cache depends libopenni0
libopenni0
  Depends: libc6
  Depends: libgcc1
  Depends: libjpeg8
  Depends: libstdc++6
  Depends: libtinyxml2.6.2
  Depends: libusb-1.0-0
  PreDepends: dpkg
    dpkg:i386
 |Recommends: libopenni-sensor-pointclouds0
  Recommends: libopenni-sensor-primesense0
  Conflicts: <openni-dev>
  Conflicts: <openni-dev:i386>
  Conflicts: libopenni0:i386
sysop@1404mini:~$

says there may be other dependency and/or issues and conflicts.

However, we work with what is .. and then once to the bottom, work our way back up to the top .

[INDENT][INDENT]just putting things to right
[/INDENT][/INDENT]

---

### Post by asaadirfans on 2015-10-14
```

asaad@VAIO:~$ sudo apt-get install libopenni0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libopenni-nite-dev : Depends: libopenni-dev (>= 1.5.4.0~precise) but it is not going to be installed
 libopenni0 : Recommends: libopenni-sensor-primesense0 but it is not going to be installed
              Conflicts: openni-dev but 1.5.2.23-iatsl2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
asaad@VAIO:~$ 

```

---

### Post by Bashing-om on 2015-10-14
asaadirfans; Oh Boy ...

OK, Let's take a look and see what we can do:
```

apt-cache policy openni-dev

```

Maybe as I 
[INDENT][INDENT]just do not have a good feeling
[/INDENT][/INDENT]

---

### Post by asaadirfans on 2015-10-14
```

asaad@VAIO:~$ apt-cache policy openni-dev
openni-dev:
  Installed: 1.5.2.23-iatsl2
  Candidate: 1.5.2.23-iatsl2
  Version table:
 *** 1.5.2.23-iatsl2 0
        500 http://ppa.launchpad.net/yani/iatsl/ubuntu/ precise/main i386 Packages
        100 /var/lib/dpkg/status
     1.3.2.1-4+precise2 0
        500 http://packages.ros.org/ros/ubuntu/ precise/main i386 Packages
        500 http://ppa.launchpad.net/v-launchpad-jochen-sprickerhof-de/pcl/ubuntu/ precise/main i386 Packages
asaad@VAIO:~$ 


```

---

### Post by Bashing-om on 2015-10-14
asaadirfans; Ouch ... 

I read that as a conflict with that package in 3 ( as in three !) PPA's .
Lemme do some peeking and poking about see what I can come up with to move us along. Get my mind right and ->

[INDENT][INDENT][INDENT]see what we can do
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-10-14
asaadirfans; Welp

I am alook'n and yikes !
I think you have taken care of this no-longer-supported PPA, thus no longer an issue ?
[http://ppa.launchpad.net/eclipse-team/ppa/ubuntu](http://ppa.launchpad.net/eclipse-team/ppa/ubuntu) 

I continue to stew about how to isolate the dependency to which PPA is holding " openni-dev " ,

If you do :
```

apt-cache show openni-dev

```
Looking to see what the proper version is, I expect a null return -> indicating it is not a ubuntu thing .
------------
Doodling :
> 
#1 Errors were encountered while processing: libopenni-nite-dev
apt-cache policy libopenni-nite-dev -> Installed: 1.3.1.5~precise --- from => 500 [http://packages.ros.org/ros/ubuntu/](http://packages.ros.org/ros/ubuntu/) precise/main i386 Packages
 sudo apt-get remove libopenni-nite-dev -> Errors were encountered while processing: libopenni-nite-dev
libopenni-nite-dev : Depends: libopenni-dev (>= 1.5.4.0~precise)
libopenni-dev : Depends: libopenni0 (= 1.5.4.0-4+precise1)
libopenni-nite-dev : Depends: libopenni-dev (>= 1.5.4.0~precise)
apt-cache policy openni-dev -> 1.3.2.1-4+precise2 0 -- from [http://packages.ros.org/ros/](http://packages.ros.org/ros/) && from ; [http://ppa.launchpad.net/v-launchpad-jochen-sprickerhof-de/pcl/ubuntu](http://ppa.launchpad.net/v-launchpad-jochen-sprickerhof-de/pcl/ubuntu)  ///****HUH**** ???

Edit *****
apt-cache policy libopenni0 ->Installed: (none)
  Version table:
     1.5.4.0-4+precise1 0
        500 [http://packages.ros.org/ros/ubuntu/](http://packages.ros.org/ros/ubuntu/) precise/main i386 Packages
        500 [http://ppa.launchpad.net/v-launchpad-jochen-sprickerhof-de/pcl/ubuntu/](http://ppa.launchpad.net/v-launchpad-jochen-sprickerhof-de/pcl/ubuntu/) precise/main i386 Packages
        100 /var/lib/dpkg/status
**********


--------------

So what have we now for
```

apt-cache policy libopenni0

``` and let's see if we have more than "packages.ros.org/ros/" at play here .

I want to hold this thought - to be done at a later time :
- I did mess this up before time -
[code]
sudo add-apt-repository "deb http://packages.ros.org/ros/ubuntu precise main"
sudo add-apt-repository -r "deb http://packages.ros.org/ros/ubuntu precise main"

As I seek to learn where we should focus our attention,

[INDENT][INDENT]version control,
[INDENT][INDENT][INDENT]version control
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by asaadirfans on 2015-10-14
```

sudo asaad@VAIO:~$ sudo apt-cache show openni-dev
[sudo] password for asaad: 
Package: openni-dev
Source: openni
Priority: optional
Section: libs
Installed-Size: 13823
Maintainer: Jochen Sprickerhof <launchpad@jochen.sprickerhof.de>
Architecture: i386
Version: 1.5.2.23-iatsl2
Depends: freeglut3, libc6 (>= 2.15), libgcc1 (>= 1:4.1.1), libgl1-mesa-glx | libgl1, libstdc++6 (>= 4.6), libusb-1.0-0 (>= 2:1.0.9~rc3)
Filename: pool/main/o/openni/openni-dev_1.5.2.23-iatsl2_i386.deb
Size: 2199272
MD5sum: da5c8de3d2521db89d25d36c0f67a907
SHA1: 7f3810ef560b13e1da6dbd96b009b248ee7ef045
SHA256: 667ce10fee7a9773afb145063cc335e9bb192f67ee167b111e7864ed6bfbd7a5
Description-en: OpenNI Framework - libraries
 The OpenNI Framework provides the interface for physical devices and for
 middleware components. The API enables modules to be registered in the OpenNI
 framework and used to produce sensory data. Selecting the hardware or
 middleware module is easy and flexible.


Package: openni-dev
Source: opennidev
Priority: optional
Section: libs
Installed-Size: 13269
Maintainer: Jochen Sprickerhof <launchpad@jochen.sprickerhof.de>
Architecture: i386
Version: 1.3.2.1-4+precise2
Depends: freeglut3, libc6 (>= 2.15), libgcc1 (>= 1:4.1.1), libgl1-mesa-glx | libgl1, libstdc++6 (>= 4.6), libusb-1.0-0 (>= 2:1.0.9~rc3)
Filename: pool/main/o/opennidev/openni-dev_1.3.2.1-4+precise2_i386.deb
Size: 2075608
SHA256: 56d7a32179ab2278a616d8b619bff1650b7213f59d0d11c0b5c6d52fe7d651f3
SHA1: 7e022ddf744b9dbd5003ca5728bca23e2793d066
MD5sum: 5e7c779ad0cf67bb970977efeda453fa
Description-en: OpenNI Framework - libraries
 The OpenNI Framework provides the interface for physical devices and for
 middleware components. The API enables modules to be registered in the OpenNI
 framework and used to produce sensory data. Selecting the hardware or
 middleware module is easy and flexible.



```
```

asaad@VAIO:~$ apt-cache policy libopenni0
libopenni0:
  Installed: (none)
  Candidate: 1.5.4.0-4+precise1
  Version table:
     1.5.4.0-4+precise1 0
        500 http://packages.ros.org/ros/ubuntu/ precise/main i386 Packages
        500 http://ppa.launchpad.net/v-launchpad-jochen-sprickerhof-de/pcl/ubuntu/ precise/main i386 Packages
        100 /var/lib/dpkg/status
asaad@VAIO:~$ 



```

---

### Post by Bashing-om on 2015-10-15
asaadirfans; Hummm ...

Surprising that last - in a good kind of way ... just presently I do not know what to make of it ..
Or what to recommend - at this time - to resolve the dependency issue.

Going to do some homework on these PPAs, and think about it .

As the system is tracking " openni-dev : maybe the same is true of "libopenni0" .

What returns :
```

grep -B3 -A10 libopenni0 /var/lib/dpkg/status

```

As I seek to learn
[INDENT][INDENT]where to focus our attention
[/INDENT][/INDENT]

---

### Post by asaadirfans on 2015-10-15
```

asaad@VAIO:~$ grep -B3 -A10 libopenni0 /var/lib/dpkg/status
Source: openni-sensor-primesense
Version: 5.1.0.41-2+precise1
Config-Version: 5.1.0.41-2+precise1
Depends: libc6 (>= 2.11), libgcc1 (>= 1:4.1.1), libjpeg8 (>= 8c), libopenni0, libstdc++6 (>= 4.1.1), openni-utils
Conffiles:
 /etc/openni/GlobalDefaults.ini 0725e8c9faffd8eae862588bcc72c6fe
 /etc/modprobe.d/libopenni-sensor-primesense0.conf cb76908c9bd8a413c7a8df157c68d55a
Description: Microsoft Kinect sensor modules for the OpenNI framework
 OpenNI is a framework for getting data to support 'Natural Interaction',
 i.e. skeleton tracking, gesture tracking, and similar ways of getting data
 from humans. This package provides modules for OpenNI that get the data from
 the Kinect camera for processing with the OpenNI Middleware, like PrimeSense
 NITE.
Homepage: http://www.openni.org
--
 in the &#8220;console-setup&#8221; package.
Original-Maintainer: Console utilities maintainers <pkg-kbd-devel@lists.alioth.debian.org>


Package: libopenni0
Status: deinstall ok config-files
Priority: optional
Section: libs
Installed-Size: 1137
Maintainer: Debian Multimedia Maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
Architecture: i386
Source: openni
Version: 1.5.4.0-4+precise1
Config-Version: 1.5.4.0-4+precise1
Depends: libc6 (>= 2.15), libgcc1 (>= 1:4.1.1), libjpeg8 (>= 8c), libstdc++6 (>= 4.1.1), libtinyxml2.6.2, libusb-1.0-0 (>= 2:1.0.9~rc3)
asaad@VAIO:~$ 



```

---

### Post by Bashing-om on 2015-10-16
asaadirfans: Well, a thought ;

We try and re-install libopenni0 and see if the package manager will direct our attention to the PPAs that are giving us such fits :
```

sudo apt-get install --reinstall libopenni0

```

[INDENT][INDENT]see if a tale gets told
[/INDENT][/INDENT]

---

