---
title: "Intrepid: Firefox CPU load goes 100% after resume from sleep (S3)"
date: 2008-12-11
forum: General Help
---

### Post by wirawan0 on 2008-12-11
I installed Ubuntu Intrepid on a VAIO laptop (PCG-FXA53, using AMD AthlonXP 1400+ with 512 MB of RAM). I am using xubuntu as my distro; but the problem could appear in all other flavors.

There is one glitch with firefox that seems to loom from time to time. I could suspend and resume fine with the laptop, except that firefox uses much CPU (near 100%) at the resume (I noted this by using "top" command). I found out that the following websites cause it:

* google mail (gmail.google.com)
* Yahoo mail new interface (mail.yahoo.com)
* [www.weather.com](www.weather.com)

This is a recollection of my observation; I will confirm this later when I have chance.

The only cure so far was to shut down the firefox and restart it again. But I am not happy with this. Does anybody suffer this kind of problem too?

By the way this kind of problem never happens on my other laptop, which is a Dell Inspiron 600m powered by Pentium M and 768MB of RAM.

Wirawan

---

### Post by Titan8990 on 2008-12-11
I have 3 laptops. ACPI doesn't work properly in Linux for any of them. Defiantly something that needs improvement.

---

### Post by pointym5 on 2009-04-02
I don't see how Firefox going bonkers could be a bug caused by ACPI. The browser operates normally, except that it sits on the CPU continuously. At most ACPI might be an indirect cause, but the problem lies with Firefox itself.

---

### Post by jis on 2009-04-09
> **wirawan0 said:**
> The only cure so far was to shut down the firefox and restart it again. But I am not happy with this. Does anybody suffer this kind of problem too?


Same problem here. The problem occurs when I have pages open that use flashplugin-nonfree. It is enough to close such pages to lessen CPU load. Flash is generally CPU hog on Linux in my experience.

Happens in a workstation: Xubuntu Intrepid, Firefox 3.0.8, flashplugin-nonfree Version: 10.0.22.87ubuntu1~intrepid1, AMD AthlonXP CPU, >1GB RAM.

---

### Post by Lan on 2009-04-11
Hello.

I'm having similar issue after I upgraded to Intrepid.
I notice it more during tabbing, or perhaps as stated above when there is flash - I gotta recheck on that.
I notice this alot on Elisa.

The whole system is cranked up that it's about to lock up until the tabs are shut off or Firefox is killed.

It sucks.


Description:    Ubuntu 8.10
Release:        8.10
Codename:       intrepid

model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz

Mem:          1008        910         97 


I also would like to know if this was covered already and if there's a nice resolution.

This happnes on my laptop as well after upgrading to Intrepid.
Dell D810 with 2GB of RAM and 2Ghz CPU. It was fine before the upgrade from Hardy Heron.

Thanks.

---

### Post by Vaphell on 2009-04-11
Flash is a big issue, true - but mentioned fancy webmail clients are very javascript heavy. Probably after resume scripts are rerun and FF grinds itself to death. Soon to be released FF 3.1/3.5 (now in beta stage) will have brand new javascript engine increasing performance considerably. Time will tell, release should be around june.
[http://www.theregister.co.uk/2009/03/17/firefox3_5_browser/](http://www.theregister.co.uk/2009/03/17/firefox3_5_browser/)

Also you can try Opera ;] It's a damn good piece of software

---

### Post by Lan on 2009-04-12
Thanks for all that info.
I'll try opera.
Yeh, it definitely burns when there's a flash running.
I just right click the flash and stop it and the CPU usage decreases. It still sucks. haha
It just feels so bloated.

---

### Post by afilonov on 2009-06-06
Same thing happens on my System76 Gazelle with Hardy. Funny enough, doesn't happen on Thinkpad t41 with Hardy. Both use the same current flash plugin (10.*).

---

### Post by afilonov on 2009-06-29
My problem with System76 Gazelle disappeared after last updates. I still have Hardy (with backports).

---

