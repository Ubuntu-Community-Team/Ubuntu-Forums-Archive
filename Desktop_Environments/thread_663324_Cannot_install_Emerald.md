---
title: "Cannot install Emerald"
date: 2008-01-10
forum: Desktop Environments
---

### Post by modalrooster on 2008-01-10
I am trying to install Emerald.   When I attempt to get the Emerald package through Synaptic, I receive the following message:

emerald:
 Depends: libemeraldengine0 but it is not going to be installed
 Depends: libwnck18 (>=2.15.90) but it is not installable

When i try to install libemeraldengine0, I get:

libemeraldengine0:
 Depends: libwnck18 (>=2.15.90) but it is not installable
 Depends: emerald but it is not going to be installed

When I try to install libwnck18, I get:

libwnck18:

Package libwnck18 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

I have libwnck22 installed.

Can anyone please help me?

---

### Post by PeterJS on 2008-01-10
What version of ubuntu are you running? Have you updated your apt index recently? You might try that. I just looked at libemeraldengine0 on my system and it depends on libwnck22.

---

### Post by Auximenes on 2008-01-10
I run 7.10 (gutsy) and I face the same problem:

libemerald0 depends on libwnck18, while I have lilbwnck22 installed.

What is meant by updating apt index?

---

### Post by PeterJS on 2008-01-10
Running either:
```

sudo apt-get update

```
or reload synaptic
apt index isn't the technical name of the package listing, but makes it's descriptive of what I was trying to explain, or I guess not.

---

### Post by oldos2er on 2008-01-10
"sudo aptitude update" will freshen your index.

 It sounds like you need to enable one or more repositories. Go to System, Administration, Software Sources, and make sure all the boxes on the first page are checked.

---

### Post by Auximenes on 2008-01-10
> **PeterJS said:**
> Running either:
```

sudo apt-get update

```
or reload synaptic
apt index isn't the technical name of the package listing, but makes it's descriptive of what I was trying to explain, or I guess not.

I thought it was apt-get update, but I wanted to be sure :)

Still, I've run update, and emerald still depends on libemeraldengine0 which still depends on the obsolete libwnck18 :(

Futher help please

---

### Post by PeterJS on 2008-01-10
Did you install compiz or beryl in 7.04 from a third party repository and then upgrade to 7.10?

---

### Post by shrinux on 2008-02-06
[COLOR="Red"]**I have the same problem :(**[/COLOR]

```
$ sudo apt-get install emerald
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
  emerald: Depends: libemeraldengine0 but it is not going to be installed
           Depends: libwnck18 (>= 2.15.90) but it is not installable
E: Broken packages
```


**[COLOR="Red"]when I update the source list, that what i get:[/COLOR]**

```
W: GPG error: http://archive.ubuntu.com gutsy-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

```


**[COLOR="Red"]And this is my source list:[/COLOR]**

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

##Universe

deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## Multiverse

deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Backports

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Canonical Partner Repository

# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
# deb http://packages.medibuntu.org/ gutsy free non-free

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt gutsy main

deb http://archive.canonical.com/ubuntu gutsy partner

# deb http://www.getautomatix.com/apt gutsy main

# deb http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
#AUTOMATIX REPOS END
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

Ubuntu 7.10

---

### Post by Detonate on 2008-02-28
Did anyone ever come up with the solution to this problem?  I'm still unable to install emerald, I get the following error message.

Depends: libemeraldengine0 but it is not going to be installed
 Depends: libwnck18 (>=2.15.90) but it is not installable

---

### Post by dolphinbrain on 2008-03-03
I had the same problem and it took me while to find out that 

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

in the /etc/apt/sources.list is most likely causing the trouble (possibly also other references tothe feisty release).

Once, you have installed the necessary packages from the feisty release, try commenting them again and reinstall emerald. This worked for me.

---

### Post by Detonate on 2008-03-03
Thank you, that turned out to be the problem.  After commenting out those lines, I was able to install emerald and get my compiz-fusion working again.

---

