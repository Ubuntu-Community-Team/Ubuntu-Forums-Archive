---
title: "Xubuntu Custom Silent Install"
date: 2006-08-09
forum: Desktop Environments
---

### Post by Jeffrey903 on 2006-08-09
Hello,

I currently work at a charity called PC Renew. We take old donated computers (usually about 350 - 600 MHz, 64MB - 128MB RAM, 4 - 10GB harddrives, etc), nuke the harddrives, replace any bad parts, and then install Windows 98 or 2000 on them (we have a deal with Microsoft to do this legally because we are a charity). We then donate the PCs to people who can not afford to buy new ones.

We are currently looking at installing Linux on them instead of Windows. I currently am trying out the Xubuntu Alternate CD on a refurbished computer. The problem is that it takes a long time to install the OS, download and install the updates, install some other programs, and customize the system.

I believe that I finally have gotten my one test system to how we want it, and I was wondering if there was anything I could do to automate the entire process for future computers? I was hoping that I could make a CD (or DVD if I have to) where basically I could pop it to the computer, and with minimal interaction from a human it would install it to how I wanted.

Is this possible, and if so, how would I go about doing it? I do not know much about the Linux command line.

Thanks for your help in advance.

---

### Post by maniacmusician on 2006-08-09
you could look at something like partimage ([http://www.psychocats.net/ubuntu/partimage.html)](http://www.psychocats.net/ubuntu/partimage.html)). It's a little bit like ghosting on windows. I was going to try it at one point but since it was only a one time thing for me so i just decided to reinstall the OS on another computer. One concern I had when doing it was that Xubuntu wouldn't automatically recognize the different hardware in the computer. Then someone suggested to me that it could probably be fixed easily with running "sudo dpkg-reconfigure xserver-xorg" in terminal. 

So, I think for you, this is a viable solution.

---

### Post by dubbreak on 2006-08-09
As maniac musician said you should be able to just use an image and copy it to various harddrives. Linux is very good at dealing with different hardware (as oppose to windows in my experience). Also as noted reconfiguring xorg will most likely be needed. You could set-up your base image file to use a generic video drive (vesa or whatever) with a reasonable screen resolution (1024x768 @60hz seems pretty safe, if super paranoid about old monitors run 800x600).

---

