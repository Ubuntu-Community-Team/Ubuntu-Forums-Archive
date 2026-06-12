---
title: "Can't Enable Desktop Effects in 7.04"
date: 2007-06-21
forum: Desktop Effects &amp; Customization
---

### Post by CarlosinFL on 2007-06-21
I just installed 7.04 on a Intel Core 2 Duo using a 8600GTS video card. The video card seems to be working fine so far in Ubuntu 7.04 except for the fact that during the splash screen when I should see the Ubuntu logo and then the orange progress bar loading at the bottom, I see noting. My monitor is in stand by until GDM starts and then I can login graphically and everything looks normal.

I then attempt to enable "Desktop Effects" on my nVidia 8600GTS video card and when I click "Enable", my entire screen goes white until I press the "enter" key to return back to normal.

Anyone know what is causing this or how I can get Desktop Effects to work on my machine? Is it my hardware?

---

### Post by lukeisthecoolest on 2007-06-21
i have the same exact problem. I don't think it is your graphics card i think it is sometin else

---

### Post by CarlosinFL on 2007-06-22
I installed Debian (testing) before Ubuntu and it was able to load the nVidia drivers with no problem but I did it the hard way by getting the drivers from nVidia.com and then building them against the kernel. Normally on Ubuntu this has no problems.

---

### Post by pardesi on 2007-06-22
1.Install the proper video drivers from restricted drivers manager from system,adminstaration

2.change the binary value at the end of 
                                                        
```
sudo gedit /etc/X11/xorg.conf
```
in composite extensions
to "1" if it is not already so.

---

### Post by CarlosinFL on 2007-06-22
When I attempt to install the Restricted Drivers, I am told my card does not require them and that is all. I show my xorg.conf is using a "nv" driver but it wont use the driver. 

Oh well. Seems like it is back to Debian for me.:(

---

### Post by avik on 2007-06-22
I won't say this is the exact issue, but Restricted Drivers never told me I needed a special driver.  Nevertheless, I installed the restricted NVIDIA driver using:

```
sudo apt-get install nvidia-glx-new
```

I need that driver for 3d acceleration.

---

### Post by ev5unleash1 on 2007-07-02
Yo everyone,

I have the same problem but I'm not using an external G card i'm using intel intergrated.

---

### Post by andrmagn on 2007-08-06
I'm having the same problem with the following comp:

Intel C2D 6420
Motherboard: Nvidia nforce 650 isli
Geforce 8600gts

Restricted manager says that there is no hardware in need of restricted drivers or something similar. Problem is that I have no driver installet and can't change the resolution or play 3d-games. 

Is this going to be fixed in 7.10? I've tried tribe 3 but it didn't work there either.

8600GTS is a common card these days so I hope this problem will be fixed shortly or a lot of people might go back to WinXP.


//Andreas

---

### Post by Chudilo on 2007-08-06
Get ENVY. It'll install everything for you. 
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

