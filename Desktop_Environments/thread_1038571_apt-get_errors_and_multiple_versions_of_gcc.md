---
title: "apt-get errors and multiple versions of gcc"
date: 2009-01-12
forum: Desktop Environments
---

### Post by davidvandebunte on 2009-01-12
I am currently having trouble with my apt-get program.  Whenever I start my computer a notification at the top says:

"A problem occurred when checking for the updates."

Where it would normally get updates for me (open synaptic package manager).  Looking at other threads I believe it may be because of multiple versions of gcc I have around (I was making a gcc cross-compiler).  When I try to run apt-get I get the following error:

davidvandebunte@djv-1501-ibex:~$ apt-get
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.8-6.so.4.6)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.8-6.so.4.6)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.8-6.so.4.6)
apt-get: relocation error: /usr/lib/libapt-pkg-libc6.8-6.so.4.6: symbol _ZSt16__ostream_insertIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_PKS3_i, version GLIBCXX_3.4.9 not defined in file libstdc++.so.6 with link time reference

And this might be relevant, I wish I knew why:

davidvandebunte@djv-1501-ibex:~$ ldconfig -p | grep libstdc++
	libstdc++.so.6 (libc6) => /usr/local/lib/libstdc++.so.6
	libstdc++.so.6 (libc6) => /usr/lib/libstdc++.so.6
	libstdc++.so (libc6) => /usr/local/lib/libstdc++.so
davidvandebunte@djv-1501-ibex:~$ cat /etc/ld.so.conf.d/libc.conf
# libc default configuration
/usr/local/lib

Thanks for any help you can give, or adding anything you understand of what is going on here.

---

### Post by bezenadam on 2009-04-25
please help i have the same problem! i am worried my system has crashed, apt-get doesn't work in any way and i can't see my desktop icons!!!

---

