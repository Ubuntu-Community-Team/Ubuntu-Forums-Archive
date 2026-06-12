---
title: "Blank Screen After Ctrl+Alt+Backspace - Recovery ?"
date: 2008-07-31
forum: Debian
---

### Post by BGFG on 2008-07-31
Hi,
I've just installed Debian. I installed the nvidia-glx and x-server packages. I have on-board nvidia
I hit ctrl+alt+backspace and my screen went blank.
No response from ctrl+alt+f1 or f5.
Even after a restart, the kernel loads then goes straight to a blank screen. No login prompt or anything. 
Any ideas on how to get back my session ?

Thanks.

---

### Post by tuxxy on 2008-07-31
Hit escape as you boot, select recovery mode.  This should get you to terminal now I would reconfigure the xorg if you say the issue was because you installed a driver.

```
sudo dpkg-reconfigure xserver-xorg
```

Follow the process and then you may need to type

```
startx
```

---

### Post by BGFG on 2008-07-31
Thanks a lot , I'll try it now...

---

### Post by BGFG on 2008-08-01
> **tuxxy said:**
> Hit escape as you boot, select recovery mode.  This should get you to terminal now I would reconfigure the xorg if you say the issue was because you installed a driver.

```
sudo dpkg-reconfigure xserver-xorg
```

Follow the process and then you may need to type

```
startx
```

Sorry I'm back here so late. My ISP stopped SP-ing. anyway I've never used recovery mode before. Is it too late to press esc if i get the grub kernel list?

---

