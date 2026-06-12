---
title: "How-to: DOSBOX with Roland MT32 sound emulation"
date: 2008-03-19
forum: Gaming &amp; Leisure
---

### Post by mia1dolfan on 2008-03-19
This installs a virtual alsa sequencer device which will emulate Roland MT-32.  This is required to obtain proper sound in legacy DOS applications.

**1.** Download and install the attached Debian package below, *compiled with Ubuntu Gutsy Gibbson.*

```
dpkg -i mt32emu-0.1.3.20070304_i386.deb
```

I am assuming you already have dosbox installed and don't need to '*apt-get install dosbox*'

**2.** Configure DOSBOX to use the Alsa midi MT-32 sequencer

**2a:**  Find out what the client # the alsa midi sequencer registered as, probably 128, unless you some other software MIDI sequencers *(like timidity)*
```

cat /proc/asound/seq/clients | grep MT-32
```

**2b:**  Copy the sample dosbox.conf.example.gz to your home directory

```
gunzip --stdout /usr/share/doc/dosbox/dosbox.conf.example.gz >~/dosbox.conf
```

**2c:**  Modify ~/dosbox.conf with your favorite editor

Ubuntu:
```
gedit ~/dosbox.conf
```
Kubuntu:
```
kate ~/dosbox.conf
```
Console:
```
editor ~/dosbox.conf
```

Modify the line close to line #88 from

```
config=
```

to...* (replace 128 with the client # obtained from step 2a)*

```
config=*128*:0
```

Save the changes...

**3.**  Launch dosbox.  If you launch dosbox from a console, you should see messages similar to...

[SIZE="1"][FONT="Lucida Sans Unicode"][I]CONFIG:Loading primary settings from config file dosbox.conf
ALSA:Client initialized [128:0]
MIDI:Opened device:alsa[/I][/FONT]
[/SIZE]

**4.** Configure your DOS application to use Roland MT-32

You can also use this with other MIDI applications, like kmid - using "GM Emulation" MIDI device

That's all folks!

:guitar:

---

### Post by Riothamus on 2011-09-20
Is there another version of this available? I got an error

```

dpkg: error processing mt32emu-0.1.3.20070304_i386.deb (--install):
 package architecture (i386) does not match system (amd64)

```

When i tried it with the --force-architecture option, it gave me dependency errors with alsa-base:

```

dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package mt32emu:i386.
(Reading database ... 160873 files and directories currently installed.)
Unpacking mt32emu:i386 (from mt32emu-0.1.3.20070304_i386.deb) ...
dpkg: dependency problems prevent configuration of mt32emu:i386:
 mt32emu:i386 depends on alsa-base.
dpkg: error processing mt32emu:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 mt32emu:i386

```

But I verified that alsa-base is installed and is the most recent version.

---

### Post by Perfect Storm on 2011-09-20
Please check the date of this guide/thread. A lot of water have running through the bridge since then.


Thread closed.

---

