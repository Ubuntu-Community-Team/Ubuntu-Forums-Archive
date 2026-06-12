---
title: "[SOLVED] Lost gimp and Unable to install it"
date: 2009-01-06
forum: General Help
---

### Post by aschwerin.moses on 2009-01-06
I dont know what i have done but i lost GIMP. I tried to install it but it gives me this error

```
gimp:
 Depends: libgimp2.0 but it is not going to be installed
 Depends: libgimp2.0 but it is not going to be installed
  Depends: libgtk2.0-0 (>=2.14.1) but 2.12.9-4ubuntu3 is to be installed
  Depends: libpango1.0-0 (>=1.21.6) but 1.20.5-0ubuntu1 is to be installed
 Depends: libpoppler-glib3  but it is not installable


```

i tried aptitude, even that did not work.. please help..

---

### Post by aschwerin.moses on 2009-01-06
btw... i have Hardy

---

### Post by p_quarles on 2009-01-06
Moved to General Help. The Cafe is meant for off-topic stuff.

---

### Post by Zeroberry on 2009-01-06
Did you try installing it with Synaptic Package Manager?

---

### Post by aschwerin.moses on 2009-01-06
> **Zeroberry said:**
> Did you try installing it with Synaptic Package Manager?

Yes.. the error i got is from Synaptic

---

### Post by p_quarles on 2009-01-06
> **aschwerin.moses said:**
> Yes.. the error i got is from Synaptic
What's the output of 
```
sudo apt-get install libpoppler-glib3
```
?

---

### Post by aschwerin.moses on 2009-01-06
> **p_quarles said:**
> What's the output of 
```
sudo apt-get install libpoppler-glib3
```
?
Package libpoppler-glib3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libpoppler-glib3 has no installation candidate

---

### Post by p_quarles on 2009-01-06
> **aschwerin.moses said:**
> Package libpoppler-glib3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libpoppler-glib3 has no installation candidate
Okay, you said you already tried it, but give us the output anyway:
```
sudo aptitude install gimp
```

And post the contents of your /etc/apt/sources.list file.

---

### Post by CoffeyW on 2009-01-06
Is it completely missing or is there some response when you type gimp into the terminal?

---

### Post by igknighted on 2009-01-06
Can you post the output of 'cat /etc/apt/sources.list'?

---

### Post by aschwerin.moses on 2009-01-07
> **igknighted said:**
> Can you post the output of 'cat /etc/apt/sources.list'?

> **p_quarles said:**
> Okay, you said you already tried it, but give us the output anyway:
```
sudo aptitude install gimp
```

And post the contents of your /etc/apt/sources.list file.

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb http://in.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://in.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy universe
deb http://in.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://in.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb http://repository.cairo-dock.org/ubuntu hardy cairo-dock
deb http://ppa.launchpad.net/gilir/ubuntu gutsy main universe #Gilir's screenlets packages and some stuff you shouldn't use
deb http://us.archive.ubuntu.com/ubuntu hardy universe
deb http://us.archive.ubuntu.com/ubuntu hardy multiverse
deb http://ubuntu.org.ua/ getdeb/

deb http://ppa.launchpad.net/team-xbmc-hardy/ubuntu hardy main
deb-src http://ppa.launchpad.net/team-xbmc-hardy/ubuntu hardy main
deb http://ubuntu.org.ua/ getdeb/

```

---

### Post by aschwerin.moses on 2009-01-07
> **CoffeyW said:**
> Is it completely missing or is there some response when you type gimp into the terminal?

nothing.. it says gimp is not installed

---

### Post by p_quarles on 2009-01-07
> **aschwerin.moses said:**
> nothing.. it says gimp is not installed
Can you please answer the other question in my last post?

---

### Post by aschwerin.moses on 2009-01-07
> **p_quarles said:**
> Can you please answer the other question in my last post?

I did .. i thought **igknighted** and you asked me the same question.. anyways.. this is the list

```
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb http://repository.cairo-dock.org/ubuntu hardy cairo-dock
deb http://ppa.launchpad.net/gilir/ubuntu gutsy main universe #Gilir's screenlets packages and some stuff you shouldn't use
deb http://us.archive.ubuntu.com/ubuntu hardy universe
deb http://us.archive.ubuntu.com/ubuntu hardy multiverse
deb http://ubuntu.org.ua/ getdeb/

