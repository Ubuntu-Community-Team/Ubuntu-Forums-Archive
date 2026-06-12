---
title: "Can't get Ubuntu running at all..."
date: 2012-06-02
forum: Desktop Environments
---

### Post by marbleduck on 2012-06-02
[edit] I solved it!  The Ubuntu installer refused to work with three, two, or even ONE of my GTX580 3072MB cards. I borrowed my dad's HD6850, and was able to get it installed without a hitch. I then downloaded the official 580 drivers from nVidia, and I was good to go.




I've been attempting to install ubuntu on my custom rig for the past couple hours, and I haven't been able to even get logged in.

I initially used the wubi tool to install ubuntu onto my other SSD from within Windows.  The Ubuntu drive managed to boot itself, but I couldn't use my mouse (I did have it plugged into one of the USB 2.0 ports on my board, not the 3.0 ones) or my keyboard.  The resolution was also extremely weird, the entire login screen took up only the top 1024x768 pixels on the left hand of my display setup (4800x2560).

So I booted back into windows, wiped the drive, and then used the pendrivelinux tool to make a USB drive of the AMD64 iso.

I booted from this ubuntu USB drive, but after a few seconds of a blank purple screen, it gave me an error telling me that the **/install/vmlinuz** file was not found.  I&#8217;ve tried this multiple times on the USB drive, and it has given me this error each time.  What is going on?

Here&#8217;s my system:
Gigabyte P67A-UD7 board
Intel i7-2600K cpu @ 5.1Ghz
16GB DDR3-2133
Windows on a RAID 0 array, Ubuntu going on a 120GB SSD
3x GTX580

I thank you for whatever help you can offer.

---

### Post by matt_symes on 2012-06-02
Hi

> So I booted back into windows, wiped the drive, and then used the pendrivelinux tool to make a USB drive of the AMD64 iso.

I have used unetbootin.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

See if you have more luck with that. Format the pen stick first.

Kind regards

---

### Post by DMGrier on 2012-06-02
I have had a issue where it was a bad burn on a disk, soon as I burnt a new version then I was okay.

Have you tried to do a regular install without wubi?

---

### Post by traditionalist on 2012-06-02
> **marbleduck said:**
> 

<SNIP>

I booted from this ubuntu USB drive, but after a few seconds of a blank purple screen, it gave me an error telling me that the **/install/vmlinuz** file was not found.  I&#8217;ve tried this multiple times on the USB drive, and it has given me this error each time.  What is going on?

Here&#8217;s my system:
Gigabyte P67A-UD7 board
Intel i7-2600K cpu @ 5.1Ghz
16GB DDR3-2133
Windows on a RAID 0 array, Ubuntu going on a 120GB SSD
3x GTX580

I thank you for whatever help you can offer.

Sounds like you are having similar problems to those I had!  Something to do with the graphics. I eventually got Ubuntu installed using a DVD burned on another machine and using GENERIC drivers. It won't work at all with proprietary drivers.

---

### Post by marbleduck on 2012-06-02
> **matt_symes said:**
> Hi



I have used unetbootin.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

See if you have more luck with that. Format the pen stick first.

Kind regards

I tried that, and got into the installer, but the installer never responded to my mouse or keyboard.  The cursor did move, but I was unable to click on anything.


> **DMGrier said:**
> I have had a issue where it was a bad burn on a disk, soon as I burnt a new version then I was okay.

Have you tried to do a regular install without wubi?

I have tried three discs; none of them worked.


> **traditionalist said:**
> Sounds like you are having similar problems to those I had!  Something to do with the graphics. I eventually got Ubuntu installed using a DVD burned on another machine and using GENERIC drivers. It won't work at all with proprietary drivers.
Trying this now.

[EDIT] Tried, did the same thing.  Maybe I'll try a different USB drive than the one I've been using...


I tried some more things:
-Disconnected 3-way SLi bridge
-Removed 2 of my GPUs
-Sacrificed a snow white cat to the god of war at high noon

At this point, I've managed to get into the installer.  I can see my mouse cursor, but it doesn't move at all.

---

### Post by marbleduck on 2012-06-03
I solved it!  The Ubuntu installer refused to work with three, two, or even ONE of my GTX580 3072MB cards. I borrowed my dad's HD6850, and was able to get it installed without a hitch. I then downloaded the official 580 drivers from nVidia, and I was good to go.

---

### Post by traditionalist on 2012-06-03
> **marbleduck said:**
> I solved it!  The Ubuntu installer refused to work with three, two, or even ONE of my GTX580 3072MB cards. I borrowed my dad's HD6850, and was able to get it installed without a hitch. I then downloaded the official 580 drivers from nVidia, and I was good to go.

Glad to hear you got it solved.

---

### Post by tomcarter979 on 2012-06-03
If you still have resolution problems, try this. [http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/x-config.html](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/x-config.html). I know, it is for freebsd but most things still work on ubuntu.

---

