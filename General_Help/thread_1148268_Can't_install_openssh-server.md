---
title: "Can't install openssh-server"
date: 2009-05-04
forum: General Help
---

### Post by stefangr1 on 2009-05-04
I have just installed Ubuntu x64 8.04LTS

When I try to install openssh-server, I get the following error:

The following packages have unmet dependencies:
  openssh-server: Depends: openssh-client (= 1:4.7p1-8ubuntu1) but 1:4.7p1-8ubuntu1.2 is to be installed


Any ideas on how to solve this?

If I do apt-get remove openssh-client, apt sais it want's to remove ubuntu-desktop entirely, which doesn't seem like a good idea.

---

### Post by sahabcse on 2009-05-04
Open synaptic package manager and click the repository site from repository menu. then click reload. After that try to install the packages.

For more info click [here]("http://sahabm.blogspot.com/2009/01/package-management-debian-and-ubuntu.html")

---

### Post by stefangr1 on 2009-05-04
> **sahabcse said:**
> Open synaptic package manager and click the repository site from repository menu. then click reload. After that try to install the packages.

For more info click [here]("http://sahabm.blogspot.com/2009/01/package-management-debian-and-ubuntu.html")


I already tried this, it results in the same error message.

---

### Post by sahabcse on 2009-05-04
try

sudo apt-get purge openssh-server

sudo apt-get install openssh-client openssh-server

Paste the o/p of cat /etc/apt/sources.list

---

### Post by stefangr1 on 2009-05-04
> **sahabcse said:**
> try

sudo apt-get purge openssh-server

sudo apt-get install openssh-client openssh-server

Paste the o/p of cat /etc/apt/sources.list


That I also tried long before I posted here :( , the subsequent reinstall attempt gives the same error message. openssh-client is already installed by default, btw, so trying to install that again won't work.

I have solved it in the mean time by changing tot the intrepid repositories. That fixed it. It is however a very bad idea as it could easily break a system. I noticed that a bug has already been filed on this issue, as long as one year ago. The related dependencies are still broken, however.

I think by now that installing an "old" LTS version to get more reliability was a very, very bad idea...

---

