---
title: "How do I create shortcuts on the desktop?"
date: 2005-07-14
forum: Desktop Environments
---

### Post by Paul Panks on 2005-07-14
I just installed Firefox 1.0.5 but the link at the top, on the info bar, launches the older version. To load the newer version, I have to navigate to my home directory, to firefox-installer, and run Firefox.sh.

Paul

---

### Post by nemin on 2005-07-15
[QUOTE=Paul Panks]I just installed Firefox 1.0.5 but the link at the top, on the info bar, launches the older version. To load the newer version, I have to navigate to my home directory, to firefox-installer, and run Firefox.sh.[/QUOTE]
It's always better to use apt to install programs, so use `sudo apt-get install mozilla-firefox` to get the latest (Ubuntu) version of firefox. Thinks like desktop shortcuts etc. are automaticaly updated and old versions are removed.
When you really want to use the version of firefox you just installed, you should first remove the old version (like `sudo apt-get remove mozilla-firefox`) and re-create all links to firefox.

---

### Post by Noah0504 on 2005-07-15
[QUOTE=nemin]It's always better to use apt to install programs, so use `sudo apt-get install mozilla-firefox` to get the latest (Ubuntu) version of firefox. Thinks like desktop shortcuts etc. are automaticaly updated and old versions are removed.
When you really want to use the version of firefox you just installed, you should first remove the old version (like `sudo apt-get remove mozilla-firefox`) and re-create all links to firefox.[/QUOTE]
 Yes, but right now you can't get Firefox 1.0.5 through Synaptic.

---

### Post by nemin on 2005-07-15
[QUOTE=Noah0504]Yes, but right now you can't get Firefox 1.0.5 through Synaptic.[/QUOTE]
If that's true, I'd advice you to wait and use an older version...

---

### Post by uniko on 2005-07-15
Right click on the desktop, choose Create Launcher, fill in name etc. choose an icon. For the command: /home/firefox-installer/.firefox.sh 

That should do the trick.

---

