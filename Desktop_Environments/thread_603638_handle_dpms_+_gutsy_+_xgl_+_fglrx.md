---
title: "handle dpms + gutsy + xgl + fglrx"
date: 2007-11-05
forum: Desktop Environments
---

### Post by bash4fun on 2007-11-05
hey guys

does anybody know how i can put my laptop screen to sleep by pressing a key combo?

i'm using an ati x1400 with fglrx and xgl and compiz enabled
i wondered if it is possible to write a script which enables me handling my screen

commands like "xset dpms force off" don't work for me
its printing me something like:
```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  146 (DPMS)
  Minor opcode of failed request:  6 (DPMSForceLevel)
  Serial number of failed request:  10
  Current serial number in output stream:  12

```

thanks in advance

---

### Post by jpk on 2007-11-05
Have a look at aticonfig --enable-monitor=...

---

### Post by bash4fun on 2007-11-05
it would be nice if you described it a bit more in detail

i don't even have a man entry for aticonfig :confused:

thx

---

### Post by jpk on 2007-11-06
Hi! Sorry about that short answer... :D

aticonfig is a part of xorg-driver-fglrx package. This tool allows you to configure your ATI graphic card. It gives you a lot of options, such as power management, dual-screen configuration and so on. 

It does not have a man-page, I think, but if you run it without arguments, you'll get a lot of information describing the usage of the program. 

What I suggest to you problem is that you use --enable-monitor switch. For example:

aticonfig --enable-monitor=crt,lvds 

will enable LCD panel and VGA-out on your laptop. If you want to disable all monitors:

aticonfig --enable-monitor=none

Alternatively, you can use radeontool utility - it allows you to control the light on LCD. I remember, I could write something like:

radeontool light off

and it turned off the screen.

---

### Post by bash4fun on 2007-11-06
i attempted to do aticonfig --enable-monitor=none
but i got the following error message

```
robert@robert-laptop:~$ aticonfig --enable-monitor=none
ati_dm: FGLRX_EnableDisplays failed when try to enable display: 0.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.

```

also radeontool light off also does not work for me, though it also doesn't print an error message

concerning the aticonfig problem...is it possible that i have to set it for another display because as far as i know Xgl uses display :1?
if it is so, how can i do that?

thx

---

### Post by jpk on 2007-11-06
strange... maybe, I'm wrong about aticonfig and you cannot use it to turn the light off. But it is possible to change GPU speed like this: aticonfig --set-powerstate=1 or try aticonfig --lsp.

radeontool works fine for me, remember to use sudo:

sudo radeontool light off

DON'T USE sudo with aticonfig - it will modify your xorg.conf file

---

### Post by bash4fun on 2007-11-07
i personally like the idea of using radeontool to turn off my light, but as already mentioned
it does not work for me...

are there any ideas how to receive an useful output to find out, why it is not working for me?

and by the way, Xgl cannot be responsible for that ?!?

i entered this command, maybe it is useful for anybody...

```
robert@robert-laptop:~$ sudo radeontool --debug
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400 (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 2003
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at ee00 [size=256]
        Memory at efdf0000 (32-bit, non-prefetchable) [size=64K]
Radeon found. Base control address is efdf0000.
usage: radeontool [options] [command]
         --debug            - show a little debug info
         --skip=1           - use the second radeon card
reading RADEON_DAC_CNTL (58) is 00000000
         dac [on|off]       - power down the external video outputs (on)
reading RADEON_LVDS_GEN_CNTL (2d0) is 00000000
         light [on|off]     - power down the backlight (off)
         stretch [on|off|vert|horiz|auto|manual]   - stretching for resolution mismatch 
         regs               - show a listing of some random registers

```

thx

---

### Post by diwant on 2008-04-08
I am experiencing exactly the same problem as bash4fun (the same debug printout, the same graphics card, the same "sudo radeontool light off" not working with no error message).

Is there a fix for this?  I am hoping 8.4 might have something for us.

Diwant

---

### Post by bash4fun on 2008-04-10
yes i also hope 8.04 is going to bring us a lot more features, especially the handling of hardware. so we'll see....

greetings

---

