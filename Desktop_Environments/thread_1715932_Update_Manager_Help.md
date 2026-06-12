---
title: "Update Manager Help"
date: 2011-03-27
forum: Desktop Environments
---

### Post by _joecrawford on 2011-03-27
When I try to do an manual check of my updates, I get this error:

"Failed to download repository information"

With these codes below:

W:Failed to fetch [http://ppa.launchpad.net/team-xmbc/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/team-xmbc/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, 
W:Failed to fetch [http://ppa.launchpad.net/team-xmbc/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/team-xmbc/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found
, 
E:Some index files failed to download, they have been ignored, or old ones used instead.

Using 10.10, any ideas on how to fix this?

---

### Post by dnairb on 2011-03-27
From the look of those errors, your sources.list is wrong. We need to find the sources.list error.

Can you post the output of:

```
ls /etc/apt/
```

---

### Post by _joecrawford on 2011-03-27
Here it is


$ ls /etc/apt
apt.conf.d     secring.gpg   sources.list.d     trustdb.gpg  trusted.gpg~
preferences.d  sources.list  sources.list.save  trusted.gpg  trusted.gpg.d

This is where I started, but didn't see anything wrong.

---

### Post by Krytarik on 2011-03-27
Ok, this is fairly easy: You have a third-party PPA and its associated sources in "System -> Administration -> Software Sources". They don't work (anymore). Check the PPA's site in Launchpad. Based on that result
- disable
- remove or
- remove and re-add them.

Greetings.

---

### Post by dnairb on 2011-03-28
Actually forget the above, I have spotted the error.

The problem is you have "team-**xmbc**/ppa" listed as a repository, where it should read "team-**xbmc**/ppa".


To remove the incorrect source, in terminal run:

```
sudo rm /etc/apt/sources.list.d/team-xmbc-ppa-maverick.list
```


To add the correct repository, again in terminal run:

```
sudo add-apt-repository ppa:team-xbmc/ppa
```

Then run:

```
sudo apt-get update
```


As an aside: The apt-add-repository command can take the "-r" modifier in Ubuntu 10.10 to remove the repository, but it doesn't seem to remove deb-src entries

---

### Post by Krytarik on 2011-03-28
LOL:D  The next bunch of typos.
> **dnairb said:**
> ```
sudo apt-add-repository ppa:team/xbmc/ppa
```
```
sudo **add**-**apt**-repository ppa:team**-**xbmc/ppa
```And to also remove the *.save file:
```
sudo rm /etc/apt/sources.list.d/team-xmbc-ppa-maverick.list*
```

---

### Post by dnairb on 2011-03-28
> **Krytarik said:**
> LOL:D  The next bunch of typos.
```
sudo **add**-**apt**-repository ppa:team**-**xbmc/ppa
```And to also remove the *.save file:
```
sudo rm /etc/apt/sources.list.d/team-xmbc-ppa-maverick.list*
```

Thank you! I have edited my post above accordingly.

Actually it seems add-apt-repository and apt-add-repository are interchangeable

---

### Post by Krytarik on 2011-03-28
> **dnairb said:**
> 
Actually it seems add-apt-repository and apt-add-repository are interchangeable
Ah, actually! I just noticed the "wrong" spelling when I looked up the manpage of it, regarding the remove option you mentioned. (I have a respective searchplugin in Firefox, and an extension which allows me to choose the searchplugin in the context menu.)

---

### Post by _joecrawford on 2011-03-28
Thank you for the help, all is well now!

---

