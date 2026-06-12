---
title: "Kylix Libraries ??"
date: 2008-12-29
forum: General Help
---

### Post by Jontyy on 2008-12-29
i have downloaded 3 files off rapidshare and they need to be joined using hjsplit, to use hjsplit i need to install kylix libraries.

i am having difficulties installing them.

could somebody please run me through how.

cheers

---

### Post by Jontyy on 2008-12-29
nobody know?

---

### Post by nazrysamaratin on 2009-01-29
> **Jontyy said:**
> nobody know?
HJSplit Files Joiner/Splitter

HJSplit for Linux (Java version).

    * Make sure you have Java Runtime Environment installed: 

sudo apt-get install sun-java6-jre

    * Download the HJSplit JAR file: 

wget [http://www.freebyte.com/download/hjsplit/hjsplit_g.jar](http://www.freebyte.com/download/hjsplit/hjsplit_g.jar)

    * Create the directory for HJSplit: 

sudo mkdir /opt/hjsplit

    * Move the file to an appropriate directory: 

sudo mv hjsplit_g.jar /opt/hjsplit/ 

    * Run: 

cd /opt/hjsplit/ && java -jar hjsplit_g.jar 

    Note: You could also make a terminal shortcut (menu item) in K Menu Editor. 

[edit]

---

### Post by mister_playboy on 2009-05-30
Thank you for the instructions!  Works perfectly.

---

