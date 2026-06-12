---
title: "Need to install jre 6_07 on xubuntu 10.04 LTS"
date: 2010-06-28
forum: Desktop Environments
---

### Post by raviprakashm on 2010-06-28
Hi,

I am new to Ubuntu/Xubuntu/Debian derived Linux. 

Recently I have intalled xubuntu 10.04 LTS on my desktop & I need to access Oracle applications through mozila firefox browser. 
my oracel application servers uses JRE 1.6_07 and i need to use same plugin in my desktop environment/browser.

Please help  to get jre_1.6_07*.deb,  install & configure the same as default plugin for my browser.

Regards - Raviprakash.

---

### Post by howefield on 2010-06-28
Enable the Partner repository and install with Synaptic Package Manager.

Systems > Administration > Synaptic Package Manager. 

Select Settings > Repositories > Other Software and place a check against Partner. Reload the sources and search for sun-java6-jre, sun-java6-plugin and sun-java6-fonts.

---

### Post by raviprakashm on 2010-06-28
Hi,

Can anybody tell me, from where can i get/download Sun JRE 1.6_07 installer for Debian/Xubuntu?

Raviprakash

---

### Post by interzoneuk on 2010-06-28
Hi.

Once you add the 'partner' repo (you can just remove the comment in sources.list) you can download sun jre/jdk/plugin (for 32+64bit)

The version is newer than 6.07, the version in apt is 6.20.

If you really need the older version (you shouldn't) be aware that there is no 64bit browser plugin for the earlier version, you would need to download it from [http://java.sun.com/](http://java.sun.com/) and install manually.

---

