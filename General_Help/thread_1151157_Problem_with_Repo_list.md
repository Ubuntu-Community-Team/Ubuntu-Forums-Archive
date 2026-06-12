---
title: "Problem with Repo list?"
date: 2009-05-06
forum: General Help
---

### Post by Psychopump on 2009-05-06
Hi all,

I wanted to try out KDE on my Jaunty (Gnome) system and ran into some issues.

Whenever I try to update synaptic I get this message:

```
Method gave invalid 400 URI Failure messageMethod gave invalid 400 URI Failure message
```

I have tried different servers in my software sources tool, including letting it search for the best one.

here are the contents of my /etc/apt/sources.list:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.                                    

deb http://giano.com.dist.unige.it/ubuntu/ jaunty main restricted
deb-src http://giano.com.dist.unige.it/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb http://giano.com.dist.unige.it/ubuntu/ jaunty-updates main restricted
deb-src http://giano.com.dist.unige.it/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in     
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.                                                                   
deb http://giano.com.dist.unige.it/ubuntu/ jaunty universe
deb-src http://giano.com.dist.unige.it/ubuntu/ jaunty universe
deb http://giano.com.dist.unige.it/ubuntu/ jaunty-updates universe
deb-src http://giano.com.dist.unige.it/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in      
## multiverse WILL NOT receive any review or updates from the Ubuntu        
## security team.                                                           
deb http://giano.com.dist.unige.it/ubuntu/ jaunty multiverse
deb-src http://giano.com.dist.unige.it/ubuntu/ jaunty multiverse
deb http://giano.com.dist.unige.it/ubuntu/ jaunty-updates multiverse
deb-src http://giano.com.dist.unige.it/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.                                                           
## N.B. software from this repository may not have been tested as        
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.                               
deb http://giano.com.dist.unige.it/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://giano.com.dist.unige.it/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is 
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.                                                                
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://giano.com.dist.unige.it/ubuntu/ jaunty-security main restricted
deb-src http://giano.com.dist.unige.it/ubuntu/ jaunty-security main restricted
deb http://giano.com.dist.unige.it/ubuntu/ jaunty-security universe
deb-src http://giano.com.dist.unige.it/ubuntu/ jaunty-security universe
deb http://giano.com.dist.unige.it/ubuntu/ jaunty-security multiverse
deb-src http://giano.com.dist.unige.it/ubuntu/ jaunty-security multiverse
```

Can anyone PLEASE help me sort this out?

---

### Post by Psychopump on 2009-05-06
sorry to bump so soon, but I cannot install ANYTHING via synaptic now...
please help?

---

### Post by Psychopump on 2009-05-07
Please, guys...I am totally disabled here.
Even updares are impossible now.

Can anyone help?

---

### Post by Psychopump on 2009-05-07
PLEASE is there no-one who can help me?
I really don't want to go down the re-install path...

---

### Post by taurus on 2009-05-07
Close down synaptic.  Then, open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo apt-get update
```

---

### Post by Psychopump on 2009-05-07
> **taurus said:**
> Close down synaptic.  Then, open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo apt-get update
```

Thanks for your reply, but I did this already.
I get the same error message.

Synaptic, apt-get and reloading sources all get me the same message:

```
Method gave invalid 400 URI Failure messageMethod gave invalid 400 URI Failure message
```

---

### Post by Psychopump on 2009-05-11
Never mind.
I reinstalled.
:(

---

### Post by emix101 on 2009-05-14
Hi there,
I'm newb....
I also had the same problem like you...
but I did this and it works for me

Just go to Software Sources>Third Party Software and uncheck everything in the list...
then close and reload....

It seem there is some of the list have some contradict with the main support update...and create problem with the connection...):P

---

