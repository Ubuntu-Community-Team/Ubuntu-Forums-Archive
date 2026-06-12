---
title: "VMWare Ubuntu Under Linux Host?"
date: 2006-08-16
forum: Desktop Environments
---

### Post by FR47 on 2006-08-16
Hello, all -

Due to various reasons that would take too long to explain, it is impractical, if not impossible, for me to repartition my laptop for Linux at this time, and I can't afford to go without Windows XP, either.  However, I'm a big Linux fan and tend to like the user environment (I'm a computer science student so in some ways I'm right at home with it).  I have access to VMWare Workstation 5.5 for Windows.  Essentially, I was wondering if it's a waste or not to try to run desktop Ubuntu under it as my "main" environment, breaking out to Windows only when I need it for something such as 3D games.  I've already set up Ubuntu to work under it and it works pretty well.  

In terms of raw computational speed it seems comperable to CoLinux though it suffers a significant degredation of disk I/O performance.  Further, its graphical performance leaves something to be desired, swap file usage is excruciating (though I speculate there may be ways around that) and 3D support is out of the question for now.

Ultimately - am I just wasting my time, RAM and CPU cycles?  My laptop is pretty beefy - Core Duo 1.8 GHz and 1 GB of RAM, about 720 megs of which I assign to the VM while it's in use.  However, I can't escape the feeling that I could be putting these resources to better use running just straight XP.

I've considered running a stripped down Ubuntu and using a VNC or Xming to access it via a virtual network connection, possibly increading performance, but I haven't tried it yet, and I don't know if it would actually improve anything.

Anyway, thank you very much for your opinions on this and any experiences you can give me regarding this.

---

### Post by jimcooncat on 2006-08-29
I use xming at work (from a different machine) and like it a lot for it's performance. Be sure to install a font server on the Ubuntu vm and set up xming to use it. It's not a 100% bug-free solution though.

Doesn't VMWare come with it's own viewer?

Regarding your setup -- I can't imagine swap slowing you down with 1GB of RAM. I'd try lowering the RAM you reserve for the VM -- Ubuntu will run great in 400 MB or so. Maybe it's the Windows swapping out. Don't know, just a guess.

I'd imagine the disk I/O would be slow, there's no chance to use a native Linux partition on the machine for the VM?

---

