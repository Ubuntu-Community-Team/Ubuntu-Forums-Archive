---
title: "X only starts with glx removed"
date: 2006-01-14
forum: Desktop Environments
---

### Post by newclique on 2006-01-14
I compiled the latest ATI drivers for my 9250 and got X working at 1280 on my LCD screen. Yippee! :p However, being pretty new to all of this, I don't understand how all the pieces fit together yet. :???: My main obstacle for 2 days to getting X to start was the glx module. Once I removed it, it starts.

But I need glx, right, for 3D support? So...my questions are these: What is the likely culprit for this not starting and what other pieces might I need to have installed to make it work. Mesa? Is that what provides OpenGL services? Is it included in the latest Ubuntu distro by default? Does it require kernel recompiling?

And what is ati-glx? Is that a seperate module I need to apt-get?

Thanks! I want to get Wine running as well as games, etc. so I assume I need to get glx to load.

Edit: I discovered that fglrx was not being loaded during boot so I added it to /etc/modules. It seems to load. Now, do I replace driver="ati" with driver="fglrx" in my xorg.conf file?

(BTW, I have seem the friendliest posts on the Ubuntu forums compared to other 'haughty' distros' forums. This has been a major attraction for me to come to Ubuntu. Keep it up!)

---

### Post by newclique on 2006-01-30
For anyone completely frustrated with trying to get all of their hardware to work with Ubuntu, I would urge them to try another distro's live eval CD to see what their results are. I sank probably 50 hours into Ubuntu trying to simply get 3D support with an ATI 9250 and 8500DV to no avail. First boot of a live eval of PCLinuxOS ([http://www.pclinuxos.com/](http://www.pclinuxos.com/)) came up with full glxgears running and fglrxinfo showing my card handling direct rendering.

Heed a warning from someone who gave this distro every opportunity: shop around.

---

