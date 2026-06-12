---
title: "[SOLVED] Compiz not running after Xgl install"
date: 2008-02-08
forum: Desktop Effects &amp; Customization
---

### Post by adster101 on 2008-02-08
Hi All,

I am running Ubuntu 7.10 on a COMPAQ Evo N600C laptop. It all works fine more or less until I installed Xgl yesterday. Now when I log into a Gnome session everything is REALLY slow graphics wise. Whenever I try to turn on desktop effects I get an error saying that I desktop effect could not be enabled. 

I ran a bash script which tells me that compiz is not running. When I log into a failsafe session then the graphics are fast (actually faster than they ever were on a normal Gnome session) but I cannot get the extra desktop effect. I did have these effects working before but they refuse to now.

If I type compiz --replace I get

aborting and using fallback: /usr/bin/metacity 

According to system admin > restricted graphics drivers I do not need any restricted graphics drivers on my system. There is no /user/bin/compiz folder but compiz is installed as the newest version.

Can anyone throw some light on what I need to do here. When I installed Xgl it said I needed to make a certain session default. Does this involve changing any start up scripts?

Thanks in advance!

---

### Post by adster101 on 2008-02-08
Also, when I type compz I get:

Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting emerald
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

Any ideas?

---

### Post by davec64 on 2008-02-08
Have a search on the forum for AIGLX.
From what I can remember, if you're using ATI you don't need XGL.
I'll see if I can find it!

---

### Post by davec64 on 2008-02-08
Found it!!

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

Scroll down the page until you get to  "3D desktop effects"
> 
The new ATI drivers use AIGLX so there is not need to install XGL that older drivers (< 8.40) required.

Don't forget to add FGLRX to the Driver Whitelist!

Hope that helps!

---

### Post by adster101 on 2008-02-08
So I need to remove XGL? 
But why is compiz not starting up?

This is confusing!

---

### Post by davec64 on 2008-02-08
First of all, I would remove XGL.

Then because you are using the FGLRX driver carry out this to add FGLRX to the Whitelist:

```
sudo gedit /usr/bin/compiz
```

Scroll down to, and add FGLRX as below:

```
# Driver whitelist
WHITELIST="fglrx nvidia intel ati radeon i810"
```

Now restart X, and we should be getting somewhere!

---

### Post by adster101 on 2008-02-08
OK, I removed Xgl and added fglrx to the driver whitelist. Rebooted and logged into a Gnome session which ran Xclient scripts. Not sure if that is the correct session (or if it matters).

Gnome then asks me about my keyboard layout (it never used to) but the general speed of the desktop is now imporved. Actually, perhaps it is better than before. 

But....I still cannot enable the desktop effect via the system > appearances tab.

My bash script also is still telling me that compiz is not running. I am assuming that it should be running (but I do not know if it was running before)!?

---

### Post by adster101 on 2008-02-08
I may just need to also install the fglrx drivers tho...

---

### Post by adster101 on 2008-02-08
fglrx appear to be installed here:

/usr/lib/fglrx/libGL.so.1.2.xlibmesa

---

### Post by davec64 on 2008-02-08
Don't worry about the Keyboard for a moment, we'll sort that in a mo!

Lets see what drivers you are using, it looked like FGLRX from your first post.
Can you post the following:

```
fglrxinfo
```

and the following, don't worry about posting this, I'm just interested to see if Direct Rendering is enabled (its near the top)

```
glxinfo
```

---

### Post by adster101 on 2008-02-08
OK, fglrxinfo

display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE NO-TCL
OpenGL version string: 1.3 Mesa 7.0.1


glxinfo


direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

---

### Post by davec64 on 2008-02-08
You're using the Mesa driver. If memory serves me right, you need Direct Rendering for Compiz.
So we need to install either the open source FGLRX driver or the ATI driver.
Which graphics Chipset have you got in your machine?
Then it's which driver do you fancy!?!

---

### Post by davec64 on 2008-02-08
To install a suitable ATI driver follow this Howto:

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

Method 1 is the easier.

Just work your way down through, and you'll be fine.

---

