---
title: "Cannot install empathy .. Help !!"
date: 2009-05-27
forum: General Help
---

### Post by brijith on 2009-05-27
Hai All, 
I am using Ubuntu Hardy. When I tried to install empathy following the link 
[[COLOR="Blue"]howto-setup-voice-chat-with-google-talk-user-using-empathy.html[/COLOR]]("http://www.ubuntugeek.com/howto-setup-voice-chat-with-google-talk-user-using-empathy.html#more-1065") I ended up in errors given below

```
 
brijith@ubuntu201:~$ sudo apt-get install empathy telepathy-gabble telepathy-mission-control telepathy-stream-engine telepathy-butterfly python-msn
[sudo] password for brijith: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
telepathy-gabble is already the newest version.
telepathy-mission-control is already the newest version.
telepathy-stream-engine is already the newest version.
telepathy-butterfly is already the newest version.
python-msn is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  empathy: Depends: libebook1.2-9 (>= 2.22.3) but 2.22.1-0ubuntu2 is to be installed
           Depends: libedataserver1.2-9 (>= 2.22.3) but 2.22.1-0ubuntu2 is to be installed
           Depends: libempathy-gtk15 (>= 2.23.91) but it is not going to be installed
E: Broken packages
brijith@ubuntu201:~$

```

The following are the repositories I enabled in the source list

```
deb http://ppa.launchpad.net/telepathy/ppa/ubuntu hardy main
deb-src http://ppa.launchpad.net/telepathy/ppa/ubuntu hardy main
deb http://archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse
```


please help me



[COLOR="Sienna"]**Thanks**[/COLOR]

---

### Post by _Purple_ on 2009-05-27
Try to run these commands
```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by brijith on 2009-05-27
> **_Purple_ said:**
> Try to run these commands
```
sudo dpkg --configure -a
sudo apt-get -f install
```



I got the following


 ```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libswing-layout-java libempathy14 libfreemarker-java javahelp2 libempathy-common subversion liblucene2-java libnb-ide8-java openjdk-6-jdk libini4j-java
  libnb-java1-java libnb-platform7-devel-java libnb-apisupport1-java libswingworker-java libdb4.5-java libjtidy-java libnb-platform7-java
  libxml-commons-resolver1.1-java libempathy-gtk-common libappframework-java libnb-javaparser-java libnb-svnclientadapter-java libbeansbinding-java
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libempathy-common libempathy-gtk-common libempathy14
The following packages will be REMOVED:
  empathy
The following NEW packages will be installed:
  libempathy-common libempathy-gtk-common libempathy14
0 upgraded, 3 newly installed, [COLOR=Red]**1 to remove**[/COLOR] and 0 not upgraded.
1 not fully installed or removed.
Need to get 841kB of archives.
After this operation, 3224kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libempathy-common libempathy-gtk-common libempathy14
Install these packages without verification [y/N]? y
Get:1 http://ppa.launchpad.net hardy/main libempathy-common 2.24.1-1ubuntu1~ppa8.04+1 [446kB]
Get:2 http://ppa.launchpad.net hardy/main libempathy-gtk-common 2.24.1-1ubuntu1~ppa8.04+1 [308kB]                                                           
Get:3 http://ppa.launchpad.net hardy/main libempathy14 2.24.1-1ubuntu1~ppa8.04+1 [87.2kB]                                                                   
Fetched 841kB in 29s (28.2kB/s)                                                                                                                             
(Reading database ... 150598 files and directories currently installed.)
[COLOR=Red]**Removing empathy ...**[/COLOR]
Selecting previously deselected package libempathy-common.
(Reading database ... 150545 files and directories currently installed.)
Unpacking libempathy-common (from .../libempathy-common_2.24.1-1ubuntu1~ppa8.04+1_all.deb) ...
Selecting previously deselected package libempathy-gtk-common.
Unpacking libempathy-gtk-common (from .../libempathy-gtk-common_2.24.1-1ubuntu1~ppa8.04+1_all.deb) ...
Selecting previously deselected package libempathy14.
Unpacking libempathy14 (from .../libempathy14_2.24.1-1ubuntu1~ppa8.04+1_i386.deb) ...
Setting up libempathy-common (2.24.1-1ubuntu1~ppa8.04+1) ...
Setting up libempathy-gtk-common (2.24.1-1ubuntu1~ppa8.04+1) ...

