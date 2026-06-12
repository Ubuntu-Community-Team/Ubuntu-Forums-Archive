---
title: "vmware kernel headers for &quot;2.6.24-24&quot;"
date: 2009-05-06
forum: General Help
---

### Post by psyncho on 2009-05-06
Hi, 

I've had the same problem described and solved here: 
[http://ubuntuforums.org/showthread.php?t=239232](http://ubuntuforums.org/showthread.php?t=239232)

However the solution doesn't work for me (of course its 3 years later, so).

I'm trying to install vmware. The install script is asking for the location of c headers for the kernel. 

Results of uname -a are: 
2.6.24-24-server

At /usr/src I have: 
linux-headers-2.6.24-17          linux-headers-2.6.24-23
linux-headers-2.6.24-17-generic  linux-headers-2.6.24-23-generic
linux-headers-2.6.24-19          linux-headers-2.6.24-24
linux-headers-2.6.24-19-generic  linux-headers-2.6.24-24-generic
linux-headers-2.6.24-21          rpm
linux-headers-2.6.24-21-generic

There were first a few errors where the script specifically wanted to find the linux folder. I figured that out then... 

When I point the script at:
/usr/src/linux-headers-2.6.24-24/include

It says there is no version.h file. I found that file under the generic directory.

When I point the script at:
/usr/src/linux-headers-2.6.24-24-generic/include

Then it said it doesn't match my current running kernel. 

I've noticed there are a lot of symlinks in the generic folder linking back to the non-generic folder. 

In any case, I have no idea where to go from here. Any advice would be much appreciated. 

Regards, 
John

---

