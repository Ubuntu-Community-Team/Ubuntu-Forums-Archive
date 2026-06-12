---
title: "Ubuntu 10.04 logo at boot"
date: 2010-04-30
forum: Desktop Environments
---

### Post by Ko$ on 2010-04-30
Hello everyone,

Congratulations with the new release. Very good looking. Thanks for upgrades. Satisfied at all )))

I did upgrade from 9.10 it went good and now works great. One problem, the logo "Ubuntu" at booting displayed on very low resolution, it`s very big and I can see that it`s not as it should be because on my laptop it looks better. I have nvidia card. However, the driver works and all my desktop effects work on max.

Any idea?

Sorry for my English :)

---

### Post by xxeper on 2010-04-30
I think what he means to say, and what I actually came here to post about, is that the login screen for Ubuntu is low res, however when logged into the desktop, everything's at the proper resolution.

I'd REALLY like the login screen to look as clean and crisp as the rest of my Ubuntu experience, is there ANY way to get that login screen to show up in the native resolution of the monitor or laptop screen?

Another question for me would be, if I can set the resolution of the login screen, and I set it up for my desktop monitor [attached to my dock], can I A) get it to play nicely with my dual screens, and B) will it have a fit if I undock my laptop [which is a lower native-res] and use it that way?

---

### Post by janosikPL on 2010-04-30
bad work, and bad resolution. logo screen on run and exit.
my graphic card - Ati/AMD fglrx


(my englisch is bad)

---

### Post by Aikon- on 2010-04-30
> **Ko$ said:**
> Hello everyone,

Congratulations with the new release. Very good looking. Thanks for upgrades. Satisfied at all )))

I did upgrade from 9.10 it went good and now works great. One problem, the logo "Ubuntu" at booting displayed on very low resolution, it`s very big and I can see that it`s not as it should be because on my laptop it looks better. I have nvidia card. However, the driver works and all my desktop effects work on max.

Any idea?

Sorry for my English :)

The proprietary nVidia graphics driver does not support kernel modesetting (KMS), a feature required for the "pretty" boot graphics. The fallback condition is now a basic framebuffer, which is why the Ubuntu logo looks so bad and pixelated during boot. This is a step backwards for those using the proprietary driver, but a step forwards for those using the nouveau driver, which *does* support KMS.

-Aikon

---

### Post by Finalfantasykid on 2010-04-30
> **Aikon- said:**
> The proprietary nVidia graphics driver does not support kernel modesetting (KMS), a feature required for the "pretty" boot graphics. The fallback condition is now a basic framebuffer, which is why the Ubuntu logo looks so bad and pixelated during boot. This is a step backwards for those using the proprietary driver, but a step forwards for those using the nouveau driver, which *does* support KMS.

-Aikon

Indeed, if you want the boot to look good, you will have to use the Nouveau driver, but by doing this you are pretty much sacrificing the rest of the cool desktop effects.  I am hoping that the boot will be updated so that it does somehow work, but this might have to wait until 10.10.

---

### Post by xxeper on 2010-04-30
I'm guessing there's no such equivalent for my wretched Intel 9xx graphics driver?

---

### Post by Ko$ on 2010-04-30
> **xxeper said:**
> I think what he means to say, and what I actually came here to post about, is that the login screen for Ubuntu is low res, however when logged into the desktop, everything's at the proper resolution.

I'd REALLY like the login screen to look as clean and crisp as the rest of my Ubuntu experience, is there ANY way to get that login screen to show up in the native resolution of the monitor or laptop screen?

Another question for me would be, if I can set the resolution of the login screen, and I set it up for my desktop monitor [attached to my dock], can I A) get it to play nicely with my dual screens, and B) will it have a fit if I undock my laptop [which is a lower native-res] and use it that way?

Not exactly, login screen (where I chose a user) looks great, but the Ubuntu logo (before) does not.



-------------


Second thing that I came across is that when I do my SD card (stick from Ipaq HP; have a reader in) in and pull out, then again in and it does NOT do anything, even the light doesn`t. Reboot helps.
:lolflag:

p.s. Won`t go to 9.10 back.

---

### Post by mister_playboy on 2010-05-01
> **xxeper said:**
> I'm guessing there's no such equivalent for my wretched Intel 9xx graphics driver?

The boot screen should display in your normal desktop resolution if you have an Intel chipset.

---

