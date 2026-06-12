---
title: "configure screen resolution"
date: 2006-02-16
forum: Desktop Environments
---

### Post by khateeb on 2006-02-16
Hi 

i ve just installed ubuntu on my new computer and the screen resolution is only 640*480. I ve tried to increase it from system -> preferences -> screen resolution but it shows that resolution as the only option.

i also tried reconfiguring xserver via

"dpkg-reconfigure xserver-xorg"

but it does not make a difference

kindly tell me how to increase the resolution

thnks

---

### Post by frodon on 2006-02-16
You need to add the horizontal and vertical refresh rate of your screen in the xorg.conf file to enable higher resolution if you have some problems with that. I give you a link where all is explained : [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

