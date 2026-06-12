---
title: "Live CD build"
date: 2011-02-15
forum: Desktop Environments
---

### Post by dj07707 on 2011-02-15
Am working on a project where i create a custom live CD. This live CD when run on a system should mount any NTFS filesystems and write stuff to a directory on the ntfs filesystem, then reboot the system. 

Two issues am having.

1. First of all there should be no user input at all. Am using remastersys for my live CD. I have a ubuntu install with auto login, so basically you turn the system on and after a few seconds, the desktop is there, great. thats not the case for the live CD i created from my running system though.  When i create my live CD and run it, it doesnt auto login. it requires me to click my username to login, though it does not require a password. why is that?

2. Am able to mount my NTFS filesystem but am not able to write to it. I read somewhere live CDs dont allow you to write to other filesystems though they can see it. Any work around, suggestions? My script is being written in perl.

Any help will be great please. Thanks

---

### Post by dj07707 on 2011-02-16
OK so i figured the autologin issue out. 
I just need to be able to write to NTFS from a live CD.

---

