---
title: "Upgrading Ubuntu 5.10/repository not working, something to do with Bad header line??"
date: 2005-12-13
forum: General Help
---

### Post by brynjarh on 2005-12-13
[COLOR="Green"]Problem solved, [carlosqueso]("http://ubuntuforums.org/member.php?u=48710") suggested at the original post to take out the is. in the addresses, it worked. I hope the IS servers will be fixed![/COLOR]

Originally posted this at [http://ubuntuforums.org/showthread.php?t=103131](http://ubuntuforums.org/showthread.php?t=103131) but not much of a reply.

So I probably posted it in the wrong place. Basically sudo apt-get dist-upgrade doesn't work, something to do with *Bad header line* and *a single header line over 360 chars*. This of course gives me no understanding what so ever on why my system refuses to upgrade it self, I'm hoping someone here can inform me about it.

So the question would be, why? And then maybe, how do I fix it?

apt-get, aptitude and synaptic all fail.

sudo apt-get dist-upgrade
```
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages will be upgraded:
  evms evms-ncurses iptables libevms-2.5 libgnutls11 xkeyboard-config
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1729kB of archives.
After unpacking 77.8kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://is.archive.ubuntu.com breezy-updates/main xkeyboard-config 0.6-5breezy1
  Bad header line
Err http://is.archive.ubuntu.com breezy-updates/main libgnutls11 1.0.16-13.1ubuntu1
  Bad header line
Err http://is.archive.ubuntu.com breezy-backports/main libevms-2.5 2.5.3-7ubuntu1~breezy1
  Got a single header line over 360 chars
Err http://is.archive.ubuntu.com breezy-backports/main evms 2.5.3-7ubuntu1~breezy1
  Bad header line
Err http://is.archive.ubuntu.com breezy-backports/main evms-ncurses 2.5.3-7ubuntu1~breezy1
  Got a single header line over 360 chars
Err http://is.archive.ubuntu.com breezy-updates/main iptables 1.3.1-2ubuntu1.1
  Bad header line
Failed to fetch http://is.archive.ubuntu.com/ubuntu/pool/main/x/xkeyboard-config/xkeyboard-config_0.6-5breezy1_all.deb  Bad header line
Failed to fetch http://is.archive.ubuntu.com/ubuntu/pool/main/g/gnutls11/libgnutls11_1.0.16-13.1ubuntu1_i386.deb  Bad header line
Failed to fetch http://is.archive.ubuntu.com/ubuntu/pool/main/e/evms/libevms-2.5_2.5.3-7ubuntu1~breezy1_i386.deb  Got a single header line over 360 chars
Failed to fetch http://is.archive.ubuntu.com/ubuntu/pool/main/e/evms/evms_2.5.3-7ubuntu1~breezy1_i386.deb  Bad header line
Failed to fetch http://is.archive.ubuntu.com/ubuntu/pool/main/e/evms/evms-ncurses_2.5.3-7ubuntu1~breezy1_i386.deb  Got a single header line over 360 chars
Failed to fetch http://is.archive.ubuntu.com/ubuntu/pool/main/i/iptables/iptables_1.3.1-2ubuntu1.1_i386.deb  Bad header line
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

/etc/apt/sources.list
```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic

# Ubuntu supported packages (packages)
deb http://is.archive.ubuntu.com/ubuntu breezy main restricted
deb http://is.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu community supported packages (packages)
deb http://is.archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://is.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse

# Ubuntu backports project (packages)
deb http://is.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
```

---

### Post by stuporglue on 2005-12-13
You only waited two hours, so it's no wonder there wasn't much of a reply. You also either didn't do what the person who did reply suggested, or didn't post your results. Anyone else who was going to reply was probably waiting to see what happened if you followed his instructions, and posted the results. 

Heck, the person who replied to you would probably have been willing to give more help if you'd posted the results of trying what he said. 

I'd try that, then post back on your original post what happened.

---

