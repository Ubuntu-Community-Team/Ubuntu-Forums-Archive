---
title: "Having problems with flash on Jaunty? Fix it here!"
date: 2009-05-19
forum: General Help
---

### Post by JECHO on 2009-05-19
***_First off this tutorial assumes you have a fresh install of Jaunty..._***


**1) Add sources to your repositories**

First you need to backup your /etc/apt/sources.list file:

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

...then add the text below to your /etc/apt/sources.list file

```

## Medibuntu
deb http://packages.medibuntu.org/ jaunty free non-free
```


next, add authentication key to your software sources (for medibuntu):

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```


then upgrade your system

```
sudo apt-get upgrade
```


[B]
2) Installing multimedia codecs, flash plugins, JRE, DVD support and MS fonts[/B]

```
sudo apt-get install ubuntu-restricted-extras w32codecs libdvdcss2
```


Reboot and now Flash will work smoothly :) (And DVD's will play as well as pretty much every other media format!)

---

### Post by paradigm2 on 2009-05-19
Thanks but doesn't this just install flash (among other things) and not really fix other issues?

---

### Post by JECHO on 2009-05-19
> **paradigm2 said:**
> Thanks but doesn't this just install flash (among other things) and not really fix other issues?

This is the method I use and have always used and I have NEVER had a problem with flash or any other codecs. This is the same method I recommend on IRC and it seems to fix everyones problems.

---

### Post by ashmew2 on 2009-05-30
Hi Jecho , I was wondering what to do if you have already installed flash using Hardy's default repositories ? 

I mean should i just do sudo apt-get remove libflashsupport 

And then do as you said in #1 ?

Thanks! :D

---

