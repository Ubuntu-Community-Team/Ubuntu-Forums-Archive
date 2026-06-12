---
title: "Installing Sun jdk for java 6 in ubuntu 9.04"
date: 2009-05-16
forum: General Help
---

### Post by greytooth898 on 2009-05-16
I cannot get Sun jdk with java 6 installed.  Whenever i finally get the install manager to install, it fails and tells me that i have "aptitude" "synaptic" or something else active and that i cant install with these open. can anyone help?

---

### Post by MeLight on 2009-05-16
What command are you running to install it?

---

### Post by ajgreeny on 2009-05-16
Make sure that none of the applications that use apt (synaptic, aptitude, update-manager) are not running, by looking in system-monitor, and closing them if they are.  Then open synaptic, search for sun-java, find the -jdk in the list that appears and mark it to install.  It should be as simple as that.  You can not have any of those applications open or working, as well as trying to use apt-get.  Choose just one method and it should work without problem.

---

