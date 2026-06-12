---
title: "Update from 8.10 to 9.04, resolution messed up"
date: 2010-04-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kamohammed on 2010-04-03
I was updating from version 8.10 to 9.04
going good so far untill a prompt came up asking something bout another display (gaah.. cant remember now) anyways... i said yes then my screen went haywire... as if it was in a resolution my screen couldnt handle... it froze there for quite a while until i decided to force reboot (yeah... bad idea)... every boot now the resolution is awesomely messed up. Doing recovery mode doesnt help... even editing the /etc/X11/xorg.conf file adding subsection display and modes "1440x900" doesnt help...

any ideas?

i think i may have to re-install as update wasnt completed

ps: if i download the 9.04 ISO can i do a repair via cd (similar to how windowsXP has it?)

---

### Post by kamohammed on 2010-04-03
great... now nothing comes up at normal boot... #-o 
...medic....

---

### Post by kamohammed on 2010-04-04
ok fixed... kinda...

i did... 

 sudo *do*-release-*upgrade*

and updated to 9.10... sort of fixed everything... however, i got the common laggy animation crap now...

---

### Post by duanedesign on 2010-04-04
As a new feature in 9.10, xorg.conf is optional and not included by default. Apparently, xorg has become smart enough not to need it. However you can still use it. If you believe something got written to it that is causing your issue try renaming the file and booting with out it.

```
sudo mv /etc/X11/xorg.conf  /etc/X11/xorg.conf.bak
```

---

