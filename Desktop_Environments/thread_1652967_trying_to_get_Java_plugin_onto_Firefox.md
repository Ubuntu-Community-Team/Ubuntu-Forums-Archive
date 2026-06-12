---
title: "trying to get Java plugin onto Firefox"
date: 2010-12-26
forum: Desktop Environments
---

### Post by Skaperen on 2010-12-26
At first, I enabled the partner source and installed "sun-java6-plugin", as that was listed in an earlier Ubuntu install's package list.  But Firefox does not see this plugin (even after a reboot).  So I removed that package and its friends, and installed "icedtea6-plugin" as found on [https://help.ubuntu.com/community/FirefoxPlugins](https://help.ubuntu.com/community/FirefoxPlugins), but this does not work, either.  This is with Ubuntu 10.10 for i386 on an ASUS Eee PC 900.

Any ideas on how to get a Java plugin working?  I know I've had it working before without having to do anything like this.  But that could have been an earlier version of Firefox.  Could Firefox now be broken?  Or could they have blocked Java, now?

---

### Post by vangop on 2010-12-26
Hava sun-java6-plugin installed and it works in FF.
You need to also have a jre installed though - sun-java6-jre for plugin to work.

---

### Post by Skaperen on 2010-12-26
> **vangop said:**
> Hava sun-java6-plugin installed and it works in FF.
You need to also have a jre installed though - sun-java6-jre for plugin to work.
The "sun-java6-jre" package was installed, as was "sun-java6-bin" and "java-common".

---

