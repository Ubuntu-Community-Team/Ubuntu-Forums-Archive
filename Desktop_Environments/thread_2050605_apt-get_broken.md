---
title: "apt-get broken"
date: 2012-08-31
forum: Desktop Environments
---

### Post by bobzxr on 2012-08-31
Hi all


After an unsuccessful upgrade to 12.04.1 (bad internet connection), now I cannot install anything from any repository, because unmet dependencies, which cannot be resolved, and neither can upgrade anything. For example:

```
$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.4 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```


Apt-get update runs without any errors, but there is nothing to be upgraded (although by now I am sure I would have more than 100 updates to install)

```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
apt-get clean does not help.

This one also does not help:
```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```

/etc/lsb_release:
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
```

It says I have 12.04.1 but the upgrade was unsuccessful and I only have 12.04.

Any ideas on how could I fix this?

---

### Post by drmrgd on 2012-08-31
What happens if you run:

```
sudo dpkg --configure -a
```

If that doesn't work, we can try:

```
sudo apt-get -f dist-upgrade
```

---

### Post by bobzxr on 2012-08-31
> **drmrgd said:**
> What happens if you run:

```
sudo dpkg --configure -a
```

If that doesn't work, we can try:

```
sudo apt-get -f dist-upgrade
```

First one did nothing, the second one the same thing as mentioned in the first post:

```

$ sudo apt-get -f dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by drmrgd on 2012-08-31
Hmmm...this is suggesting that the upgrade did complete successfully, unless the package cache is corrupt.  Maybe try running:

```
sudo apt-get clean
```

Then attempt the upgrade again.

---

### Post by bobzxr on 2012-08-31
> **drmrgd said:**
> Hmmm...this is suggesting that the upgrade did complete successfully, unless the package cache is corrupt.  Maybe try running:

```
sudo apt-get clean
```

Then attempt the upgrade again.

I also tried this before posting the topic, but it does not help.

---

### Post by ectechnologies on 2012-08-31
I think what's wrong is your dpkg (debian package) is corrupt. If you log off, above the space where you type in your password there is a cog wheel. Select that and on the drop down menu click recovery mode.

---

### Post by drmrgd on 2012-08-31
Sorry, I missed the apt-get clean in the original post!  Went back and re-read it just now.

Everything appears to be working normally with the exception of installing Wine.  As far as I could tell, there are no broken packages or any other errors.  Do you get any errors trying to install any other packages?  Are there any errors reported when you run 'apt-get update'?  Aside from maybe something like:

```
sudo dpkg --audit
```

to look for partially installed packages, I'm out of ideas.  

The only other thing I can come up with is a conflict in your sources list, which is a bit of stretch.  Maybe we can find something off in /etc/apt/source.list that is causing the conflict in wine1.4?

---

### Post by bobzxr on 2012-08-31
I was playing around a little bit, and my problem got solved. Don't know exactly what fixed it. I figure I had these problems because of a bad internet connection. Anyhow, thank you for your help and time!

---

