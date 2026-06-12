---
title: "ubuntu 8.04 LTS freezing / hanging randomly - fglrx-related?"
date: 2009-03-03
forum: General Help
---

### Post by chickenlinux on 2009-03-03
Hello.  I am new to Ubuntu, but not new to linux, so I know how to make the terminal do my bidding.

I just installed Ubuntu 8.04, and it has been driving me crazy.  The first thing I did was to install fglrx, as I need 3-D accel. for my Radeon HD 3780.  I don't know if this is related to my problem...

I've been driven crazy by my machine freezing at random intervals.  The cursor, keyboard, everything stops working.  I have to force a reset, which I hate to do, as it corrupts the HD sometimes.

Does anyone have any idea what on earth I need to do?

---

### Post by Vince4Amy on 2009-03-03
> The first thing I did was to install fglrx, as I need 3-D accel. for my Radeon HD 3780. 

It will be if you installed the drivers from the Ubuntu Driver manager or Envyng as they use older versions of the driver.

Did you download the driver from the site or use the above.

---

### Post by Seks on 2009-03-03
I had this problem in Hardy (8.04) as well. No problems with a fully updated Intrepid (8.10) system, though. I always thought it had something to do with the wifi...

If you aren't running a server or anything I suggest just installing or upgrading to 8.10, sorry.

---

### Post by chickenlinux on 2009-03-03
I am using the version of the driver from the synaptic package manager, which I assume is the old one.

Where might I download the better version?
Thanks!

Will Ubuntu autoconfigure this better version of the driver too?
That would be really nice if it could... it was a major hassle to mkinitrd on fedora 10, just to realize it didn't fully work...

---

### Post by Vince4Amy on 2009-03-04
Give this a go:

[http://ubuntuforums.org/showthread.php?p=6835871#post6835871](http://ubuntuforums.org/showthread.php?p=6835871#post6835871)

---

### Post by chickenlinux on 2009-03-04
um... thanks... but where can I find the 32-bit driver?
This should resolve it!

---

### Post by Vince4Amy on 2009-03-04
> um... thanks... but where can I find the 32-bit driver?
This should resolve it!

That driver is compatible with both, there is no separate x64 and 32-bit driver for ATI, it's one whole package.

---

### Post by chickenlinux on 2009-03-04
oh, ok!
Thank you!

---

### Post by chickenlinux on 2009-03-04
Oh No!
When I run ati-config --initial -f after downloading the driver from the ATI site (sorry, I downloaded it before you told me that the package link you provided works on 32 bit systems) I get the following:
```

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  144 (ATIFGLEXTENSION)
  Minor opcode of failed request:  7 ()
  Serial number of failed request:  8
  Current serial number in output stream:  8

```
What on earth am I supposed to do?

---

### Post by chickenlinux on 2009-03-04
Unfortunately, I just disabled the fglrx driver, and the system boots into "low graphics mode." I selected the ati radeon driver, and it works, but at 800x600 resolution.  The darn thing still crashes WITHOUT fglrx.  I'm really fed up with Ubuntu, so I'm just using Slackware, and dealing with the lack of graphical administrations utilities, and using the slackbook.

If this doesn't work very well for me, I'll try 8.10, but until then, I never intend to use Ubuntu on my computers.

thanks for the help anyway!

---

### Post by Vince4Amy on 2009-03-04
> so I'm just using Slackware, and dealing with the lack of graphical administrations utilities, and using the slackbook. Cool, feel free to ask any questions.

---

### Post by chickenlinux on 2009-03-07
well, I don't think I'm allowed to post about anything other than ubuntu, so this'll be about ubuntu and slackware at the same time.
On ubuntu, I could setup the fglrx by just installing and enabling it.
On slackware, I've installed the driver from the ATI site, and then run "aticonfig --inital"  I then ran "modprobe fglrx" (I don't think this was necessary... it returned an error anyway)
when I issued "startx", I got a big, colorful MESS on my screen. I'm going to look for slackware specific install instructions, but can you give me any pointers?

---

