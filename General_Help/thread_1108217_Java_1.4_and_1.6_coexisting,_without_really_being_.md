---
title: "Java 1.4 and 1.6 coexisting, without really being installed"
date: 2009-03-27
forum: General Help
---

### Post by cbruce8 on 2009-03-27
Had 2 separate devices that required two separate versions of java (javaws).
I fixed the problem by creating a launcher that referenced javaws in each
respective version folder.

However, I have no idea why it works, as java -version, synaptic version pkg mgr, and dpkg all show no java installed.

Just curious,
-charlie

---

### Post by jespdj on 2009-03-27
How did you install Java? Did you install it the normal way (from the Ubuntu repository: using apt-get or Synaptic), or did you download and install them manually?

If you installed them manually, then Synaptic and dpkg won't know they are installed, and you probably didn't add the directory that contains the Java launcher to your executable search path.

---

### Post by cbruce8 on 2009-03-30
Did apt-get , installed ok, but didn't work correctly. -Uninstalled, did
synaptic, installed ok, but didn't work properly.
Didn't work properly means update-java-alternatives -s java-1.5.0-sun
update-java-alternatives -s java-6-sun did not change the version that
ran.
But thanks for your suggestion,
-charlie

---

