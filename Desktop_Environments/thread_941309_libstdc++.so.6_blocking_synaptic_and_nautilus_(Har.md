---
title: "libstdc++.so.6 blocking synaptic and nautilus (Hardy Heron)"
date: 2008-10-08
forum: Desktop Environments
---

### Post by dandellion on 2008-10-08
Hardy Heron, Gnome

I did a regular update this morning and everything seemed fine. But during the afternoon all the icons from the desktop disappeared. Panels are working fine. 

I can's start nautilus (which explains dead desktop). If I try to start it from console it refuses: 
> nautilus: /lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/libexempi.so.3)

Synaptic in the tray is red circle saying that there was a problem when checking for the updates. Also Synaptic won't start from the console: 
> synaptic: /lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by synaptic)
synaptic: /lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
synaptic: /lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/libapt-inst-libc6.7-6.so.1.1)

Help, please.

---

### Post by dandellion on 2008-10-08
I think I made it....

Library was there all the time, but symlinks were messed. 
According to [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=914618](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=914618)
I did ```
export LD_LIBRARY_PATH=/usr/lib/:${LD_LIBRARY_PATH}
``` but that solves problem only terporarily and workis only for user not for the root.

So I did [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/180160](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/180160)
> 
$ ldconfig -p |grep libstdc++

         libstdc++.so.6 (libc6) => /usr/lib/libstdc++.so.6
         libstdc++.so.6 (libc6) => /usr/local/lib/libstdc++.so.6
$ diff /usr/lib/libstdc++.so.6 /usr/local/lib/libstdc++.so.6
   Binary files /usr/lib/libstdc++.so.6 and /usr/local/lib/libstdc++.so.6
differ
The two files are different which means there are two different versions gcc
in the system? I found a gcc directory under /usr/local

Then : $ cat /etc/ld.so.conf.d/libc.conf
# libc default configuration
/usr/local/lib

I added /usr/lib to the file and then run :
$sudo ldconfig

---

