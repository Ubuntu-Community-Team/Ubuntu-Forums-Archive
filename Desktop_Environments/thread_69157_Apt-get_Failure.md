---
title: "Apt-get Failure"
date: 2005-09-25
forum: Desktop Environments
---

### Post by larry on 2005-09-25
Dear All,
I tried the usual apt-get update and apt-get upgrade on my system, but this time something went wrong when trying to update from the backports:

larry@hal:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  mozilla-firefox mozilla-firefox-gnome-support
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B/8856kB of archives.
After unpacking 24.7MB of additional disk space will be used.
Do you want to continue [Y/n]? Y

Preconfiguring packages ...
(Reading database ... 98690 files and directories currently installed.)
Preparing to replace mozilla-firefox 1.0.6-1ubuntu1~5.04ubp1 (using .../mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb) ...
Unpacking replacement mozilla-firefox ...
dpkg: error processing /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb (--unpack):
 trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace mozilla-firefox-gnome-support 1.0.6-1ubuntu1~5.04ubp1 (using .../mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb) ...
Unpacking replacement mozilla-firefox-gnome-support ...
dpkg: error processing /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in package firefox-gnome-support
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb
 /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Does anyone have a clue at what is going on? I have never had such a problem in the past.
Many thanks for your help
Larry

---

### Post by Perfect Storm on 2005-09-26
Try to install them each at the time. There can be some conflicts if some packages tries to write to same file or folder.

---

### Post by christooss on 2005-09-26
Open synaptic and uninstall the problematic packages. Than write down which packages will also get uninstalled.

Than install manualy every package which got uninstaled. That worked with me perfectly

---

### Post by larry on 2005-09-29
By manual install do you mean using the command line? If so, should I use dkpg?
Can you please simply send me the command I need to use? (I am not very experienced...).
Thanks a lot.
Larry

---

### Post by christooss on 2005-09-29
no I mean

sudo apt-get install......

And than packages which were uninstalled at 

>>>Open synaptic and uninstall the problematic packages. Than write down which packages will also get uninstalled.

---

