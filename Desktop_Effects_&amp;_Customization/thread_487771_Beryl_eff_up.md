---
title: "Beryl eff up"
date: 2007-06-29
forum: Desktop Effects &amp; Customization
---

### Post by lock, stock and linux on 2007-06-29
hello

last night i finally got beryl working after months of trying different guides [http://ubuntu1501.blogspot.com/2007/04/beryl-in-feisty-with-xgl.html]("http://ubuntu1501.blogspot.com/2007/04/beryl-in-feisty-with-xgl.html")
i found one, ran it and it worked
but then i was downloading java to my computer and all of a sudden my cube doesnt work nor my rain
all the window animations work still
i ran beryl under terminal and got this:

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0

i also tried uninstalling beryl and got this:

connor@George:~$ sudo apt-get autoremove beryl emerald-themes
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 



thanks

---

### Post by ronocdh on 2007-06-29
> **lock, stock and linux said:**
> i also tried uninstalling beryl and got this:

connor@George:~$ sudo apt-get autoremove beryl emerald-themes
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 



thanks
Try **sudo aptitude remove beryl**? As for your error, post more information about your hardware, etc. for help on that.

---

### Post by lock, stock and linux on 2007-07-05
sorry for the late reply

that did not work and the error told me agian

specs:

# Microsoft(R) Windows(R) XP Professional with SP2
# AMD Athlon(TM) 64 4000+ (2.4GHz/1MB l2 Cache)
# 15.4" WXGA BrightView Widescreen (1280x800)
# 128MB ATI RADEON(R) XPRESS 200M w/Hypermemory(TM)
# 2.0GB DDR SDRAM (2x1024MB)
# 80 GB 5400 RPM Hard Drive
# DVD+/-RW/R & CD-RW Combo w/Double Layer Support
# 54g(TM) Integ. Broadcom 802.11b/g WLAN & Bluetooth

thanks

---

### Post by lock, stock and linux on 2007-07-05
sorry for the late reply

that did not work and the error told me agian

specs:

# Microsoft(R) Windows(R) XP Professional with SP2
# AMD Athlon(TM) 64 4000+ (2.4GHz/1MB l2 Cache)
# 15.4" WXGA BrightView Widescreen (1280x800)
# 128MB ATI RADEON(R) XPRESS 200M w/Hypermemory(TM)
# 2.0GB DDR SDRAM (2x1024MB)
# 80 GB 5400 RPM Hard Drive
# DVD+/-RW/R & CD-RW Combo w/Double Layer Support
# 54g(TM) Integ. Broadcom 802.11b/g WLAN & Bluetooth

EDIT:also, nothing can install/update 

thanks

---

