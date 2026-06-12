---
title: "initNG in Dapper?"
date: 2005-11-30
forum: Desktop Environments
---

### Post by Axios on 2005-11-30
Hi

Are there any chance on initNG coming in Dapper?

If not, why?

Thanks

---

### Post by WoodyDragon on 2005-12-09
Did you ever try it? I would LOVE to see initNg working in an actual distribution. It just would rock. But in gentoo I never had it running clean (it was lightning fast, but half of the services were broken ;)  ).
So I do not think, they will introduce this with dapper (well, maybe as an alternative?)

---

### Post by fannymites on 2005-12-09
I'm about to try it in a last ditch attempt to get my modem to work on boot up.
I'll report back shortly.

---

### Post by fannymites on 2005-12-09
Not sure if the first poster has actually tried it on dapper or was just asking if it will be added to the repos but I've tried it myself anyway.
Followed the tut here - [http://www.ubuntuforums.org/showthread.php?t=80423&highlight=initng](http://www.ubuntuforums.org/showthread.php?t=80423&highlight=initng)

Tried it with 2.6.12 and 2.6.15 kernels but I had to remove coldplug to get it to boot but sound was working anyway.
Everything worked as it did before in both kernels (unfortunately that meant my modem still didn't work on boot).
Didn't notice any problems other than something about /dev/mem: permission denied while booting but I didn't have any problems once fully booted.
Also didn't notice any increase in bootup speed with the 2.6.15 kernel since this already boots up much faster than previous kernels for me but the 2.6.12 kernel definitely loaded up faster.

Did some general fiddling around, burnt a cd, sent and recieved some files to/from my phone via bluetooth browsed the net and they all worked fine.
I suppose it depends on what software and services you are using as to how well it works but for me, no problems so far.
But having said that, I'm keeping it installed to mess around with but I won't be using it generally since I don't really see any advantages in my case, it still didn't get my modem to work properly and I'd rather see usplash than a screen full of text on booting.

---

