---
title: "Paintball2 on 12.04 (32 bit)"
date: 2012-07-16
forum: Gaming &amp; Leisure
---

### Post by bugtronics on 2012-07-16
Hi,
I just wanted to let any other users out there know what i had to do to get paintball2 working on Precise ( 3.2.0-26-generic-pae i386 )
about paintball2:
[http://digitalpaint.org/files/](http://digitalpaint.org/files/)

If you are running 64 bit, it seems that it may be more involved to get paintball2 to run
there is a post on dplogin.com that listed what the game author had to do to get paintball2 running on a 64 bit 10.04 installation

I included the link here as it helped me understand my issues and may help others

[*[SIZE=2]http://dplogin.com/forums/index.php?topic=23410.msg215371#msg215371[/SIZE]*]("http://dplogin.com/forums/index.php?topic=23410.msg215371#msg215371")



First the errors:
bug@main-workstation:~/Downloads/paintball2$** ./paintball2**


Paintball 2 -- Version 2.0
Execing configs/default.cfg.
Console initialized.

------- Sound initialization -------
LoadLibrary("./snd_oss.so")
/dev/dsp: No such file or directory
SNDDMA_Init: Could not open /dev/dsp.
------- Loading ref_pbgl.so -------
LoadLibrary("ref_pbgl.so") failed: libjpeg.so.62: cannot open shared object file: No such file or directory
Recursive shutdown.
Error: Couldn't load gl refresh!

So thats alot of gibberish to me, so I spent a couple of hours feeding fragments to google and learned a few things about Linux in general.

  I learned that **ldd** can show me what might be missing in libraries 


bug@main-workstation:~/Downloads/paintball2$** ldd ref_pbgl.so **
    linux-gate.so.1 =>  (0x007ed000)
    libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0x00110000)
    libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0x00a08000)
    libXxf86vm.so.1 => /usr/lib/i386-linux-gnu/libXxf86vm.so.1 (0x00abe000)
    libGL.so.1 => /usr/lib/libGL.so.1 (0x00bda000)
    **libjpeg.so.62 => not found**
    libpng12.so.0 => /lib/i386-linux-gnu/libpng12.so.0 (0x00e0a000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0x00244000)
    libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0x00d4b000)
    libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0x003e9000)
    libGLcore.so.1 => /usr/lib/libGLcore.so.1 (0x00fda000)
    libnvidia-tls.so.1 => /usr/lib/tls/libnvidia-tls.so.1 (0x003ee000)
    libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0x0077c000)
    libz.so.1 => /lib/i386-linux-gnu/libz.so.1 (0x00f94000)
    /lib/ld-linux.so.2 (0x00fb8000)
    libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0x00eec000)
    libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0x00cdb000)



[SIZE=3]**So the Solution to get paintball 2 running was**[/SIZE]:

**sudo apt-get install libjpeg62**

This enabled the application to actually start and display the main screen!! Yay!

Thanks to this post:
[https://bugs.launchpad.net/ubuntu/+source/libjpeg6b/+bug/978843/comments/8](https://bugs.launchpad.net/ubuntu/+source/libjpeg6b/+bug/978843/comments/8)

Next I plan to research the sound issue. I think what I need is ALSA-OSS but I have not found installation instructions yet.

---

### Post by bugtronics on 2012-07-16
I tried  ( from [http://ubuntuforums.org/showthread.php?t=1705760](http://ubuntuforums.org/showthread.php?t=1705760) )
```
sudo apt-get install alsa-oss
``````

aoss ./paintball2

```But the sound still did not work.

OSS is listed in the config file:

```
seta snddevice "/dev/dsp"
seta sndchannels "2"
seta sndspeed "0"
seta sndbits "16"
seta snd_driver "oss"
```

---

