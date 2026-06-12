---
title: "Synaptic not working properly"
date: 2006-08-07
forum: Desktop Environments
---

### Post by Flos-cuculi on 2006-08-07
Whenever I try to install a package with synaptic everything freezes. I haven't changed anything to synaptic recently except add the universe and multiverse repository. 
I wish I could describe the problem less vague. Which outputs or information could be helpfull to find the problem?
Thanks in advance!

---

### Post by feanix on 2006-08-07
I'm having a similar problem. When telling Synaptic to reload, it will try to connect to each repository for about a minute and give up, finally telling me it couldnt connect and that I should check my internet connection and preferences. My internet is working, so perhaps its something to do with the authentication keys?

Also, I had to disable ipv6 (there was a apparent clash between ipv4 and ipv6 which caused firefox to load pages so slowly it generally timed out every single time). I don't know if ipv6 has anything to do with Synaptic.

---

### Post by chavo on 2006-08-07
Sounds like a problem connecting to your repos. If you're using the us archives these seem to go down or timeout frequently. Just remove the us. from all the entries in /etc/apt/sources.lst and try again. This worked for me. The speed may be a little slower since the main archives are farther away, but it seems to be much more stable.

---

### Post by eXisor on 2006-08-07
Could be a couple of problems/issues here:

1) Ipv6 may slow the resolution of the IP query down slightly but should not cause a timeout. This slight slowdown will affect everything that accesses the network, including synaptic/apt-get/aptitude. We're talking milliseconds here. There are threads aplenty here to help you switch it off. It wouldn't be my first stop to resolve the issues.

2) The ubuntu servers have been slow/failing for almost everyone. Again, there are plenty of threads about. Even the mirrors are struggling. It seems, at the moment at least, that ubuntu has gotten too popular for its own good. Be patient, retry.

3) Connectivity problems in general, ie. frequent timeouts when browsing, are likely due to:

- an MTU (maximum Transmission Unit) problem. Your ISP may not be set up for the optimal 1500 mtu ubuntu defaults to. Go to [www.speedguide.net](www.speedguide.net) and run their analysis. If need be , modify your mtu. Browsing will get better. This is what I suggest as the first stop. It can make a dramatic difference.

- Your network cards drivers may not be the best/flaky. This one is difficult to resolve. You can try drivers from different distro's or the manufacturer. Installation is usually tricky for a n00b. Still, worth a shot if all else fails.

- A bad network setup/config. Automation sometimes tries to do too much, leaving a working but sub-optimal config. If all else fails this may be the problem. Post ifconfig data, the contents of /etc/network/interfaces file, and /etc/resolve.conf and maybe someone can help.

---

### Post by fakie_flip on 2006-08-07
sudo apt-get remove --purge -y --force-yes synaptic

---

### Post by Flos-cuculi on 2006-08-07
This is how my sources.list looks like. Should I make any changes?


# deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy main restricted

# deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-updates main restricted

# deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-updates main restricted

# deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

# deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe

deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) breezy multiverse universe main restricted

---

### Post by eXisor on 2006-08-07
Try drooping the 'be.', that'll make it go to ubuntu home instead of the mirror.

---

### Post by Flos-cuculi on 2006-08-07
Now I get this error message when I open synaptic:


W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages)

---

### Post by feanix on 2006-08-07
I've been trying apt-get to see how it compares. I noticed something potentially interesting:

Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out

I got that error message. Should that IP really be 1.0.0.0?

---

### Post by eXisor on 2006-08-08
Yep, that does seem dodgy. What's your setup? pc - router - modem?

---

### Post by feanix on 2006-08-08
wireless router. its odd, everything else works perfectly fine. :/of

EDIT: it has worked sporadically. Sometimes it manages to download at least some of the packages.

---

