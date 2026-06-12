---
title: "Need help using my Epson CX5400 scanner..."
date: 2009-04-07
forum: General Help
---

### Post by scampy on 2009-04-07
I am literally going crazy figuring out how to get my Epson Stylus CX5400 scanner/printer to work.  I am running Ubuntu 7.04 Feisty Fawn x386.  Could someone PLEASE tell me step-by-step how to get they system to recognize the device.  BTW, when I type 'sane-find-scanner' in the terminal, I get the following:    

# sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

found USB scanner (vendor=0x04b8 [EPSON], product=0x0808 [USB MFP]) at libusb:001:004
found USB scanner (vendor=0x046d, product=0x0850) at libusb:001:005
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
     As you can see, my scanner appears after I execute that command in the terminal but, when I run XSane, it keeps on saying that I have some Logitech scanner or whatever.  This is VERY VERY perplexing!  Any help by anyone would be greatly appreciated!  Thanks in advance!:-k

---

### Post by scampy on 2009-04-07
*Bump*

---

### Post by scampy on 2009-04-07
Well, after doing a whole bunch of reading of a bunch of different webpages, I finally found the solution!  The solution was that the make and model of my device wasn't listed in the epkowa.conf and/or the epson.conf file which are located in the /etc/sane.d/ folder.  I figured out how to solve the problem from [http://ubuntuforums.org/archive/index.php/t-286164.html](http://ubuntuforums.org/archive/index.php/t-286164.html).
     Even though I am very happy to have found the solution to the problem, it is still very disapointing that a whole bunch of tinkering had to be done just to solve the problem.  Just like the final post in that thread said, it is that kind of stuff that keeps Linux from being more popular.  See, most people aren't as capable and/or willing to go to such a bother to fix something like that.  Most people(aka sheeple) just want things to work 'right out of the box.'  Indeed, Linux needs to start sorting out this kind of stuff if it ever wants to gain an even bigger market share.  
     I am not saying all this because I like Windows.  Apart from a _FEW_ programs that run under Windows, I do not like Windows at all.  I am just giving one of the reasons why Windows is way more popular.  It's just some food for thought, in other words.

---

