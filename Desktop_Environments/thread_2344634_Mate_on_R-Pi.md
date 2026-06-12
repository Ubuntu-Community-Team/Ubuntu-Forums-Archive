---
title: "Mate on R-Pi"
date: 2016-11-27
forum: Desktop Environments
---

### Post by Geoff_Lane on 2016-11-27
Folks,

I run Ubuntu Mate on a headless RaspberryPi and access it by ssh and sometimes VNC using an ssh tunnel.

The Pi is a relative's device used as a media server.

I often run apt-get update followed by apt-get upgrade but for some time now nothing gets upgraded and it finishes with;

```
W: Failed to fetch http://ppa.launchpad.net/flexiondotorg/wily-pi/ubuntu/dists/wily/main/binary-armhf/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

The sources.list does not contain that address and as said, nothing been upgraded for quite some time.

Could this be a problem?

Geoff

---

### Post by mcduck on 2016-11-27
Take a look inside /etc/apt.sources.list.d/ directory, there's probably a .list file there that includes that repository. Remove the files and apt-get should be happy again.

(looks like that repository doesn't exist any more, which explains the error)

---

### Post by Geoff_Lane on 2016-11-27
> **mcduck said:**
> Take a look inside /etc/apt.sources.list.d/ directory, there's probably a .list file there that includes that repository. Remove the files and apt-get should be happy again.

(looks like that repository doesn't exist any more, which explains the error)

All very odd but seems version 15:10 is not supported any more - asks I upgrade to 16:04 LTS. Got that on Laptop but R-Pi working headless as a server so didn't really need to upgrade but may have to now.

Geffers

---

### Post by yetimon_64 on 2016-11-27
> **Geoff_Lane said:**
> All very odd but seems version 15:10 is not supported any more...

Yes, that is right, a non LTS release only get 9 months of support while LTS releases get 5 years support these days.

It is a good idea to install, or update to, an LTS version.

---

### Post by Geoff_Lane on 2016-11-28
> **yetimon_64 said:**
> Yes, that is right, a non LTS release only get 9 months of support while LTS releases get 5 years support these days.

It is a good idea to install, or update to, an LTS version.

My laptops I always use LTS - was using 12:04 for ages, was so stable.

Didn't really think long term when I installed on the R-Pi so may go for a reinstall.

Geffers

---

