---
title: "[SOLVED] Azureus without gcj"
date: 2007-04-26
forum: Desktop Environments
---

### Post by Kimos on 2007-04-26
I'm using a fresh install of 7.04 and am having zero problems with it so far. Great release! I installed Sun Java 1.5 through Synaptic and it seemed to install without a hitch.

I later used Synaptic to install the Azureus package which said it depends on a whole list of gcj packages and libraries. Fine, I add those and fire up Azureus. It loads but fails to run any torrents with an error saying that "Java version 1.4.2 is not supported" or something to that extent. I try to remove all of gcj so that the Sun 1.5 JVM becomes the default again and it tells me Azureus will also be removed.

Anyone know why Azureus depends on a JVM with which it is not compatible? Any idea how I can get past this (short of a non .deb/apt installation)?

---

### Post by taurus on 2007-04-26
What's the output of this command from a terminal?

```
java -version
```

---

### Post by Kimos on 2007-04-26
> **taurus said:**
> What's the output of this command from a terminal?

```
java -version
```

I'm not at the machine right now, but I was checking the versions as I went.

After I installed Azureus, it showed  gcj 1.4. When I removed gcj , and subsequently Azureus by dependency, through Synaptic  it showed Sun Java 1.5.

I'll post exact output later today.

Reading up on the package:
[http://packages.ubuntulinux.org/feisty/net/azureus](http://packages.ubuntulinux.org/feisty/net/azureus)

It shows it depends on either *[java-gcj-compat]("http://packages.ubuntulinux.org/feisty/interpreters/java-gcj-compat")*, which is probably what's pulling in all the gcj stuff, or the virtual package *[java2-runtime]("http://packages.ubuntulinux.org/feisty/virtual/java2-runtime")*. I know for sure that the *sun-java5-jre* installed which should provide the *java2-runtime* virtual package, but if it's not maybe that's the problem...

---

### Post by taurus on 2007-04-26
You need the actual java version from either Sun or Blackdown, not the gcj version.  Therefore, install one from synaptic and if "java -version" still shows the wrong version, then reconfigure java with

```
sudo update-alternatives --config java
```

---

### Post by Kimos on 2007-04-27
My resolution was to install Azureus through apt on the command line rather than through Synaptic. For some reason, it didn't require gcj as a dependency from there. Doesn't really make sense to me, but it worked... *shrug*

---

### Post by engla on 2007-04-27
aptitude-gcj is *recommended* by the package aptitude. the different apt frontends handle that differently by default, and sadly none of them dare to ask "The following packages are also recommended by *, install them [y/n]?:".

---

