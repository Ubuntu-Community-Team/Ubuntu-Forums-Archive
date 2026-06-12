---
title: "Testers wanted for Wubi 7.10"
date: 2007-11-07
forum: Development CD/DVD Image Testing
---

### Post by ago on 2007-11-07
Hi all,

Wubi 8.04 is about to be released on the Ubuntu CD and in stand-alone mode. If you do not know what wubi is, have a look at [http://wubi-installer.org](http://wubi-installer.org). This is the first "official" Wubi release, so it requires some hammering on your side (windows required for the installation).... 

You can find the development version of wubi here: [http://wubi-installer.org/devel/minefield/](http://wubi-installer.org/devel/minefield/)
Let wubi download the ISO for you. And please also try Kubuntu & friends.

If you have troubles:

1) run chckfs /f in a dos box within the drive where you installed wubi
2) after selecting wubi press esc at the countdown and try the other boot options
3) ask in the wubi forum ([http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)), possibly attaching the relevant log (even better if you select verbose mode at boot):

* Windows logs are in your temp folder (type %temp% in windows explorer) and in /ubuntu/*.log.
* Boot logs are /casper.log + /tmp/*log. They are relevant in case you cate a busybox prompt after rebooting.
* Ubiquity logs are /var/log/syslog + /var/log/installer/*. They are relevant for any issue during installation after rebooting.

Thanks in advance,

Ago

---

### Post by syxbit on 2007-11-28
you should probably tell us what it is.
based on the name i assume it's based on gutsy.
but what's different?

---

### Post by ubukool on 2007-11-28
[http://wubi-installer.org/](http://wubi-installer.org/)

:)

---

### Post by XxsydenxX on 2008-02-12
i installed the 7.10 wubi without any problems it worked perfectly...Until i restarted my computer...it went to load ubuntu and got the busybook thing...it was rather dissapointing because ive really wanted ubuntu 7.10....i can wait for this to come out..

---

### Post by ago on 2008-02-12
Can you please use 8.04 now?
Hard reboots might be an issue in any case though, but regular reboots should work

---

### Post by ago on 2008-02-12
Mods, can you please update the title to 8.04? The thread is still valid

---

### Post by insanet on 2008-02-24
count me in.
i just got a new computer and im having some strange compatibility issues with the ram and mobo which made it difficult to do a normal install of Ubuntu so i am going to test wubi 8.04.

---

### Post by D3M0L1$H3® on 2008-03-05
I'll definitely try it. I have regularly installed Ubuntu 7.10, but I had been wondering about in-windows versions.

---

