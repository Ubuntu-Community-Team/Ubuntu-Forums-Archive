---
title: "creating a local package archive from main repository"
date: 2006-08-25
forum: Desktop Environments
---

### Post by summersab on 2006-08-25
OK, here is what I want to do. I have picked the source code of Easy Ubuntu and Automatix apart and found a list of general purpose packages that every Ubuntu computer should have by default. My original idea was to write a simple script with sudo apt-get install <massive list of packages>. Then I got to thinking - that takes a long time. Couldn't I just download the files to a flash drive, write a dpkg script, and install them whenever I set up a computer? That sounds great, but I have a small problem. How do I easily download all of those packages? Can I apt-get *NOT* install <long list of packages> to a location? Wget requires a specific location, and I'd rather not dig for every package I need. Thanks for your help. If you need a list of the packages I want to install, I can post it - it's just rather extensive.

---

### Post by meng on 2006-08-25
Try this
sudo apt-get -d install ...
this downloads the packages only.

---

