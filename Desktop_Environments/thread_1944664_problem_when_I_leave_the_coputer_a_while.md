---
title: "problem when I leave the coputer a while"
date: 2012-03-21
forum: Desktop Environments
---

### Post by forsubhi on 2012-03-21
when I leave the computer for about 10 minutes and return to it again I see
this message in black and white screen and the pc is hanged 

freezing user space processes -- ( elapsed 0.01 seconds ) done 

freezing remaining freezable tasks -- ( elapsed 0.01 seconds ) done 

pm : entering mem sleep 

suspending console ( use no-console -suspend to debug ) 

what is the problem ? 

I use kubuntu 11.10

---

### Post by papibe on 2012-03-21
Hi forsubhi.

It looks like 'Power Management' (pm) is set to send to sleep your machine after a determined period of time.

If you want to avoid that, check your settings (take a look [here]("https://wiki.ubuntu.com/KubuntuPowersave")), and if that doesn't work, check your BIOS in case there are other hardware settings configured.

Hope that helps,
Regards.

---