deb http://ppa.launchpad.net/team-xbmc-hardy/ubuntu hardy main
deb-src http://ppa.launchpad.net/team-xbmc-hardy/ubuntu hardy main
deb http://ubuntu.org.ua/ getdeb/
```

---

### Post by igknighted on 2009-01-07
You've got a lot of unofficial repo's there, could be messing up your dependencies.

---

### Post by p_quarles on 2009-01-07
> **aschwerin.moses said:**
> I did .. i thought **igknighted** and you asked me the same question.. anyways.. this is the list

```
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb http://repository.cairo-dock.org/ubuntu hardy cairo-dock
deb http://ppa.launchpad.net/gilir/ubuntu gutsy main universe #Gilir's screenlets packages and some stuff you shouldn't use
deb http://us.archive.ubuntu.com/ubuntu hardy universe
deb http://us.archive.ubuntu.com/ubuntu hardy multiverse
deb http://ubuntu.org.ua/ getdeb/

deb http://ppa.launchpad.net/team-xbmc-hardy/ubuntu hardy main
deb-src http://ppa.launchpad.net/team-xbmc-hardy/ubuntu hardy main
deb http://ubuntu.org.ua/ getdeb/
```
We did, and you answered that one. I asked another question, though, which hasn't yet been answered.

---

### Post by aschwerin.moses on 2009-01-07
> We did, and you answered that one. I asked another question, though, which hasn't yet been answered.

oh.. im really sorry :confused:

```
sudo aptitude install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:
  gimp libgimp2.0 
The following NEW packages will be automatically installed:
  libbabl-0.0-0 libgegl-0.0-0 
The following packages have been kept back:
  audacity 
The following NEW packages will be installed:
  libbabl-0.0-0 libgegl-0.0-0 
0 packages upgraded, 4 newly installed, 0 to remove and 1 not upgraded.
Need to get 5440kB/5799kB of archives. After unpacking 18.1MB will be used.
The following packages have unmet dependencies:
  gimp: Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-4ubuntu3 is installed.
        Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is installed.
        Depends: libpoppler-glib3 which is a virtual package.
  libgimp2.0: Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-4ubuntu3 is installed.
              Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
gimp [Not Installed]
libgimp2.0 [Not Installed]

Score is -9872

Accept this solution? [Y/n/q/?] y
The following packages have been kept back:
  audacity 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done   
```

---

### Post by aschwerin.moses on 2009-01-07
it was fine till day before yest.. i did not install anything infact.. just lost it all of a sudden

sorry.. that was for **igknighted**

---

### Post by p_quarles on 2009-01-07
> **aschwerin.moses said:**
> oh.. im really sorry :confused:

```
sudo aptitude install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:
  gimp libgimp2.0 
The following NEW packages will be automatically installed:
  libbabl-0.0-0 libgegl-0.0-0 
The following packages have been kept back:
  audacity 
The following NEW packages will be installed:
  libbabl-0.0-0 libgegl-0.0-0 
0 packages upgraded, 4 newly installed, 0 to remove and 1 not upgraded.
Need to get 5440kB/5799kB of archives. After unpacking 18.1MB will be used.
The following packages have unmet dependencies:
  gimp: Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-4ubuntu3 is installed.
        Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is installed.
        Depends: libpoppler-glib3 which is a virtual package.
  libgimp2.0: Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-4ubuntu3 is installed.
              Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
gimp [Not Installed]
libgimp2.0 [Not Installed]

Score is -9872

Accept this solution? [Y/n/q/?] y
The following packages have been kept back:
  audacity 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done   
```
Okay, reject the first solution by typing "n", and see what else it offers.

---

### Post by aschwerin.moses on 2009-01-07
> Okay, reject the first solution by typing "n", and see what else it offers.

```
Accept this solution? [Y/n/q/?] n
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
libgimp2.0 [2.4.6-1~getdeb1 (<NULL>)]

