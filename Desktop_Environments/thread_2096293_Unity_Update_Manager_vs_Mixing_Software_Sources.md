---
title: "Unity Update Manager vs Mixing Software Sources"
date: 2012-12-19
forum: Desktop Environments
---

### Post by ArlieS on 2012-12-19
I'm looking for specifics on the interaction of the "update manager" I see as part of Unity with /etc/apt/preferences and /etc/apt/sources.list

Here's the problem: I'm running ubuntu 12.04.1 but I wanted to install the pidgin-sipe version from 12.10, and simply downloading and installing it manually didn't work, and furthermore messed up my pidgin installation. 

I followed the instructions at [http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html) modifying URLs etc. to convert from debian to ubuntu, and then did something like "sudo apt-get install pidgin-sipe/quantal". 

This worked, but now I have update manager claiming I have 280 updates selected. It also occasionally produces a pop-up, saying "not all updates can be installed" and asking whether I want to run a partial  upgrade. (E.g. I found that pop-up on my screen this morning.)

This is making me nervous. Do I need to abandon "update manager" entirely and stick with "sudo apt-get update" followed by "sudo apt-get upgrade"? 

And does that recipe in fact work correctly? I have had situations where apt-get upgrade claims there are packages held back, which "update manager" manages to sort out, suggesting that there's an additional layer here, and using apt-get as my only interface will eventually create problems for me. Perhaps "update manager" wraps some other tool, with extra storage (and configuration?) somewhere, that uses the apt "hold" mechanism in strange ways? (Would that be aptitude? I seem to remember "interesting" results with aptitude back when I was using Debian rather than Ubuntu.)

---

### Post by grahammechanical on 2012-12-19
First of all **never** accept that offer to run a partial upgrade. Just cancel and update as normal.

It is my understanding that Update Manager or Software Updater, as it is called in 12.04, is just a User Interface to apt-get. The same is true of Synaptic Package Manager which used to be installed by default in Ubuntu and which many of us still use.

You have a situation where you have a mix of precise and quantal repositories. Update Manager notices this and assumes that you are wanting to upgrade to quantal. Update Manager is assessing the differences between the listed Precise packages and those listed for Quantal and sees the need for an update of packages.

Do you want to upgrade to Quantal? An upgrade will change all your repositories to the Quantal repositories. And you will have 12.10 instead of 12.04.

I tested Quantal while it was being developed and I am testing Raring Ringtail now. I made the change by putting in a fresh install of 12.10 and then I changed the repositories from the quantal ones to the raring ones and then I updated. I did this even before there was a Raring ISO image to download. It works.

My advice to you would be to use the terminal from now on.

```
sudo apt-get update
```

will update the sources lists. The files that keep a record of what packages you have installed and where they came from and how long we have had them. It is a comparison between what we have listed as being on our machines and what is listed on the Ubuntu servers that give the list of what to update.

```
sudo apt-get upgrade
```

will download and install the updates. It will not upgrade to Quantal. The code to do that is

```
sudo apt-get dist-upgrade
```

You may get messages that you will have to ignore.

Regards.

---

### Post by ArlieS on 2012-12-20
Thank you. That's what I expected, but I wanted to be sure.  I'll probably stick with precise until the next LTS, unless cherry picking updates I want becomes a problem.

---

### Post by ArlieS on 2012-12-20
> **grahammechanical said:**
> First of all **never** accept that offer to run a partial upgrade. Just cancel and update as normal.

My advice to you would be to use the terminal from now on.

```
sudo apt-get update
```will update the sources lists. The files that keep a record of what packages you have installed and where they came from and how long we have had them. It is a comparison between what we have listed as being on our machines and what is listed on the Ubuntu servers that give the list of what to update.

```
sudo apt-get upgrade
```will download and install the updates. It will not upgrade to Quantal. The code to do that is

```
sudo apt-get dist-upgrade
```You may get messages that you will have to ignore.

Regards.


It looks like something's not working as expected. Here's what I got on my screen from "sudo apt-get upgrade"

> 
...
280 upgraded, 0 newly installed, 0 to remove and 189 not upgraded.
Need to get 129 MB of archives.
After this operation, 2,270 kB of additional disk space will be used.
Do you want to continue [Y/n]? I responded with n.

Here are the files I believe to be relevant:

```

~$ cat /etc/apt/sources.list
# /etc/apt/sources.list

# Main distribution - precise pangolin aka 12.04.1 LTS
deb http://archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse

# 12.10 distribution, for an extremely limited set of purposes
deb http://archive.ubuntu.com/ubuntu/ quantal main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ quantal-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ quantal-updates main restricted universe multiverse

``````

$ cat /etc/apt/preferences
Package: *
Pin: release a=precise
Pin-Priority: 700

Package: *
Pin: release a=quantal
Pin-Priority: 650

``````

$ ls -l /etc/apt/preferences.d/
total 0

```

---

