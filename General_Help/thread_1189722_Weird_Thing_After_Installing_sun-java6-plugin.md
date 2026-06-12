---
title: "Weird Thing After Installing sun-java6-plugin"
date: 2009-06-17
forum: General Help
---

### Post by Gias Kay on 2009-06-17
I upgraded from Intrepid to Jaunty and saw sun-java6-plugin has become available to 64-bit users, so I installed it. But I made a little mistake later by installing ubuntu-restricted-extra which contains IcedTea, so I manually removed IcedTea packages installed by ubuntu-restricted-extra.

Now in Firefox it lists my installed plugin as the following:

[IMG]http://img32.imageshack.us/img32/7223/33224382.png[/IMG]

It shows "libnpjp2.so" instead of something like "Sun Java6 Plugin", but it works.

My question is, if there is anyway to correct the name shown from "libnpjp2.so" to something more proper?

Currently in my filesystem:

/usr/lib/mozilla/plugins/libjavaplugin.so

The above file is a link pointing to:

/etc/alternatives/mozilla-javaplugin.so

Which is also a link pointing to:

/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so

---

### Post by Yellow Pasque on 2009-06-17
This is what is shown for me as well, and I've never had Icedtea installed. You could probably use vim to edit the string in that library file, but I don't really see a reason (other than pure aesthetics) to do this. Also, it's against proper Debian policy to do that and may confuse dpkg if you ever upgrade the package or distribution.

---

