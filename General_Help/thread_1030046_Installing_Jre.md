---
title: "Installing Jre"
date: 2009-01-04
forum: General Help
---

### Post by newb austin on 2009-01-04
I have all everything installed for jre but the plugin for firefox, and thats what I need. So when I type this in
sudo apt-get install sun-java6-plugin it comes up with this error:
```
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate
```

Any ideas?

---

### Post by Ahadiel on 2009-01-04
Do you have multiverse enabled?

---

### Post by newb austin on 2009-01-04
> **Ahadiel said:**
> Do you have multiverse enabled?

Well I tried it with it checked and unchecked. But just incase I am not doing multiverse correct, could you give me a link explaining? Thanks for the reply.

---

### Post by semi_fiction on 2009-01-04
You can install the plugin via Synaptic Package Manager (System->Administration->Synaptic Package Manager).
Just search for "Java Runtime Environment," the plugin will be in the search results. Select the plugin and apply changes.

---

### Post by Ahadiel on 2009-01-04
> **newb austin said:**
> Well I tried it with it checked and unchecked. But just incase I am not doing multiverse correct, could you give me a link explaining? Thanks for the reply.

Just make sure it's checked.
```
sudo apt-get update && sudo apt-get install sun-java6-plugin
```

---

### Post by newb austin on 2009-01-04
> **semi_fiction said:**
> You can install the plugin via Synaptic Package Manager (System->Administration->Synaptic Package Manager).
Just search for "Java Runtime Environment," the plugin will be in the search results. Select the plugin and apply changes.

I don't see the plugin anywhere.

---

### Post by newb austin on 2009-01-04
> **Ahadiel said:**
> Just make sure it's checked.
```
sudo apt-get update && sudo apt-get install sun-java6-plugin
```

Still get the same error.

---

### Post by Ahadiel on 2009-01-04
```
apt-cache search java6
```
Also, what Ubuntu version are you running?

---

### Post by newb austin on 2009-01-04
> **Ahadiel said:**
> ```
apt-cache search java6
```
Also, what Ubuntu version are you running?

This is what I got when I did that
```
default-jdk - Standard Java or Java compatible Development Kit
default-jre - Standard Java or Java compatible Runtime
default-jre-headless - Standard Java or Java compatible Runtime (headless)
openjdk-6-jdk - OpenJDK Development Kit (JDK)
openjdk-6-jre - OpenJDK Java runtime, using Hotspot JIT
openjdk-6-jre-headless - OpenJDK Java runtime, using Hotspot JIT (headless)
ia32-sun-java6-bin - Sun Java(TM) Runtime Environment (JRE) 6 (32-bit)
sun-java6-bin - Sun Java(TM) Runtime Environment (JRE) 6 (architecture dependent files)
sun-java6-demo - Sun Java(TM) Development Kit (JDK) 6 demos and examples
sun-java6-doc - Sun JDK(TM) Documention -- integration installer
sun-java6-fonts - Lucida TrueType fonts (from the Sun JRE)
sun-java6-javadb - Java(TM) DB, Sun Microsystems' distribution of Apache Derby
sun-java6-jdk - Sun Java(TM) Development Kit (JDK) 6
sun-java6-jre - Sun Java(TM) Runtime Environment (JRE) 6 (architecture independent files)
sun-java6-source - Sun Java(TM) Development Kit (JDK) 6 source files
cacao-oj6-jdk - OpenJDK Development Kit (JDK)
cacao-oj6-jre - OpenJDK Java runtime, using CacaoVM JIT
cacao-oj6-jre-headless - OpenJDK Java runtime, using CacaoVM JIT (headless)

```

And I just got ubuntu so whatever the newest version is.

---

### Post by semi_fiction on 2009-01-04
I can't think of why it wouldn't be displayed in Synaptic, all i had to do was scroll down a few lines. (see image)

---

### Post by Ahadiel on 2009-01-04
> **newb austin said:**
> This is what I got when I did that
```
default-jdk - Standard Java or Java compatible Development Kit
default-jre - Standard Java or Java compatible Runtime
default-jre-headless - Standard Java or Java compatible Runtime (headless)
openjdk-6-jdk - OpenJDK Development Kit (JDK)
openjdk-6-jre - OpenJDK Java runtime, using Hotspot JIT
openjdk-6-jre-headless - OpenJDK Java runtime, using Hotspot JIT (headless)
ia32-sun-java6-bin - Sun Java(TM) Runtime Environment (JRE) 6 (32-bit)
sun-java6-bin - Sun Java(TM) Runtime Environment (JRE) 6 (architecture dependent files)
sun-java6-demo - Sun Java(TM) Development Kit (JDK) 6 demos and examples
sun-java6-doc - Sun JDK(TM) Documention -- integration installer
sun-java6-fonts - Lucida TrueType fonts (from the Sun JRE)
sun-java6-javadb - Java(TM) DB, Sun Microsystems' distribution of Apache Derby
sun-java6-jdk - Sun Java(TM) Development Kit (JDK) 6
sun-java6-jre - Sun Java(TM) Runtime Environment (JRE) 6 (architecture independent files)
sun-java6-source - Sun Java(TM) Development Kit (JDK) 6 source files
cacao-oj6-jdk - OpenJDK Development Kit (JDK)
cacao-oj6-jre - OpenJDK Java runtime, using CacaoVM JIT
cacao-oj6-jre-headless - OpenJDK Java runtime, using CacaoVM JIT (headless)

```

And I just got ubuntu so whatever the newest version is.

Please paste your /etc/apt/sources.list

---

### Post by newb austin on 2009-01-04
> **Ahadiel said:**
> Please paste your /etc/apt/sources.list

I think this is what you wanted

```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
```

---

### Post by Ahadiel on 2009-01-04
Strange... because sun-java6-plugin IS in multiverse which you have enabled.

[http://us.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-plugin_6-10-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-plugin_6-10-0ubuntu2_i386.deb)

Edit: Ignore this post for now, you have x86_64 not i386.

---

### Post by newb austin on 2009-01-04
> **Ahadiel said:**
> Strange... because sun-java6-plugin IS in multiverse which you have enabled.

[http://us.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-plugin_6-10-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-plugin_6-10-0ubuntu2_i386.deb)

Well I have 64 bit If that helps... What else can I do?

---

### Post by Ahadiel on 2009-01-04
You could try icedtea6-plugin
```
sudo apt-get install icedtea6-plugin
```

---

### Post by newb austin on 2009-01-04
> **Ahadiel said:**
> You could try icedtea6-plugin
```
sudo apt-get install icedtea6-plugin
```


Alright its installed now, but what exactly is it??

---

### Post by Ahadiel on 2009-01-04
Web browser java plugin based on openjdk IIRC.

---

### Post by newb austin on 2009-01-04
> **Ahadiel said:**
> Web browser java plugin based on openjdk IIRC.

It worked I LOVE YOU. Lol Just kidding. That was creepy I am just happy. Thank you so much.

---

### Post by Ahadiel on 2009-01-04
/me points towards the thanks button. Glad to see you got it working.

---

