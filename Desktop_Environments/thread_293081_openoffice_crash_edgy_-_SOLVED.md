---
title: "openoffice crash edgy - SOLVED"
date: 2006-11-04
forum: Desktop Environments
---

### Post by tja on 2006-11-04
hi.

after todays update (IIRC fglrx was in it) openoffice would not start. starting from commandline would give only
```
** (process:<XXXXX>): WARNING **: Unknown error forking main binary / abnormal early exit ...
```
after spending some time, looking here and google around and trying various things (remove openoffice-gtk, turning off DRI etc etc etc) i managed to find the right hint :)

it seems that the update broke the xorg.conf file, symptom is when xdpyinfo reports false screen dimensions:
```
<user>@<machine>:~$ xdpyinfo |grep dimensions
  dimensions:    1600x1200 pixels (0x0 millimeters)
```
a simple
```
sudo dpkg-reconfigure xserver-xorg
```
will put things in place again:
```
<user>@<machine>:~$ xdpyinfo |grep dimensions
  dimensions:    1600x1200 pixels (542x406 millimeters)
```

oo runs fine again.
:D :D :D

---

### Post by cnbiz850 on 2006-11-13
I have the following:
```

xdpyinfo |grep dimensions
  dimensions:    1680x1050 pixels (331x212 millimeters)

```

but still can't start OO.  The error is:

```

** (process:6748): WARNING **: Unknown error forking main binary / abnormal early exit ...

```

---

### Post by Rob2687 on 2006-11-27
I had this problem too.

I solved it by removing some fonts I recently added. Apparently OO doesn't like them.

---

### Post by strimmer on 2007-02-01
After running the totem updates and the others in the same batch, I too could not start OpenOffice.

Running thru:

sudo dpkg-reconfigure xserver-xorg

fixed the problem for me.

Thanks!

---

### Post by soxs on 2007-03-05
xdpyinfo teaches me aswell about an 0x0 mm Screen, even after reconfiguring once with the dpkg-reconfigure and once manually. Both did not work.

I have no clue what to do anymore.
Every proposal is welcome.

Note: I am not going to reinstall Ubuntu totally, at least not before the new release, and I allready de- and re-installed openoffice (the latest version) several times, even with --purge and all the stuff. But it did not help either.

---

### Post by thathatman on 2007-03-08
This solved the problem for me right away. Thanks!

---

### Post by David Castelow on 2007-03-17
Try editing the /etc/X11/xorg.conf file so that the "Monitor" section contains a DisplaySize section with non-zero entries, e.g.
This worked for me.

Section "Monitor"
        VendorName   "HP"
        ModelName    "A4575A"
        Identifier   "HP A4575A"
        HorizSync    20.0 - 100.0
        VertRefresh  50.0 - 120.0
        DisplaySize  330 260
        Option      "DPMS"
EndSection

---

### Post by soxs on 2007-04-03
oh... now it works for me aswell :-P

my problem was, the tft (yes the tft ITSELF) not being configured correctly...

.. and that was the reason why it did not work.

Output is now:
root@bernhard:/home/bernhard# xdpyinfo |grep dimensions
  dimensions:    1280x1024 pixels (433x347 millimeters)

so thx a lot

---

### Post by dday376 on 2007-04-03
> **soxs said:**
> oh... now it works for me aswell :-P

my problem was, the tft (yes the tft ITSELF) not being configured correctly...

.. and that was the reason why it did not work.

Output is now:
root@bernhard:/home/bernhard# xdpyinfo |grep dimensions
  dimensions:    1280x1024 pixels (433x347 millimeters)

so thx a lot

Having the same problem.  The DisplaySize setting did not help.  What do you mean:

> my problem was, the tft (yes the tft ITSELF) not being configured correctly...

What is "tft"?

---

### Post by benner on 2007-04-09
i don't quite understand the solution here either.  i am getting closer.  i switched from the proprietary driver to whatever ubuntu puts in its place (i am using feisty with the handy restricted drivers tool) and as soon as i rebooted, openoffice worked.  unfortunately, the driver was not working correctly and my screen was greenish and text was not appearing quite right.  bummer because i was happy to get funky desktop effects and office working.  anyways, i switched back to fglrx and bang!  office does the same thing.  splash screen comes up, progress bar gets to 1/3 and it all disappears.  opening as gksudo in terminal gives me the warning... that everyone else is getting.  can someone explain this fix to me a bit more clearly?

---

### Post by VladArod on 2007-04-26
I had the same problem when changed to the "fglrx" driver. I solved the problem reducing the maximum vertical and horizontal refresh rates in the xorg.conf Monitor section.
Values higher than 100 in Vertrefresh seems to cause the OO crashing problem.

Values:
Horizsync       30-60
Vertrefresh     48-80
work for 1024+768@75Hz

Regards
Vladaros

---

### Post by djhworld on 2007-07-17
How odd, I was experiencing the same problem as stated above.

After changing my resolution to 1280x1024 and restarting X, OpenOffice worked fine (and the "dimensions" were set)

How odd....

---

### Post by prof3ta on 2007-10-06
Same problem here:
```

prof3ta@shuttle:~$ oowriter 

** (process:7419): WARNING **: Unknown error forking main binary / abnormal early exit ...

```
I reconfigured the X server, but the problem still remain. Any ideas? I neeeed openoffice!!!

---

### Post by mike2357 on 2007-10-27
Here's another solution.  It works because when openoffice is called and the openoffice.org-gnome package is installed, the first program to be called is named ooffice.  If instead, a program called soffice is called, there does not appear to be a problem.  So while the Ubuntu folks figure out how to solve the true root cause, you can "trick" openoffice to start with soffice rather than ooffice.  The steps are:

1.  Create a file in the /usr/local/bin directory called ooffice.  You will need to use the sudo command to do so, such as "sudo gedit /usr/local/bin/ooffice"

2.  The ooffice file should contain just two lines, as follows:
#!/bin/sh
exec soffice $*

3.  Set permissions on the file with the command "sudo chmod 755 /usr/local/bin/ooffice".

This appears to work, at least for me.  It's a kluge, but doesn't really hurt anything, and when the openoffice is fixed, you can remove the file.

---

