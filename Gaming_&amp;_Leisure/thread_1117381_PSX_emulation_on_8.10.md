---
title: "PSX emulation on 8.10"
date: 2009-04-05
forum: Gaming &amp; Leisure
---

### Post by ColdSpider on 2009-04-05
Hi,

So I'm fairly new to linux and just installed 8.10 (Intrepid Ibex). I was wondering if there are any guides to installing psx emulators on this particular version, or if anyone could answer the questions I have below. Sorry if this is one of those topics that's been re-visited a thousand times, but I've been looking all over the forums for a while now and have yet to be able to solve my issues.

1) I followed the tutorial for installing epsxe and I keep getting this error:
error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
even after installing the libgtk1.2 package. Are there any other steps I can take to fixing this?

2) PCSX won't close whenever I try to close it, the window just goes black and the sound keeps playing, does anyone know of anything I can do to fix this?

3) If anyone could detail for me how to install psxfin that would be greatly appreciated.


Thanks a lot!

---

### Post by fain on 2009-04-06
Are you on a 64bit system maybe? If so you might just need either a native 64bit binary of the emulator or the 32bit library.

You might try psX. I don't remember but it ran with out much prepping I believe.[http://psxemulator.gazaxian.com/]("http://psxemulator.gazaxian.com/")

---

### Post by Bakon Jarser on 2009-04-06
I've used psX on linux before (but it's been a while) and it ran games nicely.  I'd give it a try if I were you.

---

### Post by wingnux on 2009-04-06
You can get the libs you need by installing getlibs ([http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs](http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs)) and following the instructions on that thread, it's pretty easy.

---

### Post by ColdSpider on 2009-04-07
Ok, so I installed getlibs and used it to get the missing lib, but now I'm getting this error:

error while loading shared libraries: libgmodule-1.2.so.0: cannot open shared object file: No such file or directory

I tried to use getlibs to get this and it said:

libglib1.2 was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install

It's entirely possible that I've just completely overlooked something very obvious, I'm very much computer illiterate when it comes to linux (I just picked up a couple of books on Ubuntu and Python to aid this, but haven't had the chance to get through them yet) and really am not sure what I'm doing at all, so I apologize if this is making anyone bang their head against their desk in frustration. Oh, and I tried pSX (it's the one I meant when I said psxfin) and got it running, but it flickers and has all sorts of video garbage which leads me to believe that my onboard graphics (Intel 965 GM chipset) aren't configured correctly, so if by chance anyone could direct me to some help with that it would be appreciated.

---

### Post by Grishka on 2009-04-08
> **ColdSpider said:**
> Ok, so I installed getlibs and used it to get the missing lib, but now I'm getting this error:

error while loading shared libraries: libgmodule-1.2.so.0: cannot open shared object file: No such file or directory

I tried to use getlibs to get this and it said:

libglib1.2 was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install

It's entirely possible that I've just completely overlooked something very obvious, I'm very much computer illiterate when it comes to linux (I just picked up a couple of books on Ubuntu and Python to aid this, but haven't had the chance to get through them yet) and really am not sure what I'm doing at all, so I apologize if this is making anyone bang their head against their desk in frustration. Oh, and I tried pSX (it's the one I meant when I said psxfin) and got it running, but it flickers and has all sorts of video garbage which leads me to believe that my onboard graphics (Intel 965 GM chipset) aren't configured correctly, so if by chance anyone could direct me to some help with that it would be appreciated.

that's a bit odd, you sure you got the latest version of pSX? if you do, try getting the old version of glib here: [http://packages.ubuntu.com/gutsy/i386/libglib1.2/download](http://packages.ubuntu.com/gutsy/i386/libglib1.2/download). extract the .so files and put them in /usr/lib32. that should do it.

---

### Post by ColdSpider on 2009-04-09
Ok, so I did that and now it looks like the problem is just my video setup, I'm not getting any error messages any more but all three emulators have all sorts of video problems which I'm inclined to believe is because my integrated graphics aren't configured properly, so I'll figure out what I need to do in that department in a more appropriate thread, thanks a lot for the help!2

---

