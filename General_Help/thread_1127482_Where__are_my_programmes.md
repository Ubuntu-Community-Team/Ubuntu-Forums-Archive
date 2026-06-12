---
title: "Where  are my programmes?"
date: 2009-04-16
forum: General Help
---

### Post by chris301up on 2009-04-16
****Hi

I am fed up with Windows so now have installed Ubuntu 8.10 on a spare machine so that I can experiment with it.

Since I installed Ubuntu I have been unable to get my CD/DVD to play audio cd's or dvd's. Can anyone please advise?

Also, I have just installed a couple of programmes using Wine, but the installation did not place any icons on the desktop.

I have searched for these programmes but cannot find them so can anyone tell me where these may have installed to?

---

### Post by jmszr on 2009-04-16
chris301up,

First open the Terminal: Applications > Accessories > Terminal and type or copy and paste :```
sudo apt-get install ubuntu-restricted-extras
```
Press Enter
Note: When you enter your password it will not be visible. Thats OK (security).
This should take care of the CD/DVD problem. When the Java license comes up press Tab to OK it and then press Enter. 

The programs you installed via Wine should be under Applications > Wine > Programs, To put an icon on the desktop right click on the program after extending it out to the right (you'll see what I mean) and then left click on: extend this launcher to desktop.

---

### Post by chris301up on 2009-04-16
:)Thanks for your reply.

I have done exactly what you have stated but still no success. Have also tried the libdvdcss2 from Medibuntu but that won't work either.

Cannot find my programs either so I must be doing something wrong!

Also how can I access my floppy drive and my C drive?

---

### Post by oldos2er on 2009-04-16
To play commercial DVDs, you will need to install libdvdcss2 from the Medibuntu repository. Medibuntu is not enabled by default. See [http://medibuntu.org/](http://medibuntu.org/)

---

