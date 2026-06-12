---
title: "PCSX - problems reading CD-image"
date: 2008-05-09
forum: Gaming &amp; Leisure
---

### Post by Buzzdee on 2008-05-09
Hello, 

I installed PCSX and all available updates from the synaptic servers and the program starts nicely. The CDROM plugin I use is the only one available - mooby2 1.2.8
When I try and 'mount' an image ('Run CD') I get the error message, that the program cannot mount ISO-9660 images.
If one would either know which images are readable and how to create them or how to run an actual CD from my drive, that would be of great help to me. 

Best regards,
Bastian (Tekken 3 addict) :)

---

### Post by acoustibop on 2008-05-09
AIR the most recent Mooby CDROM plugin never worked for me when I had PCSX running, Buzzdee, I had to use the next most recent.

However, I was only running PCSX to see if I could get it up and running Ok; my Playstation emulator of choice is [pSX Emulator]("http://psxemulator.gazaxian.com/").  It's superior to the older plugin-based ePSXe and even older PCSX in pretty much every way and is so much easier to install and get running - particularly in Linux.  It's still in active development, too.  And compatibility is far better: the NTSC versions of all three Tekken games run fine, and so do the PAL versions of Tekken and Tekken 3: the PAL version of Tekken 2 doesn't run in the current version, but does in version 1.7.

---

### Post by Buzzdee on 2008-05-10
Thanks for your quick help, I'll give pSX Emulator a try - if someone comes by and knows a solution with pcsx, please feel free to still give answers :)

---

### Post by Buzzdee on 2008-05-10
I downloaded it and installed the (only roughly stated, though) packages it depends on via synaptic. 
"Under Linux pSX requires the following shared libraries/packages :

	OpenGL
	ALSA
	GTK
	GTKGLEXT
	libxml2"
When I try and run the emulator I get the following error though:
"./pSX: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory"
I checked back and installed the ruby packages, too (since I've heard ruby before but don't actually know, if it's needed) for the following result:
Installed packages:
libgtkglext1
libgtkglext1-dev
libgtkglext1-ruby
libgtkglext1-ruby1.8

So, do you know what's missing? By the way, I'm still running on gutsy x86.

Thanks for your help.

---

### Post by Buzzdee on 2008-05-10
I found a thread in the official forums where acoustibop also posted. but as far as I can see, no solution has been found there by now. It somehow seems to be a x86 library problem.

---

### Post by Buzzdee on 2008-05-10
So, I finally got it to run!
Here is what I did, for all users to follow:

I wanted to run pSX on my Ubuntu Gutsy x86 machine to play my beloved Tekken 3. Fortunately, a tekken 3 image and a BIOS image called "SCPH1001.BIN" fell off a trailor, so I was ready to go. I downloaded pSX from this website: [http://psxemulator.gazaxian.com/](http://psxemulator.gazaxian.com/) (Thanks to acoustibop here)
Then I had to additionally install libgtkglext1 via synaptic. 
Further, the libraries mentioned on the below website were downloaded and extracted into /usr/lib32 (root protected, use "sudo file-roller", then "open" archive):
[http://www.geekbin.net/main/content/psx-fixed-amd64-users](http://www.geekbin.net/main/content/psx-fixed-amd64-users)
Then I ran "sudo ldconfig" and started pSX via the executable. It asks for a language, a BIOS and then you're ready to go. 

Enjoy!

---

### Post by acoustibop on 2008-05-10
Ah!  Had you said you were using a 64bit OS, Buzzdee, I would have pointed you towards dreer's excellent thread, [How-To: install pSX on AMD64/i386]("http://ubuntuforums.org/showthread.php?t=394097").

---

