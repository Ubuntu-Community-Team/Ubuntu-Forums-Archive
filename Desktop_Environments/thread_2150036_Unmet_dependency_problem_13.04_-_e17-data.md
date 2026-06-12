---
title: "Unmet dependency problem 13.04 - e17-data"
date: 2013-05-30
forum: Desktop Environments
---

### Post by Drone4four on 2013-05-30
I am trying to install the latest e17 point release from the ppas.  

The first few hits on Google for how to install e17 ubuntu for raring guided me to add the ppa:hannes-janetzek/enlightenment-svn repos.  I realized that this was a big mistake after about an hour of troubleshooting broken dependency errors and the like.  I figured out how to remove e17 and that repo.  But now I can&#8217;t install the e17 that I was using that I initially installed from ubuntu&#8217;s main repos.  Here is my error message:

```
gnull@raring ~  $ sudo apt-get install e17
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 e17 : Depends: e17-data (= 0.16.999.70492-2) but 201305250913-15455~raring1 is to be installed
E: Unable to correct problems, you have held broken packages.
gnull@raring ~  $ sudo apt-get install e17-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
e17-data is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
gnull@raring ~ $ 
```

What is this error trying to say and how do I install e17?  

Only after troubleshooting hannes-janetzek&#8217;s svn repo did I actually read a very crucial message on his page: > If you are look for a stable ppa please use [https://launchpad.net/~efl/+archive/trunk](https://launchpad.net/~efl/+archive/trunk) instead!  So what I would like to do is install that, but before I get there I want to resolve my problem with e17 in the ubuntu main repository just to be safe.

EDIT: btw:

I used a combination of these commands to clean my system of e17 svn packages:

```
sudo add-apt-repository --remove ppa:hannes-janetzek/enlightenment-svn
sudo apt-get autoremove -f
sudo apt-get dist-upgrade -f
sudo apt-get --fix-missing install
sudo apt-get autoclean
sudo apt-get autoclean
sudo apt-get clean
```

Some of them helped, others seemed to do nothing.  One tip I found on Google that really helped was to load up synaptic, click status in the bottom left and then click broken depdendneces in the top left.  I selected the 3 efl based packages and marked them for removal and clicked apply.  That&#8217;s how I go to where I am now.

---

### Post by Frogs Hair on 2013-05-30
If you  added the PPA after the repository version that is cause of the problem because the PPA packages are much newer . You will probably have to install the synaptic package manager and  clean it up manually . I have used the PPA in the past but not on 13.04 . The e17 trunk is also different than the repository version so don't mix those either.

---

### Post by LTMvP61nizine on 2013-05-30
Had the same type of problem a while back and everything I typed in the terminal would not work for me at all. I didn't have Synaptic Package Manager at the time so I had do a fresh install. I learned my lesson and never wanted to install the E17 desktop ever again. The most annoying thing is the error message that keeps popping up.

---

### Post by Drone4four on 2013-05-31
> **Frogs Hair said:**
> If you  added the PPA after the repository version that is cause of the problem because the PPA packages are much newer . You will probably have to install the synaptic package manager and  clean it up manually . I have used the PPA in the past but not on 13.04 . The e17 trunk is also different than the repository version so don't mix those either.

Thanks.  This worked.  I feel silly because I should have come up with the solution myself.  It was as simple as doing to e17-data the same thing I did earlier to the 3 broken efl packages in synaptic. 

I successfully added and installed the latest point release of e17 after adding the ppa with this command:

```
sudo add-apt-repository ppa:efl/trunk
```

I am writing this forum post in my brand spanking new e17 wm.

However I can't seem to install terminology.  Here is the input and output of some relevant commands:

```
gnull@raring ~  $ sudo apt-get install terminology 
[sudo] password for gnull: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 terminology : Depends: libelementary but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
gnull@raring ~  $ sudo apt-get install libelementary
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 libelementary : Depends: libelementary-data (= 1.7.7-1ppa1~raring) but 201305300536-7906~raring1 is to be installed
E: Unable to correct problems, you have held broken packages.
gnull@raring ~  $ sudo apt-get install libelementary
libelementary         libelementary-bin     libelementary-data    libelementary-dbg     libelementary-dev     libelementary-svn-09  
gnull@raring ~  $ sudo apt-get install libelementary-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libelementary-data is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
```

What is apt telling me and how would I go about installing terminology?

(I tried using synaptic too, but when I mark it for installation it gets sent to the broken packages tab.)

---

### Post by Frogs Hair on 2013-05-31
sudo apt-get install terminologyThe above package is not in the 13.04 repository by default so I can't advise.

---

