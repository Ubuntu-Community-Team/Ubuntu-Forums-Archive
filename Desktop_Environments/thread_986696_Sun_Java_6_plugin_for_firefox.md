---
title: "Sun Java 6 plugin for firefox"
date: 2008-11-18
forum: Desktop Environments
---

### Post by tienhn on 2008-11-18
Hi All,
I am on Ubuntu 8.10 AMD64. I tried to install the sun jave6 plugin with:

sudo apt-get install sun-java6-plugin

The I go these:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

Any pointers where about this package is moved to?

Thanks,

---

### Post by taurus on 2008-11-18
Maybe you don't have enough repos enable in /etc/apt/sources.list.  Post it here.

```
cat /etc/apt/sources.list
```

---

### Post by Keyper7 on 2008-11-19
You are trying to install a 32-bit-only package in a 64-bit environment.

The Sun Java plugin is currently only available for 32-bit architecture. What 64-bit users usually do is one of the following options:

1) Install the ia32-sun-java6-bin package, which will allow you to use 32-bit Java even on your 64-bit architecture. If you install this package, the plugin will be located at

/usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

and you can copy it to the folder ~/.mozilla/plugins

However, if you choose this method you'll have to use the plugin in a 32-bit Firefox for it to work. The easiest way to get a 32-bit Firefox is to download it from [www.mozilla.com](www.mozilla.com). Ask if you need more details.

2) Install the icedtea6-plugin package, which contains the OpenJDK implementation of Java. This is the easier method, as it is a 64-bit plugin, but it is reported that this plugin does not work on all applets (should work on most, though)

PS: it might take an entire day to check your reply to this, but I will.

---

### Post by webbie180 on 2008-11-19
Or install ubuntu-restricted-extras.

---

### Post by apesa on 2009-12-03
Thanks a lot Keyper7 for the icedtea6-plugin idea. I was struggling to get a JRE plugin in firefox on karmic 64

---

