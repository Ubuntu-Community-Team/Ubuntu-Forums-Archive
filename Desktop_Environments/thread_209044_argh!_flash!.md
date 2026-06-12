---
title: "argh! flash!"
date: 2006-07-04
forum: Desktop Environments
---

### Post by rkakkar on 2006-07-04
i have installed swiftfox 1.5.0.4 and initially i let it installed flash automatically. that failed. then i installed flash using the method specified in the starter guide:

```
$ sudo apt-get install flashplugin-nonfree;sudo update-flashplugin
```

that failed. help!

---

### Post by jvictor on 2006-07-04
Download the file from the website,

run it as sudo and install it into the plugins dir where firefox/swiftfox is installed

---

### Post by aysiu on 2006-07-04
When you say "that failed," is there an error message that goes along with it?

Do you have the Multiverse repositories enabled? What's the semi-colon doing in there?

---

### Post by kpkeerthi on 2006-07-04
```
What's the semi-colon doing in there?
```
He's running two commands in one command line.

@rkakkar
As for the flash plugin, you are better off with the one available in [www.adobe.com](www.adobe.com). Make sure you remove any residues of the plugin from your disks (aptitude purge) and install from adobe's website. You will be glad you did it.... no more crashes.

---

### Post by rkakkar on 2006-07-04
downloaded from adobe and that worked like a beaut!! :).. really fast too! thanks!

---

