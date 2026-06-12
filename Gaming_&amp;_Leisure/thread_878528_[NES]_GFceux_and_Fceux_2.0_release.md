---
title: "[NES] GFceux and Fceux 2.0 release"
date: 2008-08-03
forum: Gaming &amp; Leisure
---

### Post by punkrockguy318 on 2008-08-03
The fceux team and I have been working really hard to put together a solid official release of FCE Ultra; the first release in years.  The build in Ubuntu right now is quite old and perhaps someone with some packaging experience could build a package for Ubuntu?  Both fceux and gfceux compile fine in Ubuntu 32 bit and 64 bit (both 8.04 and 8.10).

For details about the release check out [http://fceux.com](http://fceux.com)

The GTK2 Front-end has also had a lot of features added to work with some of the features that others and I have added to fceux, so I'd encourage anyone using fceu or any other NES emulator to give fceux a try and report any bugs and leave some feedback.

If you have any quesitons, feel free to post them in this thread.

---

### Post by punkrockguy318 on 2008-08-03
I'd also like to see fceux 2.0 be packaged in Ubuntu.  The legacy release is currently in Ubuntu.  I've filed a bug last night that I hope will see some attention before 8.10 release: [https://bugs.launchpad.net/ubuntu/+source/fceu/+bug/254352](https://bugs.launchpad.net/ubuntu/+source/fceu/+bug/254352)

---

### Post by dbbolton on 2010-05-02
I keep getting this error when I try to set up a gamepad:

```

Error parsing command line arguments
Traceback (most recent call last):
File "/usr/lib/python2.5/site-packages/gfceux/main.py", line 600, in gamepad_clicked
self.gamepad_config_no = d[widget.name]
KeyError: None

```

Both that file and /usr/bin/gfceux are using python2.5

---

### Post by jkxx on 2010-05-02
Not a fix to (g)fceux though you could try installing wine and then running nestopia through it - it works perfectly for me with both sound and video and detects my attached controllers properly.

As a plus nestopia has a NTSC TV emulation mode that makes it look just like playing a real NES.

As for the native fceux, it has severe audio skipping problems and runs very slowly, unfortunately.

---

### Post by punkrockguy318 on 2010-05-02
> **jkxx said:**
> Not a fix to (g)fceux though you could try installing wine and then running nestopia through it - it works perfectly for me with both sound and video and detects my attached controllers properly.

As a plus nestopia has a NTSC TV emulation mode that makes it look just like playing a real NES.

As for the native fceux, it has severe audio skipping problems and runs very slowly, unfortunately.

FceuX has NTSC TV emulation (with scanlines if you want)

Also, fceuX does NOT have audio skipping problems.  SDL/pulseaudio in Ubuntu 9.10/9.04 have low-level issues that cause problems with fceuX.  Sound in fceuX works prefectly fine and lag free out of the box in Ubuntu 10.04

I can't stress this enough just because I am really tired of hearing about fceuX-SDL sound issues.  The issue is not with fceuX.  There is a decent amount of documentation on getting it running in 9.10/4.  

I'm not saying anyone shouldn't use nestopia; it's a decent emulator.  But please don't spread false information.

---

### Post by punkrockguy318 on 2010-05-02
> **dbbolton said:**
> I keep getting this error when I try to set up a gamepad:

```

Error parsing command line arguments
Traceback (most recent call last):
File "/usr/lib/python2.5/site-packages/gfceux/main.py", line 600, in gamepad_clicked
self.gamepad_config_no = d[widget.name]
KeyError: None

```

Both that file and /usr/bin/gfceux are using python2.5

what version?

if you're using the latest version of fceux you shouldn't even be using gfceux

gfceux is completely obsolete now that fceux has a native GTK GUI

---

### Post by dbbolton on 2010-05-02
> **punkrockguy318 said:**
> what version?

if you're using the latest version of fceux you shouldn't even be using gfceux

gfceux is completely obsolete now that fceux has a native GTK GUI

2.1.2, from upstream.

The source tarball came with an "fceu" (sic) directory and a "gfceux" directory. I built and installed both.

However, I was able to set up the gamepad via
```
fceux --inputcfg gamepad1
```

---

### Post by punkrockguy318 on 2010-05-02
> **dbbolton said:**
> 2.1.2, from upstream.

The source tarball came with an "fceu" (sic) directory and a "gfceux" directory. I built and installed both.

However, I was able to set up the gamepad via
```
fceux --inputcfg gamepad1
```

i'd use 2.1.3; it's a MAJOR improvement on the linux front

---

