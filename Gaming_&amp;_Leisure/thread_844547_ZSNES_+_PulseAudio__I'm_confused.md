---
title: "ZSNES + PulseAudio | I'm confused"
date: 2008-06-29
forum: Gaming &amp; Leisure
---

### Post by brodae on 2008-06-29
As the title suggests, I'm confused as to how to run ZSNES while using Pulse Audio. I would appreciate some help.

- B

---

### Post by Grishka on 2008-06-29
zsnes -ad pulse

---

### Post by brodae on 2008-06-29
It showed up as a stream in the pulseaudio gui, but I'm still not hearing anything. Do I need to close other streams? What should I do?

---

### Post by acoustibop on 2008-06-29
Do you particularly need to run ZSNES with PulseAudio, brodae?

If not, do```
zsnes -?
```to get a list of possible drivers for ZSNES, then try```
zsnes -ad <your selected driver>
```for each one, replacing <your selected driver> with the one you want to try each time.  When you've found one that works well for you, stick with that - most people seem to find the SDL driver is favourite.

---

### Post by diablo75 on 2008-06-29
I think the command I used to fix it was this:

> zsnes -ad sdl

You only need to enter that into terminal once.  Every execution from the Applications>Games menu from there on should work fine (it did for me, anyway).  Let us know what works for you.

A bug report [found here]("https://bugs.launchpad.net/ubuntu/+source/zsnes/+bug/188567") has more info about this.  One other solution that has worked for some (say, if the above command works, but produces crackly sound) is to do this also:

```
sudo apt-get install libsdl1.2debian-oss
```
And then:
```
pasuspender -- zsnes -ad auto
```

---

### Post by brodae on 2008-06-29
The only that worked, had garbled sound, and it was libsdl1.2debian-pulseaudio. I tried all of the others and none of them worked. It was garbled and kinda "spikey" sounding, if you will.

---

### Post by acoustibop on 2008-06-30
Try installing libsdl1.2debian-all, brodae, then try the ZSNES drivers again.

You may find installing it removes some drivers, but don't worry - these will be reinstated as part of the new package.

---

### Post by brodae on 2008-06-30
I tried that, and got no results. This time, nothing worked.

---

### Post by dfreer on 2008-06-30
Try the patched version of zsnes 1.51:
[http://board.zsnes.com/phpBB2/viewtopic.php?p=168952](http://board.zsnes.com/phpBB2/viewtopic.php?p=168952)
[http://board.zsnes.com/phpBB2/viewtopic.php?p=168959](http://board.zsnes.com/phpBB2/viewtopic.php?p=168959)

---

### Post by brodae on 2008-07-01
I can't find the patched version in those articles. Where is it?

---

### Post by FranMichaels on 2008-07-01
> **brodae said:**
> I can't find the patched version in those articles. Where is it?

[http://board.zsnes.com/phpBB2/viewtopic.php?p=168959](http://board.zsnes.com/phpBB2/viewtopic.php?p=168959)

First post in that thread. Pick one that is for your system, the bottom src tarball, you'd need to build yourself.

I've been running the last svn release of zsnes. You can look at the links in my sig to see if they help you.

Anyway, my hopes are for a public source release of the newer version soon (I like cutting edge / bleeding software) That and someone offer a GTK interface for the next version, not just a QT one (although no biggie, but still...)

---

### Post by dfreer on 2008-07-02
> **brodae said:**
> I can't find the patched version in those articles. Where is it?

Indeed. Just try one of the binaries first like the above post says, unless you are comfortable with compiling zsnes. Make sure to grab the one for your processor (example, if you have an Intel Core 2 Duo, you'll probably want the core2 version).

When you install it, I'd recommend trying the following (although you don't have to, this is more to troubleshoot things):
(1). Either rename or delete your ~/.zsnes/ folder, which will delete any previous configuration files (if you delete this folder, BACKUP your saved games first!).
(2). Make sure any old versions are gone and install the new one (just decompress the zsnes*.tar.gz file).
(3). Run zsnes through the terminal to pickup any error messages.
(4). Make sure libao is installed (sudo apt-get install libao2), and try running zsnes like so:
```
zsnes -ad oss
``` If libao doesn't work for you, then try the SDL driver (I happen to think SDL doesn't sound as good, but whatever).

---

### Post by blueturtl on 2008-07-02
For me editing the ~/.zsnes/zsnesl.cfg file helped, all I had to do was change the following lines:

```
; However "auto" (to automatically pick best one), and "sdl" should
; always be available.
libAoDriver="auto"
```

to

```
; However "auto" (to automatically pick best one), and "sdl" should
; always be available.
libAoDriver="sdl"
```

That fixed it for me. Stuttering audio can be fixed, it's a problem with some cheap audio hardware (typically laptop integrated, or AC97 etc.)

The solution is in this thread:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

See part 3: stuttering audio fix

---

