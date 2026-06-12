---
title: "Installing kubuntu-desktop in karmic replaces ubuntu usplash/xsplash theme"
date: 2009-11-21
forum: Desktop Environments
---

### Post by spirytusick on 2009-11-21
Hi,

I've installed Ubuntu 9.10 the other day and I am in the process of reinstalling my favourite apps. Few of them use KDE and have missing functionality (krusader for example) if only minimal kde dependencies are installed. 
I have installed the whole kubuntu-desktop but unfortunately, this has replaced boot time ubuntu logo with kubuntu progress bar (initially) then xsplash kicks in with the karmic brown themed loading indicator. Is there ar way of getting the original white ubuntu logo back instead of the kubuntu progress bar? 

Thanks in advance.

---

### Post by stuffystuff200681 on 2009-12-18
try
```
sudo apt-get install startupmanager
```

then go select "System-->Administration-->Startup Manager"

then change the usplash to the "ubuntu....."(don't know what it says after that) option

set it and have a nice day :popcorn:


---happy holidays---:guitar:

---

### Post by spirytusick on 2009-12-20
Thanks a lot, that did the trick. Happy holidays too! Btw, is there a way of getting grub to use non vesa resolutions ? eg, 1400x900 or will we have to wait for KMS?

---