Setting up libempathy14 (2.24.1-1ubuntu1~ppa8.04+1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

Again When I tried
```
sudo apt-get install empathy telepathy-gabble telepathy-mission-control telepathy-stream-engine telepathy-butterfly python-msn
```

I got 

```
brijith@ubuntu201:~/Desktop$ sudo apt-get install empathy telepathy-gabble telepathy-mission-control telepathy-stream-engine telepathy-butterfly python-msn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
telepathy-gabble is already the newest version.
telepathy-mission-control is already the newest version.
telepathy-stream-engine is already the newest version.
telepathy-butterfly is already the newest version.
python-msn is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  empathy: Depends: libebook1.2-9 (>= 2.22.3) but 2.22.1-0ubuntu2 is to be installed
           Depends: libedataserver1.2-9 (>= 2.22.3) but 2.22.1-0ubuntu2 is to be installed
           Depends: libempathy-gtk15 (>= 2.23.91) but it is not going to be installed
E: Broken packages

```

---

### Post by _Purple_ on 2009-05-27
If you run it again, what does it show?
```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by brijith on 2009-05-27
> **_Purple_ said:**
> If you run it again, what does it show?
```
sudo dpkg --configure -a
sudo apt-get -f install
```

```
brijith@ubuntu201:~/Desktop$ sudo sudo dpkg --configure -a
brijith@ubuntu201:~/Desktop$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libswing-layout-java libempathy14 libfreemarker-java javahelp2 libempathy-common subversion liblucene2-java libnb-ide8-java openjdk-6-jdk libini4j-java
  libnb-java1-java libnb-platform7-devel-java libnb-apisupport1-java libswingworker-java libdb4.5-java libjtidy-java libnb-platform7-java
  libxml-commons-resolver1.1-java libempathy-gtk-common libappframework-java libnb-javaparser-java libnb-svnclientadapter-java libbeansbinding-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
brijith@ubuntu201:~/Desktop$
```

---

### Post by _Purple_ on 2009-05-27
Now try this
```
sudo apt-get update
sudo apt-get autoremove
sudo apt-get install empathy telepathy-gabble telepathy-mission-control telepathy-stream-engine telepathy-butterfly python-msn

```

---

### Post by brijith on 2009-05-27
> **_Purple_ said:**
> Now try this
```
sudo apt-get update
sudo apt-get autoremove
sudo apt-get install empathy telepathy-gabble telepathy-mission-control telepathy-stream-engine telepathy-butterfly python-msn

```

Nothing Happened. I lost my Subverion client

See the code below 

```
brijith@ubuntu201:~/Desktop$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libswing-layout-java libempathy14 libfreemarker-java javahelp2 libempathy-common subversion liblucene2-java libnb-ide8-java openjdk-6-jdk libini4j-java
  libnb-java1-java libnb-platform7-devel-java libnb-apisupport1-java libswingworker-java libdb4.5-java libjtidy-java libnb-platform7-java
  libxml-commons-resolver1.1-java libempathy-gtk-common libappframework-java libnb-javaparser-java libnb-svnclientadapter-java libbeansbinding-java
The following packages will be REMOVED:
  javahelp2 libappframework-java libbeansbinding-java libdb4.5-java libempathy-common libempathy-gtk-common libempathy14 libfreemarker-java libini4j-java
  libjtidy-java liblucene2-java libnb-apisupport1-java libnb-ide8-java libnb-java1-java libnb-javaparser-java libnb-platform7-devel-java
  libnb-platform7-java libnb-svnclientadapter-java libswing-layout-java libswingworker-java libxml-commons-resolver1.1-java openjdk-6-jdk subversion
0 upgraded, 0 newly installed, 23 to remove and 0 not upgraded.
After this operation, 114MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 150802 files and directories currently installed.)
Removing libnb-apisupport1-java ...
Removing libnb-java1-java ...
Removing libnb-ide8-java ...
Removing libnb-platform7-java ...
Removing libnb-platform7-devel-java ...
Removing javahelp2 ...
Removing libappframework-java ...
Removing libbeansbinding-java ...
Removing liblucene2-java ...
Removing libdb4.5-java ...
Removing libempathy14 ...
Removing libempathy-common ...
Removing libempathy-gtk-common ...
Removing libfreemarker-java ...
Removing libini4j-java ...
Removing libjtidy-java ...
Removing libnb-javaparser-java ...
Removing libnb-svnclientadapter-java ...
Removing libswing-layout-java ...
Removing libswingworker-java ...
Removing libxml-commons-resolver1.1-java ...
Removing openjdk-6-jdk ...
Removing subversion ...
brijith@ubuntu201:~/Desktop$ sudo sudo dpkg --configure -a
brijith@ubuntu201:~/Desktop$ 
brijith@ubuntu201:~/Desktop$ sudo apt-get install empathy telepathy-gabble telepathy-mission-control telepathy-stream-engine telepathy-butterfly python-msn
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
brijith@ubuntu201:~/Desktop$ sudo apt-get install empathy telepathy-gabble telepathy-mission-control telepathy-stream-engine telepathy-butterfly python-msn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
telepathy-gabble is already the newest version.
telepathy-mission-control is already the newest version.
telepathy-stream-engine is already the newest version.
telepathy-butterfly is already the newest version.
python-msn is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  empathy: Depends: libebook1.2-9 (>= 2.22.3) but 2.22.1-0ubuntu2 is to be installed
           Depends: libedataserver1.2-9 (>= 2.22.3) but 2.22.1-0ubuntu2 is to be installed
           Depends: libempathy-gtk15 (>= 2.23.91) but it is not going to be installed
