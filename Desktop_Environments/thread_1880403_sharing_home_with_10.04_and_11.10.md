---
title: "sharing /home with 10.04 and 11.10"
date: 2011-11-13
forum: Desktop Environments
---

### Post by shwallace on 2011-11-13
will it cause any problems using the same /home directory with ubuntu 10.04LTS and ubuntu 11/.10? I prefer to use the 10.04 LTS until I have to replace it and am trying to get used to the new interface.

---

### Post by Lars Noodén on 2011-11-13
It will work fine.  You can also get by with one swap partition shared between the two systems.

---

### Post by shwallace on 2011-11-13
thanks for the info. didn't want to mess up my 10.04lts setup!

---

### Post by oldfred on 2011-11-13
I prefer not to share /home. Software is designed to update to a newer version, so that should work without an issue. But then new settings from the new verisons may not be totally compatible with the old version.

Actually /home settings are very small so I split /home into /home which I keep inside  (root) and copy some or most settings to my new install, but keep the user data in a separate partition which I mount & link into /home in each install.

I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

### Post by Lars Noodén on 2011-11-14
> **oldfred said:**
> Software is designed to update to a newer version, so that should work without an issue. But then new settings from the new verisons may not be totally compatible with the old version.

In such cases, the new version usually has a different name or location for the configuration file.

---

### Post by Azyx on 2011-11-14
> **shwallace said:**
> thanks for the info. didn't want to mess up my 10.04lts setup!

I have tried and with 8.04LTS and it don't work well, so look at oldfreds reply.

Thanx oldfred

---

### Post by Azyx on 2011-11-14
> **Lars Noodén said:**
> In such cases, the new version usually has a different name or location for the configuration file.

Usually don&#7831; seems to be very trustworthy. It a bitch to downgrade.

---

### Post by Copper Bezel on 2011-11-14
Yeah, I've had apps (Chrome, for instance) refuse to load settings from later versions. And between 10.04 and 11.10, you're probably looking at two incompatible sets of gconf keys in some areas. I'd have 10.04 own /home while the other install merely symlinks to Documents, Pictures, etc. and whichever specific config directories you know you can share between.

---

