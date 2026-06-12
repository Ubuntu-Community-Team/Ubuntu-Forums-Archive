---
title: "For Nvidia, Restricted Ubuntu Drivers or Envy?"
date: 2007-07-31
forum: Gaming &amp; Leisure
---

### Post by Drezliok on 2007-07-31
I just want to know what you use and why. I am using restricted Drivers that are provided right now. But I wondered why Envy was still being updated if Ubuntu has it sorta built in now.

What's you take and driver solution.

---

### Post by dreadlord_chris on 2007-07-31
Neither, actually....
I just grab the driver package from NVIDIA and install manually...

---

### Post by cogadh on 2007-07-31
The only problem with using the Nvidia package is you will have to update it manually every time you get a kernel upgrade. In fact, after the kernel upgrade, X stops working until you update the Nvidia driver manually. With the Ubuntu package, it gets updated automatically when your kernel is upgraded and you don't have to worry about your desktop failing. I don't know if the same is true for Envy, however.

---

### Post by Sockerdrickan on 2007-07-31
> **dreadlord_chris said:**
> Neither, actually....
I just grab the driver package from NVIDIA and install manually...
Seconded.

---

### Post by Sammi on 2007-08-01
I use Envy at my own risk.

Envy has a newer driver version than the restricted driver manager, and is also quite capable of fixing a badly installed driver.

Sometimes I won't get a X server at startup, because some kernel package has changed, but then I just use Envy to reinstall, and everything's fine again. Done that a thousand times now on my machine, and it fixes my problems every time. I don't think that this is very noob friendly, so I try to always recommend Envy after the restricted driver manager. Sometimes the simply is no substitute for Envy, if the drivers are borked.

---

### Post by Drezliok on 2007-08-01
> **Sammi said:**
> I use Envy at my own risk.

Envy has a newer driver version than the restricted driver manager, and is also quite capable of fixing a badly installed driver.

Sometimes I won't get a X server at startup, because some kernel package has changed, but then I just use Envy to reinstall, and everything's fine again. Done that a thousand times now on my machine, and it fixes my problems every time. I don't think that this is very noob friendly, so I try to always recommend Envy after the restricted driver manager. Sometimes the simply is no substitute for Envy, if the drivers are borked.

Do you see an improvement to using Envy vs the Restricted drivers?

---

### Post by Naegling23 on 2007-08-01
the restricted driver installation is not integrated into kubuntu's version of fiesty (as with the compiz effects).  Kubuntu users have to use envy...at least I do anyway.

Besides, envy is a great program for those seemingly random moments where you boot into a command prompt after a kernal upgrade that you didnt notice.

---

### Post by mrazster on 2007-08-01
Since I'm using a custom compiled kernel...I find it convinient to use envy script...wich also gives me the latest drivers from nvidia.

Easy to use...like the uninstall options...and works on any kernel regardless of version and compilation.

---

### Post by hikaricore on 2007-08-01
Due to odd Feisty driver issues (which I've had to manually fix...)

> 
[hikaricore@devistate:/lib/linux-restricted-modules/2.6.20-16-386]$ ls -la nvidia*
lrwxrwxrwx 1 root root 9 2007-07-25 20:37 nvidia -> /dev/null
lrwxrwxrwx 1 root root 9 2007-07-25 20:37 nvidia_legacy -> /dev/null
lrwxrwxrwx 1 root root 9 2007-07-25 20:37 nvidia_new -> /dev/null


*cough*

I've been mosting using Envy only to remove the mess that linux-restricted made.
Then I've been reinstalling from the NVIDIA binary.  ^_^

So far my drivers no longer fail to work upon reboot (and no blacklisting them did not help... i tried).

---

### Post by Sammi on 2007-08-02
> **Drezliok said:**
> Do you see an improvement to using Envy vs the Restricted drivers?Only noticeable improvement is that I get to tinker :D

---

### Post by fktt on 2007-08-02
resticted does the job just fine for me and i dont really need the very latest.. the restricted ones update plenty enough for me(thus far at least) :)

i used to use Envy before the 7.04 though :p

---

