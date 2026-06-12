---
title: "CUDA 7 unmet dependencies [HELP A NOOB, PLEASE]"
date: 2015-06-04
forum: Gaming &amp; Leisure
---

### Post by Otto_Neres on 2015-06-04
Hello,

I recently installed the driver related to my gtx760 but Blender wasn't recognizing my GPU so that I could use the CUDA to render. And dota 2 was awfully slow.
So I decided the problem was the CUDA drivers which weren't installed.
I went to their website and download the CUDA 7 craziness. But now there seems to be a conflict between nvidia-opencl-icd-346 and nvidia-opencl-icd-331.
I am using Ubuntu 14.04 and I need 

otto@OttoPCUbuntu:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of cuda-drivers:
 cuda-drivers depends on nvidia-opencl-icd-346 (>= 346.46); however:
  Package nvidia-opencl-icd-346 is not installed.

dpkg: error processing package cuda-drivers (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cuda-runtime-7-0:
 cuda-runtime-7-0 depends on cuda-drivers (>= 346.46); however:
  Package cuda-drivers is not configured yet.

dpkg: error processing package cuda-runtime-7-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cuda-7-0:
 cuda-7-0 depends on cuda-runtime-7-0 (= 7.0-28); however:
  Package cuda-runtime-7-0 is not configured yet.

dpkg: error processing package cuda-7-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cuda:
 cuda depends on cuda-7-0 (= 7.0-28); however:
  Package cuda-7-0 is not configured yet.

dpkg: error processing package cuda (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cuda-drivers
 cuda-runtime-7-0
 cuda-7-0
 cuda

********** So I try sudo apt-get install nvidia-opencl-icd-346   (since the previous command told me it is not installed and it might be the thing causing errors), then I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  calligra-l10n-pt calligra-l10n-ptbr kde-l10n-pt kde-l10n-ptbr
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  nvidia-opencl-icd-346
0 upgraded, 1 newly installed, 0 to remove and 24 not upgraded.
4 not fully installed or removed.
Need to get 7.829 kB of archives.
After this operation, 26,5 MB of additional disk space will be used.
Get:1 [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/) trusty/main nvidia-opencl-icd-346 amd64 346.72-0ubuntu0~xedgers14.04.2 [7.829 kB]
Fetched 7.829 kB in 27s (281 kB/s)                                             
(Reading database ... 225043 files and directories currently installed.)
Preparing to unpack .../nvidia-opencl-icd-346_346.72-0ubuntu0~xedgers14.04.2_amd64.deb ...
Unpacking nvidia-opencl-icd-346 (346.72-0ubuntu0~xedgers14.04.2) ...
dpkg: error processing archive /var/cache/apt/archives/nvidia-opencl-icd-346_346.72-0ubuntu0~xedgers14.04.2_amd64.deb (--unpack):
 trying to overwrite '/etc/OpenCL/vendors/nvidia.icd', which is also in package nvidia-opencl-icd-331 331.113-0ubuntu0.0.4
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-opencl-icd-346_346.72-0ubuntu0~xedgers14.04.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



I tried a bunch of solutions online, but none of them worked. Could anyone help me? Please, I really need this, because now Ubuntu won't let me install any new software!!
P.S.: I even tried uninstalling cuda 7 in order to reinstall but ubuntu won't let me uninstall either, displaying the same "unmet dependencies" error

Thank you in advance,

---

### Post by efflandt on 2015-06-05
You should only have 1 version of video drivers installed at a time. You apparently have both nvidia-331 and nvidia-346 installed, sort of, partially. You should totally purge one of those if you expect the other one to work properly. But I cannot help you with CUDA because I have not used that.

---

