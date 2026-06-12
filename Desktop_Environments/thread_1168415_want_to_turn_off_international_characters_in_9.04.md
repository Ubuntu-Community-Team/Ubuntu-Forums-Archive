---
title: "want to turn off international characters in 9.04"
date: 2009-05-24
forum: Desktop Environments
---

### Post by breree on 2009-05-24
Hello All,

I am running 9.04 inside of vmware server 2 which is running on windows xp. The problem I have is that at both the console and inside of gnome that my " ' and ` keys are being grabbed and are being used to create accented characters. This makes typing such quote characters difficult (have to type them twice). I have experimented with localisation settings, keyboard settings but can't get rid of this behavior. If I ssh in from my windows box it is ok - the problem is not apparent. 

I am not sure when this problem developed as I recently upgraded to 9.04 and I also upgraded from vmware player to vmware server. 

Thanks,
Brett

---

### Post by breree on 2009-05-26
The solution was simple - to run dpkg-reconfigure console-setup and choose a non-international keyboard.

Brett

---

