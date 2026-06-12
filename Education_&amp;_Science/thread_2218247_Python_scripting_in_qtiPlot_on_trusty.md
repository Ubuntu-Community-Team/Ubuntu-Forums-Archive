---
title: "Python scripting in qtiPlot on trusty"
date: 2014-04-20
forum: Education &amp; Science
---

### Post by vanili on 2014-04-20
Hello to everyone.

Yesterday I've changed the system to Ubuntu 14.04 and observed that Python scripting stopped to work in the qtiPlot (0.9.8.9 svn 2288) installed from the repository. It shows a message "Fail to export qtiplot API", and  after "can bot locate python configuration file", when I try to change scripting language to Python.

I checked the qtiPlot documentation, it is written there that Qt, SIP and PyQt should be installed. I've installed Qt-SDK from repository and compiled sip-4.15.5, PyQt-x11-gpl-4.10.4. After this qtiPlot crushes with segmentation fault after "Fail to export qtiplot API".

Does anyone know how to solve it? Description for qtiplot packet on trusty says that it has full python scripting support, but how to get it?

---

### Post by vanili on 2014-04-24
solved.

See [https://bugs.launchpad.net/ubuntu/+source/qtiplot/+bug/1311721](https://bugs.launchpad.net/ubuntu/+source/qtiplot/+bug/1311721)

---

