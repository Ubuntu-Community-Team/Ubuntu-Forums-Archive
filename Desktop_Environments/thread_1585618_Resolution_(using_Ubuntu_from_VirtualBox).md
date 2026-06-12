---
title: "Resolution (using Ubuntu from VirtualBox)"
date: 2010-09-30
forum: Desktop Environments
---

### Post by sim085 on 2010-09-30
Hello, I have a problem with my resolution. My laptop is able to handle a resolution of 1600 x 900 (landscape). However on my installation I only get the maximum options of 1360 x 768. This means I have a black border around the desktop when I go to full screen. 

Is there some way how I can get the resolution to 1600 x 900 (landscape)?

Please note that this is an installation of Xubuntu on VirtualBox and that I installed the guest additions. I have this same problem also on an Ubuntu installation (still on VirtualBox)

---

### Post by sim085 on 2010-10-01
Wasn't there a file in which one could defined his preferred resolution?

---

### Post by mister_p_1998 on 2010-10-01
I think the problem is: Virtualbox uses its own virtual Video, sound and network cards, it doest see your Nvidia or whatever. This allows it to run without the need for specific drivers, it also means you cant get your hotshit video resolutions, sorry.
Steve

---

### Post by realzippy on 2010-10-01
Try:

```
VBoxManage setextradata global GUI/MaxGuestResolution 1600,900 
```

---

