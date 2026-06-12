---
title: "alien package scrips"
date: 2006-07-26
forum: Desktop Environments
---

### Post by leb3000 on 2006-07-26
Should I use the --scripts option when convertin rpm to .deb using alien?

It sometimes warns me about this and I dont know whether to use scripts

thanks

---

### Post by aysiu on 2006-07-26
What's the point of the --scripts option?

---

### Post by leb3000 on 2006-07-26
it converts the scripts (unistall and install 1s?) to their .deb equivalents I think

---

### Post by aysiu on 2006-07-26
I've never used that parameter. I just do ```
sudo alien -i nameofpackage.rpm
``` and that converts the .rpm to .deb and installs the .deb... all with one command.

---

### Post by leb3000 on 2006-07-26
Yes, I never use the scripts command. However, I want to know what it is good for. I dont think alien would mention it while converting rpms if it wasnt at least relatively important

---

