---
title: "Getting KiGB to run"
date: 2012-06-20
forum: Gaming &amp; Leisure
---

### Post by SketchMan3 on 2012-06-20
Trying to get KiGB to run. I tried checking the binary with ldd command and got this:


```

linux-gate.so.1 =>  (0x00fba000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x00a9c000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0x00202000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x00212000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x008a4000)
	libz.so.1 => /lib/libz.so.1 (0x00a09000)
	NL.so.1.6 => /usr/local/lib/NL.so.1.6 (0x00431000)
	libstdc++.so.5 => not found
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x00855000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x0043f000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00110000)
	/lib/ld-linux.so.2 (0x00147000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x001d8000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x00c5d000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00dd3000)
```

So... I'm not sure how many problems there are, but it appears that libstdc++.so.5 is missing. I checked my repositories, and indeed libstdc++5 is available, but libstdc++6 is already installed on my machine. Is it safe to install both? When I marked libstdc++5 for installation, synaptic didn't give me a warning message, but you can never be too sure...

---

### Post by Perfect Storm on 2012-06-20
It's safe to have them both installed.

---

### Post by SketchMan3 on 2012-06-20
Thank you. It worked. I'm glad I randomly found out about the "ldd" command just at the right time. 

Software developers really should just start putting hints and a list of dependencies into their readmes. I mean... really. It's just a few lines of text. Like... every readme should say "type ldd <binary> in terminal to find out what's what" and stuff...

Anyway, now I come to find that the "Sound" configuration is faded out, and I have no sound.

---

### Post by Perfect Storm on 2012-06-21
restart pulse audio.
```
killall pulseaudio
```

---

### Post by SketchMan3 on 2012-06-23
Thanks, but it didn't work. My audio settings indicator went "<)--" for a second, then it came back "<)))"

Is that what it's supposed to do? Either way, it's still not playing. But I'm using BGB in Wine now, so I guess I don't need to get KiGB running anymore.

---

