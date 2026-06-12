---
title: "psx bios problem"
date: 2007-11-23
forum: Gaming &amp; Leisure
---

### Post by MEGAMANULTIMATE on 2007-11-23
I obtained pSX using the Synaptic Package Manager, and I definately have the BIOS image required to run it. When I attempt to run it however, it always says that it doesn't have one whether I place the image into the proper folder or not. And every time it prompts me to select the image, it closes after I select it, with no error message at all. I'm at a loss. Is there anything I should do? I'm also kind of a newb here. Thanks!

---

### Post by Sockerdrickan on 2007-11-24
I would visit the pSX forums instead. Go here [http://psxemulator.proboards54.com/](http://psxemulator.proboards54.com/)
Good luck!

---

### Post by acoustibop on 2007-11-24
Did you actually install PCSX from the Ubuntu repositories, MEGAMANULTIMATE, or did you add dfreer's repository to your list and use Synaptic to download it from there?

If you actually installed PCSX, this is a very old emulator and quite complex to set up.  If you want an enhancing emulator, I'd recommend [ePSXe]("http://www.epsxe.com/").  Although this can be even more complex to set up up than PCSX, it is a better, more recent emulator.  However, even ePSXe is long out of development and hasn't been updated for over 4 years.

If you did install pSX emulator, as Tux0r says, the official forum is the best place to post your question, although the likelihood is you have a naff BIOS.  What's its exact name?

And, if you didn't install pSX, you should; it's a very easy emulator to install and configure: all you need to do is download the [latest version]("http://psxemulator.gazaxian.com/"), install libgtkglext1 in Synaptic, decompress the package you downloaded somewhere (do ```
tar xvpf <package_name>
``` wherever you want it), put a working BIOS in the bios folder and run it.  You'll also need a working 3D videocard driver.

Or you can use dfreer's repository: see his threads [here]("http://ubuntuforums.org/showthread.php?t=394097") and in [the pSX forum]("http://psxemulator.proboards54.com/index.cgi?board=feedback&action=display&thread=1174936096").

---

### Post by myromance123 on 2009-03-17
I'm having the exact same problem as you dood.
 
 Oddly enough my bios file is in capital, as in SCPH1001.BIN, so pSX keeps asking, but when I rename it and decapitalize everything, it stops asking but it still crashes either way...

 I'm working on getting epsxe to work. Wondering whether or not I should try pSX through Wine instead mmm

---

