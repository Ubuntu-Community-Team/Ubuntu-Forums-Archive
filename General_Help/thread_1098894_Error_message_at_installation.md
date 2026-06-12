---
title: "Error message at installation"
date: 2009-03-17
forum: General Help
---

### Post by OldGrey on 2009-03-17
Hi, I recently reinstalled Ubuntu 8.10 amd64. All went well except that after I had downloaded the and installed the updates, just at the end of the process, I got an error message which I now get whenever I install a new program or any updates:

```
Errors were encountered while processing:
 system-tools-backends
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up system-tools-backends (2.6.0-1ubuntu1.1) ...
 * Starting System Tools Backends system-tools-backends
invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
```

On the one hand it does not seem to affect the installation, but I do not understand what the problem is. Can anyone help and suggest a solution?

---

### Post by LegendofTom on 2009-03-17
Looks like dpkg had a problem with installing system-tools-backends.  If you want it now, you can try:
```
sudo apt-get -f install system-tools-backend
sudo apt-get update
```

---

### Post by OldGrey on 2009-03-17
Thank you for the suggestion. However all I got was:

```
E: Couldn't find package system-tools-backend
```

---

### Post by fieroboom on 2009-03-19
> **LegendofTom said:**
> Looks like dpkg had a problem with installing system-tools-backends.  If you want it now, you can try:
```
sudo apt-get -f install system-tools-backend
sudo apt-get update
```

This is a typo. There is an 's' on the end of the word 'backend':

```
sudo apt-get -f install system-tools-backends
sudo apt-get update
```

:D
-Paul

---

