---
title: "Getting wireless network up during boot"
date: 2005-12-11
forum: General Help
---

### Post by tkr7 on 2005-12-11
Hey!

I have Ubuntu 5.10 installed in my Fujitsu-Siemens Amilo Pro V2000 laptop. My primary network connection is wireless. The network itself works fine after I have enabled this Intel-made integrated card by command:
sudo modprobe fsam7400 radio=1

But there is this problem that I would like this to happen during the boot process so that I wouldn't have to allways do that manually and enter root's password everytime. And when system boots it tryes to synchronize its clock via Internet connection and this takes a lot of time before timeout. So I would like this command to be executed before this and after when network interface starts.

Any suggestions?

---

### Post by Mr_Smiley on 2005-12-11
Hello,

I don't know if this is any help but take a look at the file: /etc/modules
Add the module name you want to load automatically at boot in there and then run 
```
sudo depmod -a
``` should hopefully do what you are asking.

Hope that this helps. 
:)

---

### Post by tkr7 on 2005-12-11
Thank you a lot for your idea and time, but actually I managed to get it working by my own.

I found a script networking in /etc/init.d and modified it by hand. I placed this switcher-command in the end of start-section and another one where radio got value 0 in the end of stop-section. I tested that and it worked, but thanks for the help anyway.

---

### Post by emerick7 on 2005-12-11
yep... sudo depmod -a works!  I've been trying to get my wireless network to load at boot but wasn't successful until now... thanks Mr. Smiley!

---

### Post by Mr_Smiley on 2005-12-11
[quote=emerick7]yep... sudo depmod -a works! I've been trying to get my wireless network to load at boot but wasn't successful until now... thanks Mr. Smiley![/quote] 
Not a problem. :)
Glad to be of help.

---

