---
title: "Errors on update"
date: 2014-09-10
forum: Desktop Environments
---

### Post by x-terry on 2014-09-10
I am getting the following errors on update, I am guessing that my repo list is incorrect for Cairo Dock. I am on Ubuntu 14.04

```
Hit https://private-ppa.launchpad.net trusty/main amd64 Packages
Err http://download.tuxfamily.org trusty/cairo-dock amd64 Packages
  404  Not Found [IP: 88.191.250.171 80]
Hit https://private-ppa.launchpad.net trusty/main i386 Packages
Err http://download.tuxfamily.org trusty/cairo-dock i386 Packages
  404  Not Found [IP: 88.191.250.171 80]
Ign http://download.tuxfamily.org trusty/cairo-dock Translation-en_GB
Ign http://download.tuxfamily.org trusty/cairo-dock Translation-en
Ign https://private-ppa.launchpad.net trusty/main Translation-en_GB            
Ign https://private-ppa.launchpad.net trusty/main Translation-en               
Fetched 1,810 kB in 6s (288 kB/s)                                              
W: Failed to fetch http://download.tuxfamily.org/glxdock/repository/ubuntu/dists/trusty/cairo-dock/binary-amd64/Packages  404  Not Found [IP: 88.191.250.171 80]


W: Failed to fetch http://download.tuxfamily.org/glxdock/repository/ubuntu/dists/trusty/cairo-dock/binary-i386/Packages  404  Not Found [IP: 88.191.250.171 80]


E: Some index files failed to download. They have been ignored, or old ones used instead.

```

This is the last part of my sources list:

```

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
deb http://download.tuxfamily.org/glxdock/repository/ubuntu trusty cairo-dock

```

---

### Post by slickymaster on 2014-09-10
> **x-terry said:**
> I am getting the following errors on update, I am guessing that my repo list is incorrect for Cairo Dock. I am on Ubuntu 14.04

```
Hit https://private-ppa.launchpad.net trusty/main amd64 Packages
Err http://download.tuxfamily.org trusty/cairo-dock amd64 Packages
  404  Not Found [IP: 88.191.250.171 80]
Hit https://private-ppa.launchpad.net trusty/main i386 Packages
Err http://download.tuxfamily.org trusty/cairo-dock i386 Packages
  404  Not Found [IP: 88.191.250.171 80]
Ign http://download.tuxfamily.org trusty/cairo-dock Translation-en_GB
Ign http://download.tuxfamily.org trusty/cairo-dock Translation-en
Ign https://private-ppa.launchpad.net trusty/main Translation-en_GB            
Ign https://private-ppa.launchpad.net trusty/main Translation-en               
Fetched 1,810 kB in 6s (288 kB/s)                                              
W: Failed to fetch http://download.tuxfamily.org/glxdock/repository/ubuntu/dists/trusty/cairo-dock/binary-amd64/Packages  404  Not Found [IP: 88.191.250.171 80]


W: Failed to fetch http://download.tuxfamily.org/glxdock/repository/ubuntu/dists/trusty/cairo-dock/binary-i386/Packages  404  Not Found [IP: 88.191.250.171 80]


E: Some index files failed to download. They have been ignored, or old ones used instead.

```

This is the last part of my sources list:

```

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
**[COLOR=#ff0000]deb http://download.tuxfamily.org/glxdock/repository/ubuntu trusty cairo-dock[/COLOR]**

```

There is no repository for Trusty as you can verify [here]("http://download.tuxfamily.org/glxdock/repository/ubuntu/dists/"). So you'll have to edit your sources list, commenting that line.

---

### Post by x-terry on 2014-09-12
Thanks, I have commented it out

---

### Post by slickymaster on 2014-09-12
You're welcome. Glad you got it fixed.

---

