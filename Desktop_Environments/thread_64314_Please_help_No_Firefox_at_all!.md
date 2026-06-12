---
title: "Please help No Firefox at all!"
date: 2005-09-10
forum: Desktop Environments
---

### Post by srinath on 2005-09-10
I tried to update my Firefox from ..0.2 to ..0.6. It came up with an error "...returned error (1)" or something. Now, I do not have either of the versions. ANd Add or Remove Applications is not starting up and nor am I able to install the newer version through Synaptic. What should I do?

---

### Post by mlomker on 2005-09-10
You need to be more specific about what errors you are getting.  Look at the name of the package you are installing and then try it from the command line instead (close Synaptic first).

**sudo apt-get install packagename**

Then tell us what errors you get.

---

### Post by rafakl on 2005-09-10
First, edit you /etc/apt/sources.list file like this:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Second, do:

sudo apt-get update

Third, reinstall firefox from synaptic OR from apt-get.

The same thing happened to me because when i wanted to reinstall firefox Synaptic said that i was selecting a diferent package!!!  :-? 

But restarting solved my problem

---

### Post by srinath on 2005-09-11
I first ran an update. Then an upgrade. But Firefox was still at 1.0.2. Being new to this I got a little adventurous and decided to try 'my own' command. I typed in 'apt-get install firefox' and it said it cannot overwrite an extenstion packag which was also a part of Mozilla. Samething with Synaptic. Now, I do not have either of the versions. I tried a reinstall through Synaptic but it still did not work. I'll try reinstall trough the terminal!


This is the exact thing:
root@srinath:/home/srinath # apt-get install firefox
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  firefox-gnome-support latex-xft-fonts xprint
The following NEW packages will be installed:
  firefox
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 8956kB of archives.
After unpacking 25.3MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  firefox
Install these packages without verification [y/N]? y
Get:1 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main firefox 1.0.6-1ubuntu1~5.04ubp1 [8956kB]
Fetched 8956kB in 5m30s (27.1kB/s)

Preconfiguring packages ...
(Reading database ... 59763 files and directories currently installed.)
Unpacking firefox (from .../firefox_1.0.6-1ubuntu1~5.04ubp1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/firefox_1.0.6-1ubuntu1~5.04ubp1_i386.deb (--unpack):
 trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package mozilla-firefox
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_1.0.6-1ubuntu1~5.04ubp1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Thank you.

---

### Post by srinath on 2005-09-11
I fixed it! Thank you everyone!  :smile:

---

### Post by mlomker on 2005-09-12
[QUOTE=srinath]I fixed it! Thank you everyone!  :smile:[/QUOTE]

I'm glad that you got it.  It sounds like it wanted you to do an **apt-get remove** on the old package before installing the new one.  There is also a **dpkg -i --force-all** command that you can use to force overwritting a file, but removing the old package is always better if you can.

---

