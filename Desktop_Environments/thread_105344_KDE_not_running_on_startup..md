---
title: "KDE not running on startup."
date: 2005-12-18
forum: Desktop Environments
---

### Post by maritimer on 2005-12-18
Hi,

This is my first linux install and I have a slight problem.  Help would be greatly appreciated.

When I installed kubuntu, the first load during the installation, KDE started and everything seemed ok.  I had some issues with the video card. I have a 3dfx Voodoo 3 card and KDE would only allow a 640x480 screen res.  So I set about trying to find out how to get higher res.  In doing so I installed the Glide3 package and removed the Glide2 package since Adept said Glide2 will not work with Voodoo 3.  I still could not select a higher res. So i rebooted my system.

This time when kubuntu booted it went straight to the shell prompt and asked me to login.  In the previous boot the KDE login screen was displayed. 

How do I get the system to start KDE when boot is complete? I thought this would be automatic so I am afraid I may have messed something up by removing the Glide2 package.

Thanks,
Jason

---

### Post by mlomker on 2005-12-18
[QUOTE=maritimer]How do I get the system to start KDE when boot is complete? I thought this would be automatic so I am afraid I may have messed something up by removing the Glide2 package.
[/QUOTE]

Type **startkde** at the prompt to see if it'll load.  If that works then you could try reinstalling the **kdm** package (the login screen) to see if that takes care of it.

---

### Post by maritimer on 2005-12-18
Hi,

I tried typing startkde at the $ prompt and it tried to start KDE but had a lot of errors. Some of the errors are:

xsetroot: unable to open display ''
ksmserver: cannot connect to xserver
ERROR: couldn't attach to DCOP server!
$display is not set
Error: can't contact kdeinit

I could not see all the errors as they went by too fast.

Does this help explain why KDE doesn't start? Is there a log file I can view to get all the error text?

Thanks again,
Jason

---

### Post by Rackerz on 2005-12-18
Ok, try 'startx'.

---

### Post by maritimer on 2005-12-18
Hi,

startx gave the following errors

xauth: creating new authority file /home/jason/.serverautn.6773

giving up.
xinit: COnection refused (errno 111): unable to connect to xserver
xinit: No such process (errno 3): server error

Thanks,
Jason

---

### Post by Ptero-4 on 2005-12-18
You have to install KDM b/c AFAIK ubuntu doesn't use the startx script the way other distros do. Ubuntu relays in GDM/KDM for starting up X11 and running your desktop environment instead.

---

### Post by maritimer on 2005-12-18
Hi,  I am pretty sure KDM is starting.  When I shutdown the screen lists KDM shut down in it's list of activities.

---

### Post by maritimer on 2005-12-18
Hi,

I re-installed kubuntu and it fixed the problem.  I think when I removed the glide2 package it seriously messed up everything.

I still have the problem of only having a 640x480 screen res on a 17" monitor with a Voodoo 3 card.  Any thoughts on how I can get a higher res?

Thanks,
Jason

---

### Post by TaiChi on 2006-03-02
I am also having this problem.  I am using an HP A4331 20" monitor that rates to 1600x1200 and would like to stop the flicker.

Please advise.  Thanx
Bruce

---

### Post by incubus on 2006-03-02
You mean that that's the only option available under System Settings (or "kcontrol")?

What is the content of
/etc/X11/xorg.conf

In that file the section "Screen" should have the resolutions that you want. In my case I have:

Modes "1680x1050" "1024x768" "800x600" "640x480"

incubus

---

### Post by incubus on 2006-03-02
It may also be that the horizontal or vertical refresh rates are set at wrong values. 

In the section "Monitor" check the options HorizSync and VertRefresh. Your monitor's manual has the correct rates. In my case I don't have those options and the LCD works fine.

incubus

---

### Post by kylstien on 2006-03-05
I have virtually the same problem with KDE not launching, except that *I just now installed Kubuntu.*

---

### Post by RavenOfOdin on 2006-04-07
I'm having that issue too. . .

Seems like its just happening lately.

---

### Post by ronniet on 2006-05-14
[QUOTE=RavenOfOdin]I'm having that issue too. . .
Seems like its just happening lately.[/QUOTE]

Ditto!

](*,) 

It's been bugging me now for over 3hrs!

---

