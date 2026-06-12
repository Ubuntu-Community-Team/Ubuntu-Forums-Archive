---
title: "Failure to load nvidia kernel module."
date: 2009-04-30
forum: General Help
---

### Post by Mad dog on 2009-04-30
Ubuntu Linux newbie here: (I posted a CC in hardware support, but I'm eager to get an answer, as I'm considering downgrading to Intrepid soon)

I just installed a new (to me) nvidia GeForce FX 5200 in my Dell optiplex gx 260. Upon trying to boot, I got an error message saying I had no nvidia kernel and thus no screen settings were acceptable and I would need to use a generic driver for the time being. 

Well, I used EnvyNG to find the best nvidia driver for me, I installed it and rebooted, but got the same message. If I go to SYSTEM>ADMIN>HARDWARE DRIVERS it shows me a reccomended proprietary driver for my card, however when I try to activate it, nothing happens.

I need to know, what this "nvidia kernel" is and where do I get it? And also, will having this kernel installed enable me to activate the nvidia drivers?

Thank you!

By the way, here is the text of the error message I am getting:

(EE)NVIDIA(0): failed to load the nvidia kernel module!
(EE)NVIDIA(0): *** ABORTING ***
(EE) Screen(s) found, but none have a usable configuration.

---

### Post by kpkeerthi on 2009-04-30
The safest way is to enable the driver from System -> Admin -> Hardware drivers. 

If you used envy it should have installed the nvidia driver for you. You might have to enable the driver. Just run this command in the terminal and **reboot**

```
sudo nvidia-xconfig
```

---

### Post by Mad dog on 2009-04-30
[quote=kpkeerthi;7181927]The safest way is to enable the driver from System -> Admin -> Hardware drivers. 

When I do this, I get a GUI that has a grey circle next to nvidia driver 173 (recommended). Obviously I see it's not enabled so I press the green light button that says Activate. Upon doing so I get a quick, untitled window that says "Downloading and installing driver 0%" it quickly disappears and nothing is different.

When I run: ```
sudo nvidia-xconfig
``` in my the terminal, absolutely nothing happens.

---