E: Broken packages

```

---

### Post by _Purple_ on 2009-05-27
Did you have add/remove or synaptic one while installing? Looks like only the package empathy is giving error. What happens if you run this
```
sudo apt-get install empathy
```

---

### Post by brijith on 2009-05-27
> **_Purple_ said:**
> Did you have add/remove or synaptic one while installing? Looks like only the package empathy is giving error. What happens if you run this
```
sudo apt-get install empathy
```

here is it

```

brijith@ubuntu201:~$ sudo apt-get install empathy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  empathy: Depends: libebook1.2-9 (>= 2.22.3) but 2.22.1-0ubuntu2 is to be installed
           Depends: libedataserver1.2-9 (>= 2.22.3) but 2.22.1-0ubuntu2 is to be installed
           Depends: libempathy-gtk15 (>= 2.23.91) but it is not going to be installed
E: Broken packages
brijith@ubuntu201:~$ 

```

---

### Post by _Purple_ on 2009-05-27
Add these two line to yous /etc/apt/sources.list
```
deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

```

Then run
```
sudo apt-get update
sudo apt-get install empathy
```

---

### Post by brijith on 2009-05-27
> **_Purple_ said:**
> Add these two line to yous /etc/apt/sources.list
```
deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

```

Then run
```
sudo apt-get update
sudo apt-get install empathy
```


Again the same thing happens

```


brijith@ubuntu201:~/Desktop$ sudo apt-get update
Ign http://192.168.1.65 hardy Release.gpg
Ign http://192.168.1.65 hardy/main Translation-en_IN
Ign http://192.168.1.65 hardy/restricted Translation-en_IN                                
Ign http://192.168.1.65 hardy/universe Translation-en_IN                                  
Ign http://192.168.1.65 hardy/multiverse Translation-en_IN                                 
Get:1 http://192.168.1.65 hardy Release [2203B]                                            
Ign http://192.168.1.65 hardy/main Packages                                
Ign http://192.168.1.65 hardy/restricted Packages
Ign http://192.168.1.65 hardy/universe Packages
Ign http://192.168.1.65 hardy/multiverse Packages                                          
Hit http://192.168.1.65 hardy/main Packages                                                
Hit http://192.168.1.65 hardy/restricted Packages
Hit http://192.168.1.65 hardy/universe Packages
Hit http://192.168.1.65 hardy/multiverse Packages
Get:2 http://archive.ubuntu.com hardy-backports Release.gpg [189B]
Ign http://ppa.launchpad.net hardy Release.gpg                       
Ign http://archive.ubuntu.com hardy-backports/main Translation-en_IN 
Ign http://ppa.launchpad.net hardy/main Translation-en_IN            
Ign http://archive.ubuntu.com hardy-backports/restricted Translation-en_IN
Get:3 http://ppa.launchpad.net hardy Release [27.6kB]                
Ign http://archive.ubuntu.com hardy-backports/universe Translation-en_IN
Ign http://archive.ubuntu.com hardy-backports/multiverse Translation-en_IN
Ign http://ppa.launchpad.net hardy/main Packages
Hit http://archive.ubuntu.com hardy Release.gpg
Ign http://ppa.launchpad.net hardy/main Sources
Ign http://archive.ubuntu.com hardy/main Translation-en_IN
Hit http://ppa.launchpad.net hardy/main Packages                     
Ign http://archive.ubuntu.com hardy/universe Translation-en_IN       
Hit http://ppa.launchpad.net hardy/main Sources                      
Ign http://archive.ubuntu.com hardy/restricted Translation-en_IN     
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_IN
Get:4 http://archive.ubuntu.com hardy-backports Release [51.2kB]
Hit http://archive.ubuntu.com hardy Release     
Get:5 http://archive.ubuntu.com hardy-backports/main Packages [112kB]
Get:6 http://archive.ubuntu.com hardy-backports/restricted Packages [14B]                                                                                   
Get:7 http://archive.ubuntu.com hardy-backports/universe Packages [110kB]                                                                                   
Get:8 http://archive.ubuntu.com hardy-backports/multiverse Packages [14.6kB]                                                                                
Get:9 http://archive.ubuntu.com hardy-backports/main Sources [16.3kB]                                                                                       
Get:10 http://archive.ubuntu.com hardy-backports/restricted Sources [14B]                                                                                   
Get:11 http://archive.ubuntu.com hardy-backports/universe Sources [25.5kB]                                                                                  
Get:12 http://archive.ubuntu.com hardy-backports/multiverse Sources [4064B]                                                                                 
Hit http://archive.ubuntu.com hardy/main Packages                                                                                                           
Hit http://archive.ubuntu.com hardy/universe Packages                                                                                                       
Hit http://archive.ubuntu.com hardy/restricted Packages                                                                                                     
Hit http://archive.ubuntu.com hardy/multiverse Packages                                                                                                     
Fetched 335kB in 18s (18.0kB/s)                                                                                                                             
Reading package lists... Done
**brijith@ubuntu201:~/Desktop$** sudo apt-get install empathy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  empathy: Depends: libebook1.2-9 (>= 2.22.3) but 2.22.1-0ubuntu2 is to be installed
           Depends: libedataserver1.2-9 (>= 2.22.3) but 2.22.1-0ubuntu2 is to be installed
           Depends: libempathy-gtk15 (>= 2.23.91) but it is not going to be installed


