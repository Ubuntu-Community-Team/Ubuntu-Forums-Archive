---
title: "Strange problem updating repos"
date: 2012-12-08
forum: Desktop Environments
---

### Post by Acharn on 2012-12-08
I've been trying all day to solve my problem of installing AlephOne game platform. I stumbled across the face that there's supposed to be a pachage in the getdeb repository. Swell, except the IP address isn't responding. So I found another ppa and seemed to get it installed OK and the pgp key installed, and when I went to "sudo apt-get update" I got my usual assortment of errors -- I have severe connectivity problems with all the repos, that come and go. Some days they work and most days they don't. Anyway, following a suggestion I found on some other forum I tried manually following a couple of the links that apt-get wasn't able to connect to.
```
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages  Unable to connect to extras.ubuntu.com:http:
```
OK, in the directory at extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386 there are two files, Packages.bz2 and Packages.bz. I would guess that the request for Packages got a 404 message.

```
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_US  Unable to connect to extras.ubuntu.com:http:
```
In the directory at extras.ubuntu.com/ubuntu/dists/precise/main/ there is no sub-directory i18n. I presume apt-get received a 404 File Not Found.

```
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en  Unable to connect to extras.ubuntu.com:http:
```
Same as for above. There is no sub-directory i18n.

I haven't tried following all the links in the error messages, but my guess is they all have the same cause. Then there's the problem that there's no response at all from archive.getdeb.org, so of course I couldn't connect there.

Can anyone explain what's going on here, and maybe recommenda solution? A lot of my difficulty is just from my ISP and lousy network connectivity, but I'm baffled that apt-get is trying to download from non-existent locations. Oh, yeah, I have similar results using Synaptic and Software Center. And Update Manager, for that matter. It keeps saying it was last updated (now) six days ago, and for three days I've been trying to update it.

---

### Post by Kirk Schnable on 2012-12-08
Apt decides where to download from based on the file **/etc/apt/sources.list** and any files in **/etc/apt/sources.list.d/**. I suggest removing or commenting out the affected source lines, running **apt-get update** and trying your package installation again.

---

### Post by Acharn on 2012-12-23
I finally deleted all the ppa's except for Wine. That was the only way I could get 'apt-get update' to succeed.

---

### Post by Kirk Schnable on 2012-12-23
> **Acharn said:**
> I finally deleted all the ppa's except for Wine. That was the only way I could get 'apt-get update' to succeed.

Glad to hear you got this sorted out. If you need any assistance re-adding or fixing other affected PPA's please feel free to start up a new thread.

---

