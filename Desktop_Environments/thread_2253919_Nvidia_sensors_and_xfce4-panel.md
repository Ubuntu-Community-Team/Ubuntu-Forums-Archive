---
title: "Nvidia sensors and xfce4-panel"
date: 2014-11-23
forum: Desktop Environments
---

### Post by Tares on 2014-11-23
Hello,

Is it possible to somehow add readings from my GTX970 to the xfce panel?

I have set up my CPU and SSDs temperatures using lm-sensors, but I don't know how to add GPU.

Thanks,
Tares

---

### Post by Toz on 2014-11-23
Unfortunately, the [default build]("https://launchpadlibrarian.net/140779264/buildlog_ubuntu-saucy-i386.xfce4-sensors-plugin_1.2.5-2_UPLOADING.txt.gz") of the the xfce4-sensors-plugin doesn't include the configuration option to display nvidia readings. You need to build the package with the "--enable-xnvctrl" configure parameter. There is a more detailed explanation of this [here]("https://forum.xfce.org/viewtopic.php?id=8903").

---

### Post by Tares on 2014-11-30
Thanks for the link. I have used the first method with xfce4-genmon-plugin. I've modified a little bit the script and it is working perfectly ;)

For future reference, below is the script I've used:
```
#!/bin/bash
nvidia-smi -q -d TEMPERATURE | grep "GPU Current" | cut -c39-40 | sed 's/$/*C/'
exit 0
```

Edit:
Just adding some extra script for the fan speed ;)
```
#!/bin/bash
nvidia-smi -q | grep Fan | cut -c39-40 | sed 's/$/%/'
exit 0
```

---

