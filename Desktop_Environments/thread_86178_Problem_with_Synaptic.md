---
title: "Problem with Synaptic"
date: 2005-11-04
forum: Desktop Environments
---

### Post by Effect on 2005-11-04
Okay, basicly what I did was install the preview version of 5.10 since the version I downloaded of the final release wasn't working. I did the updates. Now trying to go into Synaptic I got the following when I started up. Once that was shown I clicked okay and then the program loaded. Now I didn't do anything after that but I want to know if there is a way to fix this?

Is the OS still considered it the preview released even after all the updates?

Thanks.

> W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Preview%20i386%20(20050908)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Preview%20i386%20(20050908)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by Ampersand on 2005-11-04
When you see a message like that, you just need to press the Reload button at the top of Synaptic to correct it. Once you've got all the updates, it's the same as the final release version.

---

### Post by aysiu on 2005-11-04
I'm seeing a lot of us.archives in there.
Try following these instructions to get a more up-to-date sources.list:
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

