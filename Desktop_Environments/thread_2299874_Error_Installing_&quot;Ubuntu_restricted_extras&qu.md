---
title: "Error Installing &quot;Ubuntu restricted extras&quot;"
date: 2015-10-22
forum: Desktop Environments
---

### Post by neel3 on 2015-10-22
I am getting this error while trying to install Ubuntu restricted extras:

> Failed to download package files
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/chromium-codecs-ffmpeg-extra_45.0.2454.85-0ubuntu0.14.04.1.1097_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/chromium-codecs-ffmpeg-extra_45.0.2454.85-0ubuntu0.14.04.1.1097_amd64.deb) 404  Not Found [IP: 91.189.91.24 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/oxide-qt/oxideqt-codecs-extra_1.9.1-0ubuntu0.14.04.2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/oxide-qt/oxideqt-codecs-extra_1.9.1-0ubuntu0.14.04.2_amd64.deb) 404  Not Found [IP: 91.189.91.24 80]


I wanted to install audio and video codecs.

System: Xubuntu on Crouton

---

### Post by deadflowr on 2015-10-22
Those packages have newer versions in the repos, so you need to update your package lists
```
sudo apt-get update
```
probably best to actually update the system as well
```
sudo apt-get upgrade
```
if the output shows for anything being held back, such as newer kernels run
```
sudo apt-get dist-upgrade
```
which will pull in the newer kernel.
Based on how new(or old) the chromium codecs package is, i'd definitely run the dist-upgrade command.
(Purely for security related reasons)

After the system is fully up-to-date, then try installing the restricted packages.

---

### Post by Bucky Ball on 2015-10-22
... and further to deadflowr's post, you are attemtping to install from the repositories using Synaptic or terminal?

---

### Post by neel3 on 2015-10-22
used Ubuntu Software Center.
works fine after the update.
thanks

---

### Post by Bucky Ball on 2015-10-22
Good news. Please see th first link in my signature and enjoy. :)

---