### Post by json25 on 2008-02-08
I have the same issue but with the newest drivers and after doing the checks you mentioned I have Direct Rendering enabled, I followed all the tips on the ATI wiki but I still get a message that says it cannot find XGL.  How do I keep it from looking for XGL?  I also get a pixmap not found error.  :(

I even tried the compiz.real command options to use AIGLX 

compiz.real --intigrated-rendering (I think) --strict-binding --replace

---

### Post by davec64 on 2008-02-08
> **json25 said:**
> I have the same issue but with the newest drivers and after doing the checks you mentioned I have Direct Rendering enabled, I followed all the tips on the ATI wiki but I still get a message that says it cannot find XGL.  How do I keep it from looking for XGL?  I also get a pixmap not found error.  :(

I even tried the compiz.real command options to use AIGLX 

compiz.real --intigrated-rendering (I think) --strict-binding --replace


so what does fglrxinfo give you?

---

### Post by json25 on 2008-02-08
I'm at work right now, had to go from memory but it doesn't say mesa I remember that, and it states the correct version of the driver.  It also states my video chipset correctly.  I'll post the rest of the info from home later.

---

### Post by davec64 on 2008-02-08
I was just readin and came across this quote:

The fglrx driver supports ATI cards from 8500 and up, with the exception of the 9100 IGP, the Mobility 9000 (IBM/Lenovo), and possibly a few others (read the release notes on the download page on ATI's website). As of this writing the x800 cards are difficult to get working and the x1600+ cards are not supported.

Yours isn't an unsupported or problem card is it?

---

### Post by json25 on 2008-02-08
I'll have to check, mine is the X1100 Xpress integrated chipset in a laptop.  But I don't think it's a driver issue as far as normal GL stuff is concerned, the screensavers all run fast and glxgears works fine.

---

### Post by adster101 on 2008-02-11
Ah well, I tried installing fglrx via the wiki tutorial you linked but with no luck.

I already had fglrx installed (which is good) but when I try and do:

sudo aticonfig --initial

I get an error about core dumped as if the process doesn't finish properly. Then there is no xorg.conf file which i have to make a copy of the back up.

If I then modify ati to fglrx in the xorg.conf file as suggested my machine hangs on restart with etc/gdm/failsafeXserver line 47 could not retrieve EDID because get edid is not installed. 

I have to do sudo dpkg-reconfigure -phigh xserver-xorg to get it back up!

And after all that I still have the mesa graphics driver running when I do fglrxinfo! (tears out hair).

What is going on as compiz is not running and I cannot activate the desktop effects. These have been working previously so I know that they do work on this machine. 

Anyone any ideas?

---

### Post by adster101 on 2008-02-11
Tears hair out!

---

### Post by davec64 on 2008-02-12
That is bizarre
I'm at work at the moment, but I'll try and dig some info up when I get back.tonight!
I had a similar issue back with edgy, no matter what I did the Mesa driver was always there!
Hang in there!

---

### Post by adster101 on 2008-02-12
Hmmmm, still no luck. If there is anyone out there that has a clue what I need to do then please let me know. Thanks.

---

### Post by adster101 on 2008-02-12
@davec64, any help you could give would be much appreciated. I will try method 2 from the wiki you posted later today.

---

### Post by adster101 on 2008-02-12
This is what I get when I try and run aticonfig --initial:

Uninitialised file found, configuring.
Using xorg.conf
Saved back-up to xorg.conf.original-4
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbfe389ce ***


======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7ce892b]
aticonfig[0x805c5c7]
aticonfig[0x805c875]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7c91050]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 08:02 1061195    /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 08:02 1061195    /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7c6d000-b7c6e000 rw-p b7c6d000 00:00 0 
b7c6e000-b7c70000 r-xp 00000000 08:02 470520     /lib/tls/i686/cmov/libdl-2.6.1.so
b7c70000-b7c72000 rw-p 00001000 08:02 470520     /lib/tls/i686/cmov/libdl-2.6.1.so
b7c72000-b7c76000 r-xp 00000000 08:02 1055687    /usr/lib/libXdmcp.so.6.0.0
b7c76000-b7c77000 rw-p 00003000 08:02 1055687    /usr/lib/libXdmcp.so.6.0.0
b7c77000-b7c79000 r-xp 00000000 08:02 1055685    /usr/lib/libXau.so.6.0.0
b7c79000-b7c7a000 rw-p 00001000 08:02 1055685    /usr/lib/libXau.so.6.0.0
b7c7a000-b7c7b000 rw-p b7c7a000 00:00 0 
b7c7b000-b7dbf000 r-xp 00000000 08:02 470517     /lib/tls/i686/cmov/libc-2.6.1.so
b7dbf000-b7dc0000 r--p 00143000 08:02 470517     /lib/tls/i686/cmov/libc-2.6.1.so
b7dc0000-b7dc2000 rw-p 00144000 08:02 470517     /lib/tls/i686/cmov/libc-2.6.1.so
b7dc2000-b7dc5000 rw-p b7dc2000 00:00 0 
b7dc5000-b7de8000 r-xp 00000000 08:02 470521     /lib/tls/i686/cmov/libm-2.6.1.so
b7de8000-b7dea000 rw-p 00023000 08:02 470521     /lib/tls/i686/cmov/libm-2.6.1.so
b7dea000-b7ed7000 r-xp 00000000 08:02 1055829    /usr/lib/libX11.so.6.2.0
b7ed7000-b7edb000 rw-p 000ed000 08:02 1055829    /usr/lib/libX11.so.6.2.0
b7edb000-b7ee8000 r-xp 00000000 08:02 1055853    /usr/lib/libXext.so.6.4.0
b7ee8000-b7ee9000 rw-p 0000d000 08:02 1055853    /usr/lib/libXext.so.6.4.0
b7ee9000-b7ef0000 r-xp 00000000 08:02 1055831    /usr/lib/libXrender.so.1.3.0
b7ef0000-b7ef1000 rw-p 00006000 08:02 1055831    /usr/lib/libXrender.so.1.3.0
b7ef1000-b7ef6000 r-xp 00000000 08:02 1056337    /usr/lib/libXrandr.so.2.1.0
b7ef6000-b7ef7000 rw-p 00005000 08:02 1056337    /usr/lib/libXrandr.so.2.1.0
b7ef7000-b7ef8000 rw-p b7ef7000 00:00 0 
b7efc000-b7f06000 r-xp 00000000 08:02 470558     /lib/libgcc_s.so.1
b7f06000-b7f07000 rw-p 0000a000 08:02 470558     /lib/libgcc_s.so.1
b7f07000-b7f09000 rw-p b7f07000 00:00 0 
b7f09000-b7f23000 r-xp 00000000 08:02 473455     /lib/ld-2.6.1.so
b7f23000-b7f25000 rw-p 00019000 08:02 473455     /lib/ld-2.6.1.so
bfe24000-bfe3a000 rw-p bfe24000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

Does it shed any light?

---

### Post by davec64 on 2008-02-12
To help with mu digging, what graphics chip have you got and which version of the driver did you try and install?

---

### Post by adster101 on 2008-02-12
Quote from another site: 
ATI Mobility Radeon 9600 M10 graphics chipset which will work with full acceleration and stuff using ATI's custom proprietary X.org drivers. 

I think mine may be a M6 but it is definitely a mobility chipset. (I am at work now so don't have access to the machine)

In term of which version of the driver I am not sure. I just did apt-get install fglrx or similar as it suggested in the wiki. But it was already installed and at the latest version.

It hangs xserver when I change ati to fglrx in the xorg.conf file. This seems to be a sticking point. 

Is that any help?

---

### Post by davec64 on 2008-02-12
Right then, I've been digging!

I came up with this Howto:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

This is for Radeon open-source driver (ati)

we've been trying to get xorg-driver-fglrx working. I think I may have misled you, I certainly confused myself! That driver appears to require XGL, but the one in the link has AIGLX incorporated.

Which way do you want to go? The ATI driver or the FGLRX?

In my opinion the ATI driver in the Link might be the one as the Howto looks very detailed.

Keep me posted and I'll help where I can!!

Good Luck!:)

---

### Post by davec64 on 2008-02-12
If you want to go the XGL route, I found this, that at facew value looks dead simple:

[http://www.chr05210084.com/content/install-compiz-fusion-ubuntu-gutsy-using-ati-video-card]("http://www.chr05210084.com/content/install-compiz-fusion-ubuntu-gutsy-using-ati-video-card")

Perhaps give this a go first!

I had to use the ATI driver as the above didn't work for me!

---

### Post by adster101 on 2008-02-12
Cracked it in the end! 

This link that you posted was useful:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I think the uninstall of the fglrx driver did the trick. According to the help wiki you are supposed to edit xorg.conf file but every time I do X refuses to start for some reason. It complains about EDID not being installed. I will try and install it at some point (whatever it is!). 

Then I have to do sudo dpkg-reconfigure -phigh xserver-xorg and then it seems to work. Also I kept getting a message about keyboard setting and did I want to choose X setting or Gnome settings. I chose Gnome setting and all seems well. 

I have emerald themes and fancy graphics now! :-)

Still one last point. Compiz does not seem to be running. not sure that it needs to be but would it add anything?

Thanks again.

---

### Post by adster101 on 2008-02-13
Scrap that as compiz is compiz-fusion so I expect that is running somewhere.

---

### Post by davec64 on 2008-02-13
Sweet!!!!!!!!!!!!!!

You might want  download the other Compic Packages Which will give you the Advanced Desktop Settings item in the Preferences menu, if you haven't done it already.

Glad you got the Keyboard sorted that was the was the easy one! For  some reason Xorg and Gnome settings don't match, but you sussed it! Same happened on mine!

All the best!

---