```

---

### Post by _Purple_ on 2009-05-27
Does this work?
```
sudo apt-get install telepathy-gnome 
```

---

### Post by brijith on 2009-05-27
> **_Purple_ said:**
> Does this work?
```
sudo apt-get install telepathy-gnome 
```


No ..

```

**brijith@ubuntu201:~/Desktop$** sudo apt-get install telepathy-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  telepathy-gnome: Depends: empathy but it is not going to be installed
E: Broken packages


```

---

### Post by _Purple_ on 2009-05-27
Can you post the content of /etc/apt/sources.list?

---

### Post by brijith on 2009-05-27
> **_Purple_ said:**
> Can you post the content of /etc/apt/sources.list?





```

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://in.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://192.168.1.65/ubunturepose hardy main restricted universe multiverse
deb http://ppa.launchpad.net/telepathy/ppa/ubuntu hardy main
deb-src http://ppa.launchpad.net/telepathy/ppa/ubuntu hardy main
deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb file:///home/brijith/Desktop/repo/ /
deb http://archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse

```

---

### Post by _Purple_ on 2009-05-27
Please add the following two lines to your sources.list :
```
deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
```

Then run 
```
sudo apt-get update
```
Then try to install the packages again.

---

### Post by brijith on 2009-05-28
> **_Purple_ said:**
> Please add the following two lines to your sources.list :
```
deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
```

Then run 
```
sudo apt-get update
```
Then try to install the packages again.

YESS!!!!

At last I got it installed. 

Thanks. Buddy...


Now, can you help me to configure it. When I give the required fields and tried to connect it fails (*[COLOR="Blue"]please see the attachment[/COLOR]*). I am accessing net through proxy. I cann't find proxy setting anywhere in empathy so that I can give my proxy ip and port no .

Please help!

---

### Post by _Purple_ on 2009-05-28
I think empathy does not supoport proxy but I could be wrong. May be someone else can confirm.

---

### Post by brijith on 2009-05-28
> **_Purple_ said:**
> I think empathy does not supoport proxy but I could be wrong. May be someone else can confirm.

I think you are right. I Googled for the proxy support of Empathy. It seems that there no such facility available. Hope they will introduce it very soon. 
I checked Empathy connecting directly to internet. It is working well...

**[COLOR="DarkOrange"]anyway Thanks a lot for your replies[/COLOR]** 


:D:D:D:D:D:D:D:D

---

### Post by _Purple_ on 2009-05-28
You are welcome. :)

---

### Post by brijith on 2009-05-31
Hai Friends,
I got my probelm solved. Usually I sued to mark the thread solved by choosing it from thread tools at the top of the page. But now that option is not there in thread tools. How can I mark a thread Solved....

**[COLOR="Sienna"]Thanks[/COLOR]**

---

### Post by _Purple_ on 2009-05-31
You can click on the "Edit Tags" button and add a tag "Solved" to this thread or edit the thread title and add [SOLVED] in front of it. :)

---

### Post by brijith on 2009-06-01
> **_Purple_ said:**
> You can click on the "Edit Tags" button and add a tag "Solved" to this thread or edit the thread title and add [SOLVED] in front of it. :)


Is it that simple? 
**[COLOR="DarkOrange"]Thanks[/COLOR]**

---

