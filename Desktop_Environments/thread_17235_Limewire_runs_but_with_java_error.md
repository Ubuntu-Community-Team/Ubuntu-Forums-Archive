---
title: "Limewire runs but with java error"
date: 2005-02-27
forum: Desktop Environments
---

### Post by yoha on 2005-02-27
I have been running Limewire for sometime now w/o any problem. today, i run the prog by typing it on the command line instead of "point n click" and terminal spits out this: 

java.io.FileNotFoundException: out.txt (Permission denied)
        at java.io.FileOutputStream.open(Native Method)
        at java.io.FileOutputStream.<init>(Unknown Source)
        at java.io.FileOutputStream.<init>(Unknown Source)
        at com.zerog.lax.LAX.setStdOutStdErr(Unknown Source)
        at com.zerog.lax.LAX.setStdOutStdErrOnSupportedPlatforms(Unknown Source)        at com.zerog.lax.LAX.<init>(Unknown Source)
        at com.zerog.lax.LAX.main(Unknown Source)
java.io.FileNotFoundException: err.txt (Permission denied)
        at java.io.FileOutputStream.open(Native Method)
        at java.io.FileOutputStream.<init>(Unknown Source)
        at java.io.FileOutputStream.<init>(Unknown Source)
        at com.zerog.lax.LAX.setStdOutStdErr(Unknown Source)
        at com.zerog.lax.LAX.setStdOutStdErrOnSupportedPlatforms(Unknown Source)        at com.zerog.lax.LAX.<init>(Unknown Source)
        at com.zerog.lax.LAX.main(Unknown Source)

The program runs of course like normally it does. But i am just curious as to why the java errors occur. any ideas? also as instructed on ubuntuguide.org, i installed LimeWire on /opt folder which belongs to the root and put the application launcher on the Internet menu. I am also curious as to why i am able to launch LimeWire without being prompted for passwd when it is obvious the prog belongs to root.
Thanks for any suggestions

Best Regards,
y0ha

---

