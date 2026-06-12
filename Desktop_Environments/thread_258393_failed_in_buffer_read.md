---
title: "failed in buffer_read"
date: 2006-09-15
forum: Desktop Environments
---

### Post by tandre75 on 2006-09-15
I am having trouble installing updates using either the update manager or synaptic:
Two examples or the errors I am getting follow:
[I]E: /var/cache/apt/archives/automatix_6.5-1-6.06dapper1_i386.deb: failed in buffer_read(fd)

E: /var/cache/apt/archives/linux-image-2.6.15-26-386_2.6.15-26.47_i386.deb: failed in buffer_read(fd)[/I]

Any advice?

---

### Post by dmizer on 2006-09-26
i'll toss my hat in the ring for this one.  have a bit more information though.

there seems to be a problem with a couple packages:
gstreamer0.10-plugins-bad-multiverse and libxvidcore4

i figured i could remove the packages and reinstall them after the update so i just tried sudo aptitude remove libxvidcore4 and gstreamer0.10-plugins-bad-multiverse respectively, and wound up with this:
```
$sudo aptitude remove gstreamer0.10-plugins-bad-multiverse
The following packages are unused and will be REMOVED:
  libfaac0 libfaad2-0 libmp4v2-0 libxvidcore4
The following packages will be automatically REMOVED:
  gstreamer0.10-plugins-bad-multiverse 
The following packages have been kept back:
  firefox libnspr4 libnss3 mozilla-firefox 
The following packages will be REMOVED:
  gstreamer0.10-plugins-bad-multiverse libxvidcore4 
0 packages upgraded, 0 newly installed, 5 to remove and 4 not upgraded.
Need to get 0B of archives. After unpacking 2314kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... dpkg: error processing gstreamer0.10-plugins-bad-multiverse (--remove):
 failed in buffer_read(fd): files list for package `libxvidcore4': Invalid argument
Errors were encountered while processing:
 gstreamer0.10-plugins-bad-multiverse
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```
then it dumps me back to a prompt.

what gives?

---

