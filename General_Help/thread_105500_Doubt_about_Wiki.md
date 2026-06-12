---
title: "Doubt about Wiki"
date: 2005-12-18
forum: General Help
---

### Post by tL0z on 2005-12-18
Hello, I've followed [**this**]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Method_1:_Installing_Breezy.27s_Included_Driver_.288.16.20.29")  wiki but when I do

```
fglrxinfo
```

it says:

```
hugo@a85-138-64-207:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
```

and not what is in the wiki. I have a AMD 64 3200+ and a ATI 9600 XT. Can you please help me? :(

---

### Post by amohanty on 2005-12-18
Tae a look at this:
[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

HTH
AM

PS: a meaningful title will go a long way in getting you immediate help.

---

### Post by tL0z on 2005-12-18
I've already read and asked for help -> [http://ubuntuforums.org/showthread.php?p=584896#post584896](http://ubuntuforums.org/showthread.php?p=584896#post584896)

But I would still like to install the drivers that come with the Breezy Badger.

---

### Post by Zimmer on 2005-12-18
Try checking your xorg.conf file..I think you should have selected fglrx in re configure process..look for the following section...your identifier will probably be different from mine, but you should have Driver "fglrx"...if it says "ati", then change it...re boot..and try fglrxinfo again..
-------------------------------------------------------
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Driver		"fglrx"
------------------------------------------------------------
I followed this wiki to get my ATI 9600 working, but I am not running an AMD64
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

Zimmer

---

### Post by tL0z on 2005-12-18
I did it and when I rebooted it had a fatal error and I had to change back to ati by terminal :s 
I actually have:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9600 XT (RV350 AR)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection
```

It's possible to try the Wiki you gave me or should I reinstall Ubuntu before?

---

### Post by Zimmer on 2005-12-19
[QUOTE=tL0z]I did it and when I rebooted it had a fatal error and I had to change back to ati by terminal :s 
I actually have:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9600 XT (RV350 AR)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection
```

It's possible to try the Wiki you gave me or should I reinstall Ubuntu before?[/QUOTE]
 No..do not use that as the wiki I pointed to makes reference to the LACK of drivers (at the time it was written)for AMD64.

The link you first followed: ***
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Method_1:_Installing_Breezy.27s_Included_Driver_.288.16.20.29](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Method_1:_Installing_Breezy.27s_Included_Driver_.288.16.20.29)

appears to be the one you need.
If you open System>Administration>Synaptic Package Manager and find xorg-driver-fglrx      is it marked as installed?

If it is not ,
What drivers ARE installed for your ATI?
 I suggest you read that wiki method *** again .
not forgetting the extra item for 64 bit users...did you read this...

64-bit users:
You have to downgrade to an older version of libdri.a due to an incompatilbity with the ATI drivers...

Did you follow that step?

Regards
Zimmer

---

### Post by az on 2005-12-19
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

---

### Post by tL0z on 2005-12-19
**Zimmer**, what do you mean by ***?

> If you open System>Administration>Synaptic Package Manager and find xorg-driver-fglrx is it marked as installed?

Yep


> Did you follow that step

Yes


When I do this step:

```
sudo dpkg-reconfigure xserver-xorg #Select the fglrx driver and 64-bit users should deselect int10a
```

Should I select fglrx instead of ati?
EDIT: I've just tried it and I got the same erro as above :(

---

### Post by Zimmer on 2005-12-19
*** was just a marker to point you back to the wiki link ,which I had previously marked ***
Sorry for the confusion..
So have you completed the step in the wiki that said..
..................................................................
You have to downgrade to an older version of libdri.a due to an incompatilbity with the ATI drivers. Download it here  [http://mail3.mpr.org/mlomker/libdri.a.gz](http://mail3.mpr.org/mlomker/libdri.a.gz)

Change to the  directory you have downloaded it to: then:

gunzip libdri.a.gz
sudo cp /usr/X11R6/lib/modules/extensions/libdri.a libdri.a.old
sudo cp libdri.a /usr/X11R6/lib/modules/extensions/

 then reconfigure with..

sudo dpkg-reconfigure xserver-xorg

choose fglrx...
...............................................................................................
and you re-booted and tried fglrxinfo and it still shows the Mesa driver message?

If that is the case , have you  investigated the log files:
/var/log/kern.log and Xorg.0.log files   ?

If you would like to mail them to me I have altered my user profile to allow a v Card download of my E mail address ...

Regards
Zimmer

---

### Post by amohanty on 2005-12-19
BTW the steps that zimmer suggested are aplicatble only if you are using the **amd_x64** version of the kernel. It is not meant to be used if you have a 64 bit processor and are using the 32 bit version of the kernel. If you are _not_ using the 64 bit kernel and downgraded libdri you will get a Signal 11 Xserver error. 

If you are using a 32 bit kernel just do the following (I am merely restating zimmer's instructions):

> sudo apt-get install xorg-driver-fglrx
sudo dpkg-reconfigure xserver-xorg

Other than selecting fglrx in the first (possibly second) screen leave everything else to default and reboot (ctrl-alt-backspace) did not work for me.

HTH

---

### Post by tL0z on 2005-12-20
Hello,

Today my internet services had some problems and when starting Ubuntu it often crashed at "setting up network interface" and "adjusting the clock by [url]". I don't know if it influencies the results or not.

> and you re-booted and tried fglrxinfo and it still shows the Mesa driver message?

If I put fglrx instead of ati when configuring, when I reboot the interface has a fatal error and I have to change the configuration by the comand line.

I've just mailed you the files. :)


**amohanty**, yup, I'm using the 64 kernel version.


Regards,
tL0z

---

### Post by Zimmer on 2005-12-22
[QUOTE=tL0z]Hello,

I've just mailed you the files. :)

Regards,
tL0z[/QUOTE]
I have not yet received them :(

I have sent you a message on this forum regarding an alternative e mail address..

Zimmer

---

### Post by Zimmer on 2006-01-17
tLoz? What does    <fglrxinfo>  say about your drivers now?
 and what happens if you type  <fgl_glxgears> at the terminal prompt?
Regards

Zimmer

---

