---
title: "help with Ubuntu 11.10 lightdm?"
date: 2011-10-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jeggy on 2011-10-15
i've installed the nvidia driver in ubuntu 11.10 and i had to turn of lightdm and i did that by writing 'sudo stop lightdm' and then i installed the driver successfully, but now i don't know how to start the lightdm again or how i can come to the desktop again.

i have tried 'sudo start lightdm' but it's getting stuck at 'logmein-hamachi' don't know why it has to load hamachi to get to the desktop... 

any solutions?

---

### Post by mikewhatever on 2011-10-15
You really didn't have to download the driver, then stop lighdm, then install. The process in Ubuntu is fully automated, point and click easy peasy. Just click the prompt to install additional drivers, wait and reboot.
Here is the howto for reference:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Anyway, since you've gone the hard route, I think the command you need to use is
**sudo service lightdm start**

---

