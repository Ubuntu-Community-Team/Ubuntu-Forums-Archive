---
title: "Fixing Pulseaudio on Sugar Desktop"
date: 2009-07-21
forum: Desktop Environments
---

### Post by afrodeity on 2009-07-21
There are a number of sugar activities that require access to pulseaudio.

[http://wiki.laptop.org/go/PulseAudio](http://wiki.laptop.org/go/PulseAudio) mentions the following packages needed to get pulsaudio working on the XO

```
pulseaudio pulseaudio-lib-zeroconf pulseaudio-module-zeroconf
 deps: libsamplerate libtool-ltdl
```

Is there another way to get sugar desktop working with pulseaudio or do these sugar packages need to be repackaged for ubuntu hardy, etc?

BTW if you need to get sound in sugar, you have to install python-csound

I also edited the ~/.sugar/default/config just to be on the safe side.

set volume  to any number, but one should not have to do this since sugar should automatically alter settings.

There is also quite a bit of talk in fedora community about pulesaudio sound and sugar.

This is what I get when I try to use a sugar app that requires pulse

*** PULSEAUDIO: Unable to connect: Access denied 

I am going to try editing
```
gedit /etc/pulse/default.pa
```

uncommenting "load-module module-native-protocol-tcp" and adding "auth-anonymous=1" to the end of the line.

---

### Post by afrodeity on 2009-07-26
> I am going to try editing
Code:

gedit /etc/pulse/default.pa

uncommenting "load-module module-native-protocol-tcp" and adding "auth-anonymous=1" to the end of the line.

no go, I'm stumped

---

### Post by afrodeity on 2009-07-26
> I am going to try editing
Code:

gedit /etc/pulse/default.pa

uncommenting "load-module module-native-protocol-tcp" and adding "auth-anonymous=1" to the end of the line.

no go, I'm stumped

---

