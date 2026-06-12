---
title: "problem with installing pakages"
date: 2009-05-16
forum: General Help
---

### Post by i.arnav on 2009-05-16
i am using Ubuntu 8.10

few days back while installing a pakage java6-docs from synaptic package manager, it said ur pakage has crashed

now i am not able to install any package from that day

it gets downloaded bt during installation it says:
This package is an installer package, it does not actually contain the JDK documentation. You will need to go and download one of the archives

jdk-6-doc.zip jdk-6-doc-ja.zip

(choose non updated version if its the first time)

Please visit
              [http://java.sun.com/javase/downloads](http://java.sun.com/javase/downloads)

and download
The file should owned by root.root and be copied to/tmp

plz help

---

### Post by cariboo on 2009-05-16
You can either go to System-->Administration-->Synaptic Package Manager-->Edit-->Fix Broken Packages, or open an Applications-->Accessories-->Terminal and type:

```
sudo apt-get -f install
```

to repair your problem.

---

### Post by i.arnav on 2009-05-17
no its not working writing this in terminal shows the same msg again

---

