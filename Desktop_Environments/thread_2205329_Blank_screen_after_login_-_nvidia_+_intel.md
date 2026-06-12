---
title: "Blank screen after login - nvidia + intel"
date: 2014-02-13
forum: Desktop Environments
---

### Post by moreschi on 2014-02-13
Ubuntu 13.04. installed using wubi

acer aspire 5755g-941

intel i7 + nvidia geforce gt540M. nvidia optimus

After installing ubuntu, I realized the laptop gets too hot even when I'm not doing anything. I learned it was because the nvidia graphics card is on all the time and that its a drivers issue. After installing the drivers, I got the problem.

Problem: After system startup, I see the ubuntu logo fine and the login screen - nothing looks out of the ordinary. after logging in, all I have is the background (not a black screen). I can ctrl-alt-t to get a terminal and try to fix stuff through that. But there are no toolbars or icons or a desktop really. I got an error when trying to open firefox through the terminal but firefox started anyway. the error:

> (process:2385): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size=0' failed

I do not really care about using the nvidia graphics card when on ubuntu. I'm happy with completely disabling it and using only the intel integrated graphics card. at least for now.

What I tried:

I tried removing the nvidia graphics drivers using the command

> sudo apt-get purge nvidia-common nvidia-settings-319-updates nvidia-319-updates

I tried installing Bumblebee but I still get the problem.

output of lpsci | grep VGA is:
> 00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 540M] (rev ff)

output of apt-cache policy nvidia:
> nvidia:
Installed: (none)
Candidate: (none)
Version table:

Output of apt-cache police fglrx
> fglrx:
Installed (none)
Candidate: 2:13.200~beta-0ubuntu1~xedgers~raring2
Version table:
2:13.200~beta-0ubuntu1~xedgers~raring2 0
500 [http://ppa.lauchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.lauchpad.net/xorg-edgers/ppa/ubuntu/) raring/main amd64 Packages
2:9.010-0ubuntu3 0
500 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) raring/restricted amd64 Packages
500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring/restricted amd64 Packages

That's about it for the information I currently have, which I suspect is insufficient. I would appreciate if anyone here can help.

Thank you

---

### Post by moreschi on 2014-02-13
nvm, found the answer here

[http://askubuntu.com/questions/204428/unity-missing-cant-see-top-or-side-panels](http://askubuntu.com/questions/204428/unity-missing-cant-see-top-or-side-panels)

---

