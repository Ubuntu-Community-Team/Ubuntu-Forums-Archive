---
title: "NVIDIA Linux drivers version 1.0-8174 (nvidia-glx)"
date: 2005-12-26
forum: Deferred/Invalid Requests
---

### Post by F for Fragging on 2005-12-26
I consider this an essential backport, especially because:

# Added support for NVIDIA SLI. Please see the README for details.
# Added support for new GeForce 6100, GeForce 6150 and GeForce 7800 GTX 512.

Currently if you'd have a brand new system with one of these video cards, you'd have no 3D acceleration support because the drivers in Ubuntu's repo are lagging behind. You'd have to wait half a year for the next Ubuntu release or run the development branch before you can use 3D acceleration. IMO this is a serious problem. I have also filed a bug report on this issue a while ago - [http://bugzilla.ubuntu.com/show_bug.cgi?id=20682](http://bugzilla.ubuntu.com/show_bug.cgi?id=20682) - but there has been no response. I hope the backports people could be more helpful.

Newer version of nvidia-glx is in Dapper: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nvidia-glx&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nvidia-glx&searchon=names&subword=1&version=all&release=all)  this is version 1.0-8174, NVIDIA released 1.0-8178 on 22 December. See [http://www.nvidia.com/object/linux_display_archive.html](http://www.nvidia.com/object/linux_display_archive.html) for details.

Support for the latest video cards is such an essential feature which should justify a backport. Since the drivers are a kernel module, it could easily be compiled against the kernel available in Breezy, and thus be easily backported, am I correct?

---

### Post by veloct on 2005-12-26
You could also install the driver yourself. There are entries in the forums here on installing the latest ATI and Nvidia drivers in Breezy.

---

### Post by F for Fragging on 2005-12-26
Sure I can, but using NVIDIA's installer is too difficult and user-unfriendly. We should be able to get the latest drivers from the repository, without having to study a complete HOWTO - [http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074) - and having to edit config files.

---

### Post by jdong on 2006-01-02
Kernel module backports are not done; I've addressed this a few times before, also.

---

### Post by idn on 2006-01-07
I think this is pretty important, as it is now I cant use my card out the box I have to install the drivers manually which kind of sucks, and I agree the install is unusable to novice users.

---

### Post by jdong on 2006-01-07
What may fix your card will break many other people's, until the hardware specific compatibility issues with the 8174 series are fixed. I cannot afford to let that happen.

---

### Post by poofyhairguy on 2006-01-07
[QUOTE=F for Fragging]Sure I can, but using NVIDIA's installer is too difficult and user-unfriendly.[/QUOTE]

Not really. You would think so, but its not that bad. Just follow the guide:

[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

You are going to have to do it yourself- Jdong can't mess with anything that deals with the kernel. Its up to you!

---

### Post by David Jaša on 2006-02-01
[QUOTE=F for Fragging]Sure I can, but using NVIDIA's installer is too difficult and user-unfriendly. We should be able to get the latest drivers from the repository, without having to study a complete HOWTO - [http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074) - and having to edit config files.[/QUOTE]

I agree with this opinion - I've installed a breezy on offline box recently and it was a horror because
[LIST]
[*]no backported drivers were available
[*]not everything necessary to build it myself is included (AFAIK)
[*]nVidia isn't able/doesn't want to make VESA-compliant chip and CRT screen run in 60 Hz only.
[/LIST]

Isn't possible to make a separate package for new drivers as is nvidia-*-legacy for old?

---

### Post by tseliot on 2006-02-01
[QUOTE=jdong]Kernel module backports are not done; I've addressed this a few times before, also.[/QUOTE]
**Jdong** I have a question for you:
Where can I find the documentation about how to make kernel modules from the Nvidia installer (in the way Ubuntu developers do it)?

I'm asking this because I would like to learn how to do that and maybe I could make a repository with the latest drivers.

Thanks

---

### Post by nocturn on 2006-02-01
[QUOTE=tseliot]**Jdong** I have a question for you:
Where can I find the documentation about how to make kernel modules from the Nvidia installer (in the way Ubuntu developers do it)?

I'm asking this because I would like to learn how to do that and maybe I could make a repository with the latest drivers.

Thanks[/QUOTE]

That would be cool!

---

### Post by jdong on 2006-02-01
First, be familiar with how Debian packages are made (dpkg-buildpackage, apt-get build-dep, etc).

Next, look at the linux-restricted-modules-2.6.12 source package. Also look at the nvidia-kernel-common source package. Both have to be updated with the latest NVidia driver. Work off Dapper's l-r-m-2.6.15 and nvidia-kernel-common packages as examples, but straight backporting would not work due to kernel module infrastructure changes.

**IMPORTANT**: Remember that upon any security updates released for the kernel, you must **IMMEDIATELY** recompile your nvidia packages against the new kernel headers, else you'll have hundreds (thousands, maybe even more) users with broken X configurations and a group of developers going after you!

---

