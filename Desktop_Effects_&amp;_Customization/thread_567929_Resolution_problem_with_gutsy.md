---
title: "Resolution problem with gutsy"
date: 2007-10-05
forum: Desktop Effects &amp; Customization
---

### Post by Gavbuntu on 2007-10-05
I have installed Gutsy and the only two resolutions it gives me are 640x480 and 800x600. How do I get higher resolution options?

Thanks
Gav

---

### Post by Faud on 2007-10-05
Check out this guide:

[https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28resolution%29](https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28resolution%29)

---

### Post by bigken on 2007-10-05
do have right drivers installed for your graphics card 
try this in a terminal 

sudo dpkg-reconfigure -phigh xserver-xorg

from you can select the correct driver and resolution size good luck :)

---

### Post by Gavbuntu on 2007-10-06
Thanks, it worked great.

---

