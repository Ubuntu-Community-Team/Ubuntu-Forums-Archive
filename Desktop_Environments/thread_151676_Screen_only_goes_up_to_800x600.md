---
title: "Screen only goes up to 800x600?"
date: 2006-03-28
forum: Desktop Environments
---

### Post by shultzjr on 2006-03-28
Hi all,

I just installed Ubuntu 5.10 on an older eMachine.  The monitor is a Dell D1728-TCO. The install didn't pick up the monitor and just installed a generic driver that supports 640x480 and 800x640.  I need to know what I have to change to get the driver to go all the way up to the max resolution that this monitor will handle, 1280x1024 I think.

thanks,
charles.....

---

### Post by gnu2tux on 2006-03-28
Check your monitor horiz/vert refresh settings in it's manual/online and drop back to the terminal:

ctrl+alt+f1

Log in as normal and reconfigure your x server:

```

$sudo bash
Password: <your pass>
#/etc/init.d/gdm stop (or kdm if using kubuntu)
#cp /etc/X11/Xorg.conf /etc/X11/Xorg.conf.backup
#dpkg-reconfigure xserver-xorg

```

Choose the advanced or medium setup option, armed with your monitors refresh values, entering when prompted (advanced).

Finally, when you are finished, start up gdm again:

```

#/etc/init.d/gdm start

```

Let me know how you get on.

Ali

---

### Post by BlaineM on 2006-03-28
I dont know in ubuntu, but when I was using FC4, I had to change the max colors to less than what it was set at by default to allow for the higher resolution rate.  Hope this sheds some light.  If not...

---

### Post by gnu2tux on 2006-03-28
The reason that reducing your colours gave you a higher resolution was probably because your emachines PC probably has quite a low-spec graphics card (probably inbuilt). These machines were typically Intel 810/814 integrated chipsets (I know the machines too well unfortunately!).

I have set up Ubuntu on my girlfriends mothers emachines pc which is great at 1024x768x16bpp (16bpp =colours).

The more colours you use, the more memory required. These systems dont have a lot of graphics memory (they use 32mb I think, shared out of the system ram). So, by turning down the colours you can raise the amount of pixels on the screen. This is the same for Windows as it is Linux. 

You will be able to specify the amount of colours for the xserver to use in the dpkg-reconfigure xserver-xorg as explained earlier. 16bpp (or 16k) colours is a safe enough bet to go for firstly.

If you would like better performance out of your monitor, consider buying a cheap graphics card like an Nvidia 5200, cost ~ £25 GBP. Although, make sure you have an AGP port on the motherboard, or buy a PCI card instead if you dont.

Ali.

---

### Post by shultzjr on 2006-03-28
[QUOTE=gnu2tux]The reason that reducing your colours gave you a higher resolution was probably because your emachines PC probably has quite a low-spec graphics card (probably inbuilt). These machines were typically Intel 810/814 integrated chipsets (I know the machines too well unfortunately!).

I have set up Ubuntu on my girlfriends mothers emachines pc which is great at 1024x768x16bpp (16bpp =colours).

The more colours you use, the more memory required. These systems dont have a lot of graphics memory (they use 32mb I think, shared out of the system ram). So, by turning down the colours you can raise the amount of pixels on the screen. This is the same for Windows as it is Linux. 

You will be able to specify the amount of colours for the xserver to use in the dpkg-reconfigure xserver-xorg as explained earlier. 16bpp (or 16k) colours is a safe enough bet to go for firstly.

If you would like better performance out of your monitor, consider buying a cheap graphics card like an Nvidia 5200, cost ~ £25 GBP. Although, make sure you have an AGP port on the motherboard, or buy a PCI card instead if you dont.

Ali.[/QUOTE]

Thanks to you and all who responded.

I tried the suggestions of the first responder.  Everything went well except one letter was capitalized when it should have been lower case.  I did use the medium option on the package manager and I did enable the 1280x1024 mode but when I restarted gdm and logged in, there was no 1280x1024 mode listed  System -> Preferences -> Screen Resolution listing.  It did however have 1024 by 768 listed and it was the default.  That was the only thing I was needing.  Turns ou this monitor will do:

640x480x100Hz
800x600x100Hz
1024x768x100Hz
1280x1024x79Hz

I could go back and do some more fiddling but what I have at the moment is good enough.

BTW, the eMachine I have has the graphics chip on the motherboard and it is an ATI 3D Rage IIc AGP.   The sound and ethernet worked correctly on the first install.

later,
charles.....

---

### Post by halitech on 2006-03-28
Thanks for the info here. Was having the same problem with a test machine here at work and after running through the config a few times, was finally able to get it working at 800x600 which is a big improvement over 640x480. will give it another go tomorrow when I come back to work and see if I can't get 1024x768 running :)

---

### Post by xXx 0wn3d xXx on 2006-03-28
[QUOTE=halitech]Thanks for the info here. Was having the same problem with a test machine here at work and after running through the config a few times, was finally able to get it working at 800x600 which is a big improvement over 640x480. will give it another go tomorrow when I come back to work and see if I can't get 1024x768 running :)[/QUOTE]
Edit your xorg file if you don't have the option. I didn't have the option but I edited my xorg.conf file and my display is now looking great !

---