### Post by Trapper on 2010-05-01
> **Ko$ said:**
> Not exactly, login screen (where I chose a user) looks great, but the Ubuntu logo (before) does not.

Gee, a graphical login screen? I'm using the nvidia driver and get a login screen about every 10 boots. The rest of the time I get the commandline instead and have to do a startx to get to the gui. It's irritating me quickly.

---

### Post by Ko$ on 2010-05-01
> **Trapper said:**
> Gee, a graphical login screen? I'm using the nvidia driver and get a login screen about every 10 boots. The rest of the time I get the commandline instead and have to do a startx to get to the gui. It's irritating me quickly.

I think that we just need to wait for the first "service pack" for 10.04. Will work properly :)

---

### Post by ScripterJR on 2010-05-01
Yeah, I'm getting the same stuff. My experience with Ubuntu so far is wonderful, but the boot screen looks nasty :(

---

### Post by dino99 on 2010-05-01
> **Trapper said:**
> Gee, a graphical login screen? I'm using the nvidia driver and get a login screen about every 10 boots. The rest of the time I get the commandline instead and have to do a startx to get to the gui. It's irritating me quickly.

sudo dpkg-reconfigure gdm

---

### Post by dino99 on 2010-05-01
> **ScripterJR said:**
> Yeah, I'm getting the same stuff. My experience with Ubuntu so far is wonderful, but the boot screen looks nasty :(

sudo gedit /etc/default/grub

add or modify:

GRUB_GFXMODE=1024x768
GRUB_GFXPAYLOAD_LINUX=keep

---

### Post by fantom4ik on 2010-05-01
> **dino99 said:**
> sudo gedit /etc/default/grub

add or modify:

