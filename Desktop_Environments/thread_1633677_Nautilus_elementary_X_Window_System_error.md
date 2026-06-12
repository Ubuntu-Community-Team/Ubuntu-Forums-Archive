---
title: "Nautilus elementary X Window System error"
date: 2010-11-29
forum: Desktop Environments
---

### Post by kajivarvdw on 2010-11-29
Hello everyone,

I recently updated my nautilus to nautilus elementary. I've been using it in the past (with ubuntu 10.04), but now it just fails to open. I get the following X Server error when opening nautilus in from a terminal:

```
The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadLength (poly request too large or internal Xlib length erro'.
  (Details: serial 129 error_code 16 request_code 136 minor_code 17)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

I already tried reinstalling X Server, the NVIDIA drivers. I even installed the NVIDIA drivers from the official nvidia website, and updated the X Server to the latest PPA version (now I reverted it back to the default 10.10 X Server version).

With normal nautilus (not elementary), it works perfectly.

Could anyone help me with this? I really would love to be able to use Nautilus Elementary!

A bit of information:

Ubuntu 10.10
NVIDIA drivers (latest from website)
Version of xserver-xorg-video-nouveau: 1:0.0.16+git20100805+b96170a-0ubuntu1
Version of xserver-xorg-video-all: 1:7.5+6ubuntu3
Version of xserver-xorg-video-nv: 1:2.1.17-3ubuntu3
Version of nautilus: 1:2.32.0-0ubuntu6~ppa160

If it would help to include log or conf files or other interstingness, please don't hesitate to ask.

Well, thank you very much for your time!

Cheers,

Kaj-Ivar

---

### Post by Bubbel on 2010-12-10
Same here. Going to get back to plain vanilla nautilus for now. :(

---

### Post by Krytarik on 2010-12-10
I've also tried Nautilus Elementary a few weeks ago. Although I like the look and the additional options, I had to revert back to the standard Nautilus, because there are graphical glitches when scrolling through a long directory tree. I think it's not worth tweaking a otherwise stable system to try to get NE running like it should.;)
I'm running 10.04.

---

### Post by Bubbel on 2010-12-12
> **Krytarik said:**
> I've also tried Nautilus Elementary a few weeks ago. Although I like the look and the additional options, I had to revert back to the standard Nautilus, because there are graphical glitches when scrolling through a long directory tree. I think it's not worth tweaking a otherwise stable system to try to get NE running like it should.;)
I'm running 10.04.

I agree, for the most part. But I would like to see the extra features NE brings to be merged in the official Nautilus release. To get there, NE needs to be tested, and thus used by a lot of people to get all the bugs out.
So: Yes use it on a private system, No don't use it on a production system.

IMHO, of course...
:D

---

### Post by Frogs Hair on 2010-12-12
I have been using NE for 7 months on 10.04 and 10,10 with a Nvidia graphics card and  drivers. I  have not had a single problem . I wish I had something helpful to offer the op. I using the Nvidia current driver installed with the driver jockey.

---

### Post by Bubbel on 2010-12-12
> **Frogs Hair said:**
> I have been using NE for 7 months on 10.04 and 10,10 with a Nvidia graphics card and  drivers. I  have not had a single problem . I wish I had something helpful to offer the op. I using the Nvidia current driver installed with the driver jockey.

Well, same thing here. I use the older version (176, if I'm correct) in stead of the current version. That does not seem to have a lot of effect, though.
It worked fine, till I removed some unused packages. I had some old package cruft build-up since I used a few PPA repositories.
Maybe I'll try to re-enable the NE PPA again, to see if that will work again.
Something though cought my attention, as I removed the NE PPA. The Elementary Desktop PPA also provides the Nautilus Elementary packages. So when I only removed the NE PPA, things weren't back to normal yet, obviously.

Greetz, Bubbel

---

### Post by Krytarik on 2010-12-12
> **Frogs Hair said:**
> I have been using NE for 7 months on 10.04 and 10,10 with a Nvidia graphics card and  drivers. I  have not had a single problem . I wish I had something helpful to offer the op. I using the Nvidia current driver installed with the driver jockey.
The same on my side, I'm using Nvidia-driver version 96 since I have a 9-year-old video card. I'm using Compiz with desktop effects enabled. Do you?
Have you changed anything to make NE run flawless?
What version of NE are you running?

---

### Post by Frogs Hair on 2010-12-12
If using 10.10 make sure you are using the 2.32 version ppa found at the link. The second link is for 10.04.  [http://www.webupd8.org/2010/09/ubuntu-1010-nautilus-elementary-ppa.html](http://www.webupd8.org/2010/09/ubuntu-1010-nautilus-elementary-ppa.html)
[http://www.webupd8.org/2010/04/install-nautilus-elementary-230-via-ppa.html](http://www.webupd8.org/2010/04/install-nautilus-elementary-230-via-ppa.html)

---

### Post by Krytarik on 2010-12-12
> **Frogs Hair said:**
> If using 10.10 make sure you are using the 2.32 version ppa found at the link. The second link is for 10.04.  [http://www.webupd8.org/2010/09/ubuntu-1010-nautilus-elementary-ppa.html](http://www.webupd8.org/2010/09/ubuntu-1010-nautilus-elementary-ppa.html)
[http://www.webupd8.org/2010/04/install-nautilus-elementary-230-via-ppa.html](http://www.webupd8.org/2010/04/install-nautilus-elementary-230-via-ppa.html)
The ppas are the same, directing to the packages for the respective Ubuntu version.
I've also installed the latest available packages, running Ubuntu 10.04.
What about my other questions?

---

### Post by Frogs Hair on 2010-12-12
I did not know the ppas were the same , one is listed as Lucid only and the article is dated . I am running Compiz 0.8.2 from the software center with normal effects enabled and the AWN testing ppa . I also use the Gnomenu ppa.

---

