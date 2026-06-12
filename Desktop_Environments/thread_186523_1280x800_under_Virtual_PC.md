---
title: "1280x800 under Virtual PC"
date: 2006-06-02
forum: Desktop Environments
---

### Post by Oatmeat on 2006-06-02
I'm having trouble getting X to run in 1280x800 mode (running on Virtual PC). I've tried adding various things to my xorg.conf file, but none of them seem to have any luck. Is there something special I need to do since this is on Virtual PC?

Thanks.

---

### Post by Cemetric on 2006-06-02
Hey ... 

Maybe you can give [this site]("http://www.computernetworkinghelp.com/content/view/43/1/") a try ??

At the very least it will get you started in the right direction.

.C.

---

### Post by rcarring on 2006-06-02
MS Virtual PC has a feature that means it won't support 24bpp.

 I have MSVPC SP1 installed and when botting the Live CD, the display was unreadable at the provided resolution of 1024 x 768, I also got a message to say that my monitor could not display the chosen guest resolution and that was why the VM was running in a window. This is a known feature of MSVPC.

This is the wiki page:

[https://wiki.ubuntu.com/HowToConfigureUbuntuForMicrosoftVirtualPC2004?highlight=%28pc%29%7C%28virtual%29](https://wiki.ubuntu.com/HowToConfigureUbuntuForMicrosoftVirtualPC2004?highlight=%28pc%29%7C%28virtual%29)

Hope this helps

---

### Post by Oatmeat on 2006-06-02
I've looked at both of the above links, but unfortunetly neither has helped. I'm already running at a color depth of 16 and no modeline additions seem to have any effect on this problem. Thanks though.

---

### Post by Oatmeat on 2006-06-02
I solved the issue by changing the driver from "vesa" to "s3". Thanks again for the help.

---