GRUB_GFXMODE=1024x768
GRUB_GFXPAYLOAD_LINUX=keep
Thanks.
P.s I add only GRUB_GFXMODE=1920x1200 in /etc/default/grub and used  sudo update-grub 
It`s work ((:

---

### Post by YongQing on 2010-05-03
> **fantom4ik said:**
> Thanks.
P.s I add only GRUB_GFXMODE=1920x1200 in /etc/default/grub and used  sudo update-grub 
It`s work ((:
i did what you did
and the boot image remained low res but the GRUB OS selection screen did become higher res =/

---

### Post by maiaymistru on 2010-05-03
> **dino99 said:**
> GRUB_GFXMODE=1024x768
GRUB_GFXPAYLOAD_LINUX=keep

Tnx! The pixelated logo has been driving me nuts, but the gfxpayload did the trick.

---

### Post by fantom4ik on 2010-05-03
> **YongQing said:**
> i did what you did
and the boot image remained low res but the GRUB OS selection screen did become higher res =/
Try

```
GRUB_GFXMODE=1024x768 #change to your screen size
GRUB_GFXPAYLOAD_LINUX=keep
```
Then in console:
```
sudo update-grub
```

---

### Post by YongQing on 2010-05-03
> **fantom4ik said:**
> Try

```
GRUB_GFXMODE=1024x768 #change to your screen size
GRUB_GFXPAYLOAD_LINUX=keep
```
Then in console:
```
sudo update-grub
```
tried it, now the boot image won't even show XD
i'm using nvidia drivers btw. the problems started after installing the drivers.

---

### Post by Slave2Metal on 2010-05-03
This is exactly how mine is set up, and the splash shows.  Had to remove the # before GFXMODE to change grub resolution from 640x480.  Also, your GRUB_CMDLINE_LINUX_DEFAULT="quiet splash", should have the word splash in order to see it.

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=800x600
GRUB_GFXPAYLOAD_LINUX=1280x1024 

> **YongQing said:**
> tried it, now the boot image won't even show XD
i'm using nvidia drivers btw. the problems started after installing the drivers.

---

### Post by AbangBoltok on 2010-05-03
> **dino99 said:**
> sudo gedit /etc/default/grub

add or modify:

GRUB_GFXMODE=1024x768
GRUB_GFXPAYLOAD_LINUX=keep


:popcorn: :popcorn: :popcorn: :popcorn: :popcorn: 

Thank u....

the Grub list become smaller and the boot screen become so sexy....

:-({|= u rock...!! :-({|=

---

### Post by YongQing on 2010-05-04
> **Slave2Metal said:**
> This is exactly how mine is set up, and the splash shows.  Had to remove the # before GFXMODE to change grub resolution from 640x480.  Also, your GRUB_CMDLINE_LINUX_DEFAULT="quiet splash", should have the word splash in order to see it.

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=800x600
GRUB_GFXPAYLOAD_LINUX=1280x1024
tried it as well.
i've tried almost every combination. over n over again. now, the splash won't show on either boot up or shut down. also, no messages are displayed. i just get a black screen.
i'm giving up

---

### Post by Trapper on 2010-05-04
> **dino99 said:**
> sudo dpkg-reconfigure gdm

I did this and never will again. :) I spent hours after my first bootup after it trying to get into the gui. I finally quit and just reinstalled Lucid. Uniquely, with this install I haven't had an instance where I haven't gotten the gui login screen.

---

### Post by AbangBoltok on 2010-05-04
> **YongQing said:**
> tried it as well.
i've tried almost every combination. over n over again. now, the splash won't show on either boot up or shut down. also, no messages are displayed. i just get a black screen.
i'm giving up


Try this......

> **dino99 said:**
> sudo gedit /etc/default/grub

add or modify:

GRUB_GFXMODE=1024x768
GRUB_GFXPAYLOAD_LINUX=keep


dont give up.
grab some beers and listen to music and try to fix it.

---

### Post by YongQing on 2010-05-04
> **AbangBoltok said:**
> Try this......

dont give up.
grab some beers and listen to music and try to fix it.
i dont respond well to alcohol. nobody wants to hear me pour out my (mostly angry) feelings on ubuntu.

that was my last attempt. splash screen won't load on boot up or shut down.

here's my grub file:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" vga=792 splash"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1024x768
GRUB_GFXPAYLOAD_LINUX=keep

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

thing is, i don't think it's a problem with settings in grub. i think it's another problem. instead of the splash screen, i see 1 or 2 green/blue lines near the top of the screen. maybe the graphics driver can't render the splash image.

---

### Post by AbangBoltok on 2010-05-04
my grub is sexier than yours.. :D

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_GFXMODE=1280x800
GRUB_GFXPAYLOAD_LINUX=keep

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

---

### Post by Trapper on 2010-05-04
> **AbangBoltok said:**
> 
dont give up.
grab some beers and listen to music and try to fix it.


Yeah .... and after many hours of futility simply reinstall U10.04. I ended up with everything working okay and a nice buzz using that procedure.  :D

---

### Post by YongQing on 2010-05-04
> **AbangBoltok said:**
> my grub is sexier than yours.. :D

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_GFXMODE=1280x800
GRUB_GFXPAYLOAD_LINUX=keep

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```
as i suspected, the only difference b/w our grubs is our GRUB_CMDLINE_LINUX. are you using nvidia drivers? if you are, i'll try removing that line.

---

### Post by AbangBoltok on 2010-05-04
> **YongQing said:**
> as i suspected, the only difference b/w our grubs is our GRUB_CMDLINE_LINUX. are you using nvidia drivers? if you are, i'll try removing that line.


yes. i am....:guitar:

---

### Post by YongQing on 2010-05-05
> **AbangBoltok said:**
> yes. i am....:guitar:
changed it to GRUB_CMDLINE_LINUX="" and it works now.
thx!

---

### Post by smittix on 2010-05-05
I have the same problem when using the non-free ati drivers. I would use the driver that is installed on a fresh install but for some reason my laptop fans stay on all the time.

When i install the ATI Driver the fans operate normally.

---

### Post by xxeper on 2010-05-05
I've tried pretty much everything suggested in this thread [everything that applies to my non-Nvid/ATi IGP]

I still get:

1) no splash screen at boot up [there's supposed to be one after grub-loader, correct? I just get a black screen until the login screen comes up]

2) 640x480 login screen.

here's my current grub:

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1680x1050
GRUB_GFXPAYLOAD_LINUX=keep

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

The grub loader shows up in 1680x1050 just fine.

---

### Post by AbangBoltok on 2010-05-06
yup... same here..
i couldnt see my boot screen.
well, i've just find out when i reboot my computer after a new kernel update.
but before, i still can see my boot screen.

any suggestion??

---

### Post by xxeper on 2010-05-10
Nothing? No advice? Guess I'm a one-off.

---

### Post by green69 on 2010-06-09
Hi guys!

For me no one of the solution proposed in this thread worked out.

I found the solution for my system at:

[http://ubuntuforums.org/showthread.php?p=9435597#post9435597](http://ubuntuforums.org/showthread.php?p=9435597#post9435597)

Basically just 2 commands:

echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u

I hope this works for you!

---

