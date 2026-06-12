---
title: "Inspiron 1720 Nvidia woes"
date: 2007-08-10
forum: Dell  Ubuntu Support
---

### Post by rboone on 2007-08-10
Hi,

Jut got a new Dell Inspiron 1720 with Nvidia Geforce Go 8400 card.  I'm unable to get the nvidia drivers to work.  Anyone have any suggestions?

I've tried installing via apt-get the nvidia-glx, nvidia-glx-new, and nvidia-glx-legacy drivers but none of them work.  I've tried dowloading the latest drivers from nvidia (NVIDIA-Linux-x86-100.14.11-pkg1.run) and then did:

apt-get install linux-headers-`uname -r`

went through the kernel compilation steps with the NVIDIA*.run 
package and it didn't complain.  But when I try to start X, it tells me
there are no Nvidia GPUs, and/or kernel module does not match.

Been trying for about 6 hours to get something beyond 800x600
(system supports 1900x1280 I think).  

Suggestions?
Thanks in advance,
Rog

---

### Post by rboone on 2007-08-11
Some success but not very nice.  Oh, I forgot to mention in my earlier post, this is Ubuntu 7.04 and kernel 2.6.20-16-generic.

I used the Envy script to install the driver (the same one I was ttrying to install manually above).  I'm able to set the nvidia resolution, but if I attempt to save that to xorg.conf (via ndvidia-settings), the next time I reboot, I'm unable to get back to the desktop.  I login and then the screen goes black and I have to boot in recovery mode to restore
my original xorg.conf.

If, however, I revert back to the original xorg.conf (that did not have my 1680x1200 resolution info saved), then when I login, the screen goes black and after a few seconds will return me to the login screen again (I do see the Nvidia logo screen a couple of times though).

If after a couple of attempts to login,   
I  then choose "Gnome" from the sessions list (rather than "Last Used" (which was Gnome as well), I can get to my desktop (800x600).  I can then set the res to 1680x1200 or whatever and work for that session.

Thoughts anyone?  Thanks,
Rog

---

