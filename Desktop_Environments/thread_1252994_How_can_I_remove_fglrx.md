---
title: "How can I remove fglrx?"
date: 2009-08-29
forum: Desktop Environments
---

### Post by TomB19 on 2009-08-29
I'm getting:

```
# fglrxinfo
Error: unable to open display (null)
```

I'm frustrated with the binary driver.  How can I get back to the open source driver?

Can I just:

```
apt-get remove fglrx-amdcccle fglrx-kernel-source fglrx-modaliases xorg-driver-fglrx
apt-get install --reinstall linux-generic
rm /etc/X11/xorg.conf
```

???

---

### Post by TomB19 on 2009-08-29
OK...  now that I know that won't work, how can I get back to the O/S drivers?  lol!

---

### Post by baizon on 2009-08-29
Hi,
Open */etc/X11/xorg.conf*. 

```
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 9500 Pro (R300 AD)"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
EndSection

```
Change fglrx to _radeon_, save and restart the Xserver.

---

### Post by TomB19 on 2009-08-29
Thanks, baizon.

Nothing I try is working.  I was having trouble with the binary driver so I did my best to remove it.  I even ran "dpkg-reconfigure xserver-xorg"  ... but to no avail.  When I start X it comes up black.

Note: I've tried both with and without using the kernel framebuffer device.

:(

---

### Post by baizon on 2009-08-29
> **TomB19 said:**
> Thanks, baizon.

Nothing I try is working.  I was having trouble with the binary driver so I did my best to remove it.  I even ran "dpkg-reconfigure xserver-xorg"  ... but to no avail.  When I start X it comes up black.

:(

Try: 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
What graphic card do you have?

---

### Post by TomB19 on 2009-08-29
Still a black screen.  :(

VGA compatible controller: ATI Technologies Inc Radeon HD 3300 Graphics

---

### Post by TomB19 on 2009-08-29
Thank you very much for the help, Baizon.  I'm a bit lost on this one.

---

### Post by baizon on 2009-08-29
> **TomB19 said:**
> Thank you very much for the help, Baizon.  I'm a bit lost on this one.

Did it work?

---

### Post by TomB19 on 2009-08-29
No.  Still a black screen.  :(

---

### Post by baizon on 2009-08-29
OK, try that:
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by TomB19 on 2009-08-30
I also tried both methods of removing fglrx that are cited on this page:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

It's still not working.

Knoppix works, so I'm going to try installing Arch  I've wanted to play with it for a while anyway, so this might be as good a time as any.

---

### Post by TomB19 on 2009-08-31
[solved]

For what it's worth, I've managed to get my system running.  The solution was to create a new root partition and install arch linux on it.

Arch has been running very well, although it gives me a lot of errors when I open a command window and type:

"apt-get install application-name"  :)

I really wish kubuntu would stabalize.  I'd probably come back.  I like arch a lot.  It reminds me of my gentoo days.  The problem I have with arch is that it reminds me of my gentoo days.

I freely admit that I like the level of bloat of the *buntu project.  I just wish it would work.

Aside from the stability issues, I also could not manage to get QCAD to save a drawing properly.  QCAD in the jaunty repository will strip a drawing down to a single detail and a single layer.  It won't make any noise about it when you save but when you open the drawing, it's all gone but a single layer/element.  Nasty!

Spamassassin stopped working for me on my two ubuntu servers too.  The positive aspect of this experience is that I now appreciate spamassassin a lot more.  lol!

I'll probably go to arch on the systems at all three of my offices, just for the qcad functionality.  KDE 4.3 is nice but it wouldn't be enough to get me to change on it's own.

Now I'm on arch and it seems pretty good.  I have to get used to typing "pacman -S" instead of "apt-get install".  The packages are all direct from the projects.  That's a sweet benefit of arch.  Unfortunately, arch makes the user do all the work to go beyond bare-bones functionality.  That won't be a huge problem if it's stable but it will get old fast if I end up reinstalling it as frequently as I've had to reinstall kubuntu 9.04.

I have an odd feeling as I type this message.  I know I'll be back.  Not until things are stable, though.

---

