---
title: "Font Problem- Change resolution from 87x96 to 96x96"
date: 2006-01-06
forum: General Help
---

### Post by Foucault on 2006-01-06
Hello everyone,
I have succesfully installed Ubuntu 5.10 and everything works perfectly. However I seem to have a problem with the fonts. They do not look exactly "right". I' ve searched a bit and I notice that the output of ```
xdpyinfo | grep dots
``` is ```
resolution: 87x96 dots per inch
``` I guess this must have created the problem. Shouldn't these numbers be exactly the same? Is there a way to change that to 96x96?

I would gladly provide more information if required; just ask!

Thanks in advance,
Foucault

---

### Post by mo_x on 2006-01-06
Can you post (as attachment) your /etc/X11/xorg.conf and /var/log/Xorg.0.log.

---

### Post by Foucault on 2006-01-06
Yes, of course. Here is my xorg.conf

Edit: The DisplaySize line under monitor section is commented. This is not an error I've just tried a lot of display sizes, but none worked so I switched to default

---

### Post by mo_x on 2006-01-06
I see you use the nvidia driver. You can set the dpi by adding the following line to the Screen or Device section of the xorg.conf:
Option "DPI" "96x96"
See also the nvidia README.
You didn't post your /var/log/Xorg.0.log. Maybe in there you can see how the dpi is calculated.

---

### Post by Foucault on 2006-01-06
Here is my log as well; sorry for omitting.
I'll try out your tips and post back

Edit Progress:
Well I have tried that out but nothing came out. DPIs won't change. In addition when I've rebooted I could not login as normal user as session was crashing. I turned to recovery mode and started x as root, so that I can find out what happened. Anyway the log of the previous session (which crashed) is

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "foucault"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (gnome-session:9266): WARNING **: Unable to read ICE authority file: /home/foucault/.ICEauthorit

Oh, and the DPI's were perfectly set to 96x96 when I login as root.
What is going on?

---

### Post by mo_x on 2006-01-06
From the log:
(++) NVIDIA(0): DPI set to (100, 100)
Did you give a command line option to set the dpi?

---

### Post by Foucault on 2006-01-06
[QUOTE=mo_x]From the log:
(++) NVIDIA(0): DPI set to (100, 100)
Did you given a command line option to set the dpi?[/QUOTE]

No, I have never given a command line option to set the DPI. In every single screen resolution (from 800x600 to 1600x1200) the dpi is not in the form AxA (96x96 etc.). Strangely enough this does not happen with the root user.

I have thought that it might have been a problem because my /home/foucault folder was kept from the previous distro (SuSE 10) so I made a fresh install. The problem exists. The resolution is wrong and hence the fonts do not look right. I do not have a clue.:confused:  (Well, to be honest I've read in a forum that I can change the dpi by passing the DisplaySize option in xorg.conf, however nothing happens either). HELP :cry:

---

### Post by mo_x on 2006-01-06
The "DPI"option in the xorg.conf is not supported by the version of the nvidia driver in Ubuntu, you would have to get the latest from nvidia for that.
You could try starting X with -dpi option:
startx -- -dpi 96
Is the size of your display reported correctly:
xdpyinfo | grep dimension
Are there any differences in the logs when you start X as root or normal user?

---

### Post by Foucault on 2006-01-07
[QUOTE=mo_x]The "DPI"option in the xorg.conf is not supported by the version of the nvidia driver in Ubuntu, you would have to get the latest from nvidia for that.
You could try starting X with -dpi option:
startx -- -dpi 96
Is the size of your display reported correctly:
xdpyinfo | grep dimension
Are there any differences in the logs when you start X as root or normal user?[/QUOTE]

"xdpyinfo | grep dimension" returns "dimensions: 1280x1024 pixels (373x272 millimeters)" which is absolutely correct

I do not notice any difference in the root logs. It also says that dpi is set to (100,100).

Starting x with the -dpi 96 option does not seem to yield any results.

It seems that I'll have to get the latest drivers. I've installed nvidia's kernel modules in previous distros so it is not a big deal, however I have to ask: Should I uninstall previously installed the debian package first?

---

### Post by mo_x on 2006-01-07
I keep this little howto because it seems to be useful to many people :) Just posted it on some other thread a minute ago.

Here is a short howto for installing the latest nvidia driver.
- Install compiler etc. and linux headers.
```
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
sudo apt-get instal gcc-3.4
```
- Remove all packages related to nvidia driver with --purge option
```
sudo dpkg --purge nvidia-glx
sudo dpkg --purge nvidia-kernel-common
sudo dpkg --purge linux-restricted-modules-`uname -r`
```
- Run the installer script (you may need a different version).
```
export CC=/usr/bin/gcc-3.4
sudo sh NVIDIA-Linux-x86_64-1.0-8178-pkg2.run
```

---

### Post by mo_x on 2006-01-07
Based on the dimensions I would say the dpi is correct:
1280*25.4/373=87
1024*25.4/272=96

---

### Post by Foucault on 2006-01-07
Update: 
I have succesfully installed the NVIDIA 8178 Driver. After that I tried to pass the DPI Option in xorg.conf. However this was fruitless as well. What I cannot understand is that the Xorg.log states
```
DPI set to (96, 96); computed from "DPI" X config option
```

which means that X has succesfully changed the DPI to 96x96 which is the correct one (And I know that, because every single distribution I have used before has set the dpi to 96x96 in this resolution). However:
```
foucault@ubuntu:~$ xdpyinfo | grep dot
  resolution:    77x82 dots per inch

```

By the way, the login screen works at the correct DPI after the installation of the NVIDIA driver (also at 1280x1024). Everywhere there is 96x96 resolution except for my session. It is a bit weird, isn't it? :rolleyes: It is sure that I am missing something. I just need some help to locate it!

I attach my new Xorg.log and xorg.conf in a compressed bz2 file. Thank you for your patience.

---

### Post by mo_x on 2006-01-07
Could it be the dpi is set by GNOME. You can check the font preferences. I am using KDE myself.
Another possibility, the dpi is calculated for 1600x1200. Can you remove 1600x1200 from the Modes in your xorg.conf and try again.
1280/1600*96=77
1024/1200*96=82

---

### Post by Foucault on 2006-01-07
Gnome's fond DPI is set to 96, of course. Maybe the dpi is indeed calculated for 1600x1200 but shouldn't this be overriden by the DPI option in xorg.conf? Anyway I'll try reconfiguring xorg and post back.

---

### Post by Foucault on 2006-01-07
Update:
Reconfiguring xorg, removing 1600x1200 and passing the DPI options under screen section did the job. Everything looks better now. I just need to find out a way to enable the higher resolution. Anyway thank you so much for your valuable help ;)

---

### Post by konungursvia on 2007-01-09
> **mo_x said:**
> I see you use the nvidia driver. You can set the dpi by adding the following line to the Screen or Device section of the xorg.conf:
Option "DPI" "96x96"
See also the nvidia README.
You didn't post your /var/log/Xorg.0.log. Maybe in there you can see how the dpi is calculated.

Dank u wel! This fixed a problem for me. :D

---

