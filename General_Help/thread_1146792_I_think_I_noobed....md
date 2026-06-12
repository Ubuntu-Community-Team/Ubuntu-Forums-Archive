---
title: "I think I noobed..."
date: 2009-05-02
forum: General Help
---

### Post by LT1Caprice57L on 2009-05-02
So I reverted to Firefox2 through a process of temporarilly converting to the Hardy repos temporarilly.  That went fine.

Here's the deal.  I went to remove FF3 (because I hate it, it's a buggy/resource-hogging piece of ****, I loved FF2 though) and well...I'll let this do the talking:
```
laptop:~$ sudo apt-get autoremove firefox-3.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
The following packages will be REMOVED:
  firefox firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support
  firefox-gnome-support linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
0 upgraded, 0 newly installed, 7 to remove and 5 not upgraded.
After this operation, 56.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 120680 files and directories currently installed.)
Removing firefox ...
Removing firefox-gnome-support ...
Removing firefox-3.0-gnome-support ...
Removing linux-headers-2.6.27-7-generic ...
Removing linux-headers-2.6.27-7 ...
Removing firefox-3.0 ...
Removing firefox-3.0-branding ...
laptop:~$
```

Out of habit I just typed Y and hit enter without reading. *facepalm*

So did I just delete my kernel or an essential part of it, and if so, what's done to get it back?

---

### Post by lisati on 2009-05-02
It's common for Ubuntu to keep a handful of old kernels around just in case something goes wrong while running newer ones and you need to go back. In the absence of evidence to the contrary, I suspect that you're probably safe.

---

### Post by s3a on 2009-05-02
Are you experiencing anything bad or were you just concerned by what the terminal told you?

---

### Post by Locutus_of_Borg on 2009-05-02
does the command 'uname -r' output "2.6.27-7-generic"?

if so, you will need to reinstall your headers by means of apt-get install linux-headers-2.6.27-7-generic

if not, it is safe to ignore assuming you do not intend to use the old kernel or have need for the kernel headers which is used for such things as compiling source, etc.

---

### Post by LT1Caprice57L on 2009-05-03
Thanks guys.  I forgot that it updated to -11 awhile back, so -7 sat unused.

---

