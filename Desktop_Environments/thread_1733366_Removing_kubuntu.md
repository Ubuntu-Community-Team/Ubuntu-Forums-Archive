---
title: "Removing kubuntu"
date: 2011-04-19
forum: Desktop Environments
---

### Post by Rennonz on 2011-04-19
I installed kubuntu through the synaptic package manager to try it however now I want to remove it, I can't. I followed the guide here ([http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)) but all I get is this-

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libaccess-bridge-java : Depends: default-jre but it is not going to be installed or
                                  openjdk-6-jre but it is not going to be installed or
                                  sun-java6-jre but it is not installable
E: Broken packages
```

Can anyone help?

---

### Post by daxbau on 2011-04-19
try to remove the packages libaccess-bridge-java and libaccess-bridge-java-jni first then run the command like in your link, but don't forget to reinstall it afterwards.
may it helps:D

---

