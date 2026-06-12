---
title: "libfreetype6-dev broken packages in feisty"
date: 2007-08-10
forum: Desktop Environments
---

### Post by yoburtu on 2007-08-10
Hello,

I've a problem installing libfreetype6-dev in Feisty. There are broken packages:

$ sudo apt-get install libfreetype6-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libfreetype6-dev: Depends: libfreetype6 (= 2.2.1-5ubuntu1) but 2.2.1-5ubuntu1.1 is to be installed
E: Broken packages

What's the problem?.

Best regards.

---

### Post by PaulFr on 2007-08-11
Did you first run ```
sudo apt-get update
``` to get the latest package definitions ? On my system, libfreetype6-dev points to 2.2.1-5ubuntu1.1 and not 2.2.1-5ubuntu1, so maybe your package definitions are old.

---

