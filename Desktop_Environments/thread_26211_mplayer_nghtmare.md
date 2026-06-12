---
title: "mplayer nghtmare"
date: 2005-04-12
forum: Desktop Environments
---

### Post by !nkubus on 2005-04-12
i want to install mplayer, i need it for some video editing software called tovid and i'm not able to get mplayer to work.

heres when i install the package mplayer-custom from ubuntu repository, everything goes good but heres what i get when i launch it :

**mpayer-custom:**
```

mplayer
MPlayer 1.0pre5-3.3.4 (C) 2000-2004 MPlayer Team

CPU: Advanced Micro Devices Athlon 4 /Athlon MP/XP Palomino 1733 MHz (Family: 6, Stepping: 2)
Detected cache-line size is 64 bytes
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Reading config file /etc/mplayer/mplayer.conf
Illegal instruction

```

here is whan i try to install it from marillat repository:

**mplayer-k6** (because i have an amd)
```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer-k6: Depends: libfontconfig1 (>= 2.3.0) but 2.2.3-4ubuntu7 is to be installed
              Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
E: Broken packages

```


myy system spec are the fllowing:

Amd athlon XP 2200+
512 RAM



as i hear it might be a processor troulble, but how to fix ?

any help would very nice :)

thanks :)

---

### Post by josete on 2005-04-12
[QUOTE=!nkubus]i want to install mplayer, i need it for some video editing software called tovid and i'm not able to get mplayer to work.

as i hear it might be a processor troulble, but how to fix ?
[/QUOTE]

No, the problem is that the Marillat packages require some libraries that are to be found in Debian unstable, and that are not in (k)ubuntu. You can maybe install them by changing the "unstable" in your Marillat line to "testing", but I don't know.

There should be a Marillat repository for ubuntu-stuff, otherwise, we're going to get the fingers burnt every time Debian unstable changes!

---

### Post by vanaedium on 2005-04-12
what is this repository? Would you give me the right line into apt list?
Thanx

---

### Post by !nkubus on 2005-04-12
[QUOTE=josete]No, the problem is that the Marillat packages require some libraries that are to be found in Debian unstable, and that are not in (k)ubuntu. You can maybe install them by changing the "unstable" in your Marillat line to "testing", but I don't know.

There should be a Marillat repository for ubuntu-stuff, otherwise, we're going to get the fingers burnt every time Debian unstable changes![/QUOTE]

Thank you for your relply :)

i'm gonna try to use marillat with staging instead of unstable as soon as i come home . :)

---

### Post by darkaudit on 2005-04-12
There's always the option of compiling your own .deb package using the source from Mplayer's home site. In fact, the Mplayer developers suggest that one compiles their own. The Debian folder in the source gives brief instructions on how to do it, and pages such as this one: [http://www.princessleia.com/MPlayer.html](http://www.princessleia.com/MPlayer.html) give more details, and suggests packages you'll need. YMMV, but some of the options on this page didn't work for me, but once they were removed, I ended up with a better version of Mplayer than the one on Ubuntu, without the conflicts that accompany third-party repos.

---

### Post by !nkubus on 2005-04-12
Well ,
very nice find, because the one from staging marillat and the one with apt-get source did not work for me.

thank you very much :)

---

### Post by !nkubus on 2005-04-13
i have finally got mplayer and transcode installed, i had to force the package from hoary with synaptic.

now i will pin them to not upgrade to marrilats ones ;)

thanks for your help guys :)

---

