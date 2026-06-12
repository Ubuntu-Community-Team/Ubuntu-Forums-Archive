---
title: "Failed to load session &quot;gnome&quot;."
date: 2011-05-16
forum: Desktop Environments
---

### Post by Northernen on 2011-05-16
Having just installed Ubuntu 11.04 for the first time. I did not like the look of Unity, so I purged it, and instead installed Gnome 3.

Now as I try to log on I get the message "Failed to load session "gnome"", regardless of choosing "ubuntu", "Ubuntu GNOME Shell Desktop" or "User Defined Session" in the drop-down box on the log-in screen. I can still access the recovery console.

I thought perhaps some of the packages I installed and downloaded was outdated, so I did apt-get upgrade and dist-upgrade, but it found no updates.

What can be the problem?

---

### Post by apoole7 on 2011-05-16
Same problem here - how did you solve it?

Thanks

Andy

---

### Post by wildmanne39 on 2011-05-16
> **apoole7 said:**
> Same problem here - how did you solve it?

Thanks

Andy
Hi, my understanding if you install gnome 3 and it does not work the only thing you can do is a fresh install of ubuntu.:)

---

### Post by Northernen on 2011-05-19
> **apoole7 said:**
> Same problem here - how did you solve it?

Thanks

Andy

Silly mistake really.

In my eager to get it to work I had forgotten to install "ugr-desktop-g3".

---

### Post by pengpengpeng on 2011-05-19
if you however want to REMOVE gnome3 bcause its not working as in my case:

to revert packet changes made by the gnome3 release use "ppa-purge".
afaik it will reset ALL changes done by this repository (ppa gnome3-team) and put them back to original distribution settings.

```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:gnome3-team/gnome3

```i found this in a post on this board, but couldnt say thx coz thread got locked, maybe someone finds this helpful so i post it here :D

---

### Post by BDNiner on 2011-08-11
Thanks a lot pengpengpeng. This saved me a lot of time.

---

