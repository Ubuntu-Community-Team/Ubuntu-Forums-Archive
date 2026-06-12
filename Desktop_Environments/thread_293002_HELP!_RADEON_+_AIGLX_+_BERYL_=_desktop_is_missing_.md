---
title: "HELP! RADEON + AIGLX + BERYL = desktop is missing a third"
date: 2006-11-04
forum: Desktop Environments
---

### Post by japatoo on 2006-11-04
I have got an ibm thinpad t41, it has a Mobility Radeon 9000 in it. I installed ubuntu 6.10 several days ago and want to run Beryl on it. Therefor i followed the instructions on [http://wiki.beryl-project.org/index....ntu/Edgy/AiGLX](http://wiki.beryl-project.org/index....ntu/Edgy/AiGLX)

But if i execute beryl or beryl-manager, the desktop and panels are messed up. They're both missing a third or so. The right part where stuff is missing doesn't redraw. And the desktop is white. The windows are fine though.

The blurfx plugin doesn't work, though I thought my Radeon 9000 supports fragment shaders? Or maybe it doesn't? Or it's the opensource drivers?

Anyhoo, I'm hoping to get it to run at a usable level soon. 

my xorg.conf:

Section "Device"
Identifier "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
Driver "ati"
BusID "PCI:1:0:0"
Option "XAANoOffscreenPixmaps"
EndSection

i added the option "XAANoOffscreenPixmaps" by myself but it does not effect anything

hope someone can help me.

tom

---

### Post by crony on 2006-12-22
I had the same exact problem as you, regarding the missing portion of the desktop.  The solution for me was to add the following line to the ServerLayout section of the xorg.conf file:

Option "AIGLX" "true"

That, and a file named .drirc in your home directory with the following contents:

```

<driconf>
    <device screen="0" driver="r200">
        <application name="all">
            <option name="allow_large_textures" value="2" />
        </application>
    </device>
</driconf>
```

Dropping that into /etc/drirc also works if you want it systemwide

---

### Post by justplayin on 2007-02-15
Take a look at post no. 7 from [here.]("http://forum.beryl-project.org/viewtopic.php?f=36&t=2789") I have the same card and a screen with 1400x1050. Now I can have beryl at that resolution and I see no difference in the colors by switching to 16 bit depth.

I have driconf installed but I think changing the depth to 16 bit will do the trick.

---

### Post by Abdi110 on 2007-04-22
Hi.

So I've had the same problem with the white area appearing after switching on GL. This fix corrects the issue for me, but like everyone else beryl runs slow. I switched to 16 bit color and got a major performance boost, but that whole magic about having images still be displayed at 24 bit, I don't see. Any ideas on how this is achieved?

Since then I've switched to compiz running at 24 bit color, it flys so much faster then beryl, sadly it doesn't have as many neat effects and isn't playing nicely with Emerald.

---

### Post by Flare183 on 2007-04-22
Try changing the drive from "ati" to "radeon". If that doesn't work then let me know.

---

### Post by Abdi110 on 2007-04-22
Wouldn't that just load up the same driver?

A friend of mine sent me a quote from the man pages for ait.

DESCRIPTION
      ati is an Xorg wrapper driver for ATI video cards. It
      autodetects whether your hardware has a Radeon, Rage 128, or
      Mach64 or earlier class of chipset, and loads the radeon(4),
      r128(4), or atimisc(4) driver as appropriate.

---

