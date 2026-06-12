---
title: "sun-java6-plugin package missing the plugin?"
date: 2012-01-02
forum: Desktop Environments
---

### Post by akos.maroy on 2012-01-02
Hi,

I'm trying to get the SUN Java6 plugin working in my browser, but it seems that the sun-java6-plugin package actually does not contain the browser plugin itself. After installing the plugin, this package seems to contain only references to directories, but no plugin files:

```
# dpkg-query -L sun-java6-plugin
/.
/usr
/usr/share
/usr/share/doc
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/sun-java6-plugin
/usr/lib
/usr/lib/mozilla
/usr/lib/mozilla/plugins
/usr/lib/xulrunner-addons
/usr/lib/xulrunner-addons/plugins
/usr/share/doc/sun-java6-plugin

# ls /usr/lib/mozilla/plugins | more
flashplugin-alternative.so
libtotem-cone-plugin.so
libtotem-gmp-plugin.so
libtotem-mully-plugin.so
libtotem-narrowspace-plugin.so
npwrapper.nppdf.so

```

how can one make the sun browser plugin work in his browser?

this is on an ubuntu 10.04 64 bit system..

any help would be appreciated.


Akos

---

### Post by crazy bird on 2012-01-02
Did you also installed the resctricted-extras packages? Check here how to complete the multimedia under Ubuntu: [https://sites.google.com/site/tipsandtricksforubuntu/multimedia](https://sites.google.com/site/tipsandtricksforubuntu/multimedia)

---

### Post by akos.maroy on 2012-01-02
> **crazy bird said:**
> Did you also installed the resctricted-extras packages? Check here how to complete the multimedia under Ubuntu: [https://sites.google.com/site/tipsandtricksforubuntu/multimedia](https://sites.google.com/site/tipsandtricksforubuntu/multimedia)

the sun-java6-plugin package already comes from the 'partners' repository. but I haven't found it anywhere else...

---

### Post by Karlchen on 2012-01-02
Hello, akos.maroy.

As the Oracle folks have revoked their permission to Linux distributors of offering Oracle Java through their repositories, Canonical, too, had to remove Oracle Java from their repositories.
Therefore, currently you have got two choices:
Either you can use OpenJRE/OpenJDK, because your Java applications run fine on them. You will be able to get them from the Canonical repositories.
Or you have to stick with Oracle Java. In the latter case, you should follow the instruction here, [**Oracle (Sun) Java JRE for Ubuntu, Linux Mint and Debian**]("http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-64-BIT-UBUNTU"), carefully. Note that there are actually two step by step instructions: one for the 32-bit Java installation  and one for the 64-bit Java installation.
As you reported problems related to the Firefox plugin integration you may wish to pay extra attention to the steps on how to [[SIZE=3][COLOR=#000000]**Install the Firefox plugin**[/COLOR][/SIZE]]("http://sites.google.com/site/easylinuxtipsproject/java#TOC-Install-the-Firefox-plugin1").

HTH,
Karl

---

### Post by crazy bird on 2012-01-02
Or install the OpenJDK package which is a good Sun JAVA replacement.

---

### Post by sammiev on 2012-01-02
Post #4 is the method I have used for sometime now. Sun-java seems to be required for a lot games and gaming sites. If OpenJDK works for you that is great.

---

### Post by akos.maroy on 2012-01-02
> **Karlchen said:**
> Hello, akos.maroy.

As the Oracle folks have revoked their permission to Linux distributors of offering Oracle Java through their repositories, Canonical, too, had to remove Oracle Java from their repositories.


this is interesting, as actually the sun-java6 packages are there, I can install the JRE or the JDK, and they all work fine. the only thing that doesn't work is the browser plugin.

> **Karlchen said:**
> Therefore, currently you have got two choices:
Either you can use OpenJRE/OpenJDK, because your Java applications run fine on them. You will be able to get them from the Canonical repositories.
Or you have to stick with Oracle Java. In the latter case, you should follow the instruction here, [**Oracle (Sun) Java JRE for Ubuntu, Linux Mint and Debian**]("http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-64-BIT-UBUNTU"), carefully. Note that there are actually two step by step instructions: one for the 32-bit Java installation  and one for the 64-bit Java installation.
As you reported problems related to the Firefox plugin integration you may wish to pay extra attention to the steps on how to [[SIZE=3][COLOR=#000000]**Install the Firefox plugin**[/COLOR][/SIZE]]("http://sites.google.com/site/easylinuxtipsproject/java#TOC-Install-the-Firefox-plugin1").

HTH,
Karl

thanks, seems to work fine...

---

### Post by crazy bird on 2012-01-02
> Originally Posted by **Karlchen** [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11580896#post11580896") 
[I]Hello, akos.maroy.

As the Oracle folks have revoked their permission to Linux distributors of offering Oracle Java through their repositories, Canonical, too, had to remove Oracle Java from their repositories.[/I]
[QUOTE]this is interesting, as actually the sun-java6 packages are there, I can install the JRE or the JDK, and they all work fine. the only thing that doesn't work is the browser plugin.[/QUOTE]
 
I thougth that the Sun JAVA package is not standard installed due to the reason that Sun JAVA is not open source i.e. non-free software. Even so, it is available in the repository.

---

### Post by akos.maroy on 2012-01-02
> **crazy bird said:**
> I thougth that the Sun JAVA package is not standard installed due to the reason that Sun JAVA is not open source i.e. non-free software. Even so, it is available in the repository.

it's not standard installed, but it's in the 'canonical partners' repository

---

### Post by crazy bird on 2012-01-02
> **akos.maroy said:**
> it's not standard installed, but it's in the 'canonical partners' repository
Really??? I really thougth it was due to the fact that Oracle Sun JAVA is non-free.....

---

### Post by akos.maroy on 2012-01-02
> **crazy bird said:**
> Really??? I really thougth it was due to the fact that Oracle Sun JAVA is non-free.....

I guess this is what the partners repository is for. also, the new Software Center offers software for purchase as well - I guess those are also non-free :)

---

