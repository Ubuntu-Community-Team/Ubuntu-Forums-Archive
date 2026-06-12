---
title: "wubi install"
date: 2010-08-15
forum: Desktop Environments
---

### Post by pete_who on 2010-08-15
I have been trying to download wubi to intstall Ubuntu to run alongside an existing windows intallation. However, it was taking ages so I cancelled and tried again and each time it seems to be requiring more time. I'm now up to 200 hours of required time! Any suggestions please as I would love to try it out!

---

### Post by Frogs Hair on 2010-08-15
The first time I tried Wubi it took about 50 minutes and 20 minutes for updates after install with DSL . are you using dial up and is your download rate displayed ?  The download is about 700 mb and you should expect lots of up dates once installed. Did you disable the windows firewall when the download began ?  You should be asked to do this automatically.

---

### Post by PGHammer on 2010-08-15
> **Frogs Hair said:**
> The first time I tried Wubi it took about 50 minutes and 20 minutes for updates after install with DSL . are you using dial up and is your download rate displayed ?  The download is about 700 mb and you should expect lots of up dates once installed. Did you disable the windows firewall when the download began ?  You should be asked to do this automatically.

As opposed to running the installer the *hard way*, there is an easier (in fact, far easier) method.

1.  Download the ISO (either CD or DVD) of the 'buntu of your choice.

2.  Instead of burning the ISO, simply mount it using your virtual drive software of choice.  (I have tried all the various shareware and freeware virtual-drive software for Windows with this option, and they all work.)  The autorun (if allowed by your virtual-drive settings) will kickstart Wubi (which is included on the ISO); choose the same options as you would installing from a real CD or DVD via Wubi.

3.  This option is decidedly easier, as it works for computers without optical drives at all, or with only an external USB optical drive (which isn't exactly a speed merchant).  I've used this option (or the original variant using a pre-downloaded CD or DVD image file) since Wubi itself was in beta. The only times this hasn't worked is with some (and only some) alphas of 'buntu (it doesn't currently work with the alphas of 10.10, though it did work with nearly every build of 10.04 and 9.xx).  *Yes*; it does work with the x64 versions of 'buntu (installed within the apropos flavors of Windows), as I have Kubuntu Lucid x64 installed within 7 Ultimate x64 (from which I am typing this).

---

### Post by KdotJ on 2010-08-15
> **PGHammer said:**
> As opposed to running the installer the *hard way*, there is an easier (in fact, far easier) method.

1.  Download the ISO (either CD or DVD) of the 'buntu of your choice.

2.  Instead of burning the ISO, simply mount it using your virtual drive software of choice.  (I have tried all the various shareware and freeware virtual-drive software for Windows with this option, and they all work.)  The autorun (if allowed by your virtual-drive settings) will kickstart Wubi (which is included on the ISO); choose the same options as you would installing from a real CD or DVD via Wubi.

3.  This option is decidedly easier, as it works for computers without optical drives at all, or with only an external USB optical drive (which isn't exactly a speed merchant).  I've used this option (or the original variant using a pre-downloaded CD or DVD image file) since Wubi itself was in beta. The only times this hasn't worked is with some (and only some) alphas of 'buntu (it doesn't currently work with the alphas of 10.10, though it did work with nearly every build of 10.04 and 9.xx).  *Yes*; it does work with the x64 versions of 'buntu (installed within the apropos flavors of Windows), as I have Kubuntu Lucid x64 installed within 7 Ultimate x64 (from which I am typing this).

Nice idea!
And of course, if you don't wish to download/use 3rd party virtual drive software, you can always actually burn the ISO to a CD, have the CD in the drive and run wubi off of it

---

