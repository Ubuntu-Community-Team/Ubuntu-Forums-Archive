---
title: "Difference in kernel packages and kernel source?"
date: 2009-05-02
forum: General Help
---

### Post by techphets on 2009-05-02
[COLOR=#333333][FONT=arial]Hi, 

I am trying to install ieee80211 subsystem and the INSTALL file says I need to have kernel packages. It says they should be in lib/modules/`uname -r`/build 

I have no /build directory there. I downloaded the linux-source using apt-get but this put files in /usr/src... 

What is different about the files in /usr/src and the files in /lib/modules/'uname -r'/build ?? ?

How do I get the files into the /build directory? 

Also, how would I determine if the ieee80211 subsystem is already installed on a system? 

Please note, I was originally trying to install a wireless adapter.  I have found a different way to do that, I just want to understand what I was trying to do for hours beforehand...



Thanks.[/FONT][/COLOR]

---

### Post by danwood76 on 2009-05-02
The IEEE80211 stack is installed by default.

I would have thought you are trying to install an old manufacturers install package which probably wont work.
What card are you trying this on?
Most cards are supported by default in the latest Ubuntu.

---

### Post by 3rdalbum on 2009-05-02
I have a 'build' directory there. Do you have the kernel headers package? That's usually what you need in order to compile a kernel module, and according to Synaptic, it's what is providing the /lib/modules/`uname -r`/build directory.

---

### Post by techphets on 2009-05-02
danwood76, 

To begin with I was trying to install the ipw2100 on Debian.  I ended up switching to Ubuntu which supported the adapter immediately after install. 

How could I have verified if the IEEE80211 stack had been installed?  I'm just asking for learning purposes here since I now have the problem solved.  If it is complex to determine there's no need to detail it. 

3rdalbum, 

Thanks, that's it.  How were you able to work backwards to determine that?

---

### Post by danwood76 on 2009-05-02
well from a terminal the binary portion of the 80211 stack is located here:
/lib/modules/KERNEL_VERSION/kernel/net/mac80211
therefore the following command would reveale the stack module:
```

ls /lib/modules/$(uname -r)/kernel/net/mac80211

```
With regards to debian, if you install debian stable it wont have all the latest wireless drivers installed as they only really came into existence at the end of last year.
Ubuntu is built on top of the unstable for of debian so has a lot more features but cant be considered stable for a server environment. (Its stable enough for a desktop for sure)

---