Keep the following packages at their current version:
gimp [Not Installed]

Downgrade the following packages:
gimp-data [2.6.3-1~getdeb1 (<NULL>, now) -> 2.4.6-1~getdeb1 (<NULL>)]

Score is -9881

Accept this solution? [Y/n/q/?]
```

---

### Post by p_quarles on 2009-01-07
> **aschwerin.moses said:**
> ```
Accept this solution? [Y/n/q/?] n
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
libgimp2.0 [2.4.6-1~getdeb1 (<NULL>)]

Keep the following packages at their current version:
gimp [Not Installed]

Downgrade the following packages:
gimp-data [2.6.3-1~getdeb1 (<NULL>, now) -> 2.4.6-1~getdeb1 (<NULL>)]

Score is -9881

Accept this solution? [Y/n/q/?]
```
Well, that sheds some light on the situation. Try this:
```
gksudo gedit /etc/apt/sources.list
```
Comment out the getdeb line by placing a # at the beginning.

Then run:
```
sudo apt-get update; sudo apt-get upgrade; sudo apt-get install gimp
```
and let us know what happens.

---

### Post by aschwerin.moses on 2009-01-07
> Well, that sheds some light on the situation. Try this:
```
gksudo gedit /etc/apt/sources.list
```
Comment out the getdeb line by placing a # at the beginning.

Then run:
```
sudo apt-get update; sudo apt-get upgrade; sudo apt-get install gimp
```
and let us know what happens.

... you meant the **deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/** line right, yes did put a # before it

and tried to install gimp... got this

```
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
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
  gimp: Depends: gimp-data (< 2.4.5-z) but 2.6.3-1~getdeb1 is to be installed
E: Broken packages

```

---

### Post by igknighted on 2009-01-07
There were 2 getdeb lines... did you comment them both out?

---

### Post by aschwerin.moses on 2009-01-07
> **igknighted said:**
> There were 2 getdeb lines... did you comment them both out?

yes... removed the other one infact

---

### Post by igknighted on 2009-01-07
> **aschwerin.moses said:**
> yes... removed the other one infact

Can you run 'sudo apt-get -f install' to clear everything out, then try to install gimp again

---

### Post by aschwerin.moses on 2009-01-07
> Can you run 'sudo apt-get -f install' to clear everything out, then try to install gimp again


same error... even after that

---

### Post by p_quarles on 2009-01-07
> **aschwerin.moses said:**
> same error... even after that
Run Synaptic and try "Fix broken packages."

---

### Post by aschwerin.moses on 2009-01-07
> **p_quarles said:**
> Run Synaptic and try "Fix broken packages."

same.. i get the same error in synaptic and in terminal

```
The following packages have unmet dependencies:
  gimp: Depends: gimp-data (< 2.4.5-z) but 2.6.3-1~getdeb1 is to be installed
E: Broken packages

```

---

### Post by igknighted on 2009-01-07
> **aschwerin.moses said:**
> same.. i get the same error in synaptic and in terminal

```
The following packages have unmet dependencies:
  gimp: Depends: gimp-data (< 2.4.5-z) but 2.6.3-1~getdeb1 is to be installed
E: Broken packages

```

Try running the command 'sudo apt-get clean', the 'sudo apt-get update' then try to install again via aptitude

---

### Post by aschwerin.moses on 2009-01-07
> **igknighted said:**
> Try running the command 'sudo apt-get clean', the 'sudo apt-get update' then try to install again via aptitude

DUDE'S.................. claps claps.. SOLVED

thank you.. both of you.. Thank You :)

---

### Post by nickstephens on 2009-01-09
Another thank you from myself! This thread helped me fix my problem also. Problem appears to be an updated libgimp2.0 which does not work with the previous version of gimp. Solution was to uninstal gimp and anything that was associated using synaptic and then installing gimp again using sudo adt-get in stall gimp. This has only been an issue with the gutsy machine I am running.

---

