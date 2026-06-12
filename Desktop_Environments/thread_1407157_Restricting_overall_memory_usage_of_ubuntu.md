---
title: "Restricting overall memory usage of ubuntu"
date: 2010-02-14
forum: Desktop Environments
---

### Post by voncloft on 2010-02-14
I have 4 gb of ram for usage, however I want one process to always have access to atleast 2 gb - VirtualBox.

Is there a way for ubuntu to stop using all 4 gb and I mean the entire OS, and then have those other 2 gb available strictly and only for VirtualBox and linux can never go over 2 gb but still have 2 gb free of ram?

---

### Post by jken146 on 2010-02-15
RAM will free up as and when it's needed.

---

### Post by NightwishFan on 2010-02-15
I never heard of a way to do so, but unless you are running a lot of programs you will probably not use up 4gb. Personally I configure my system to swap often to leave more active parts of programs in RAM, however I have very low memory compared to you.

---

### Post by mcduck on 2010-02-15
> **voncloft said:**
> I have 4 gb of ram for usage, however I want one process to always have access to atleast 2 gb - VirtualBox.

Is there a way for ubuntu to stop using all 4 gb and I mean the entire OS, and then have those other 2 gb available strictly and only for VirtualBox and linux can never go over 2 gb but still have 2 gb free of ram?

VirtualBox (or any other virtual machine app) will automatically take the amount of RAM you have set your virtual system to have available. So you really don't need to do anyhting to accomplish this. Just set your virtual machine to have 2GB of memory and the momet you start it 2GB of RAM will be assigned to that process.

(there is no sense in restricting the RAM to some app if that app is not running, unused RAM wil not increase your system's performance, quite the opposite, as long as there is enough RAM that can be freed if some process needs it.)

---

