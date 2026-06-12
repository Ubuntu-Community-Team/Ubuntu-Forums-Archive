---
title: "How to stop modem connecting during boot."
date: 2006-01-03
forum: Desktop Environments
---

### Post by km4hr on 2006-01-03
My modem recently starting connecting when I boot my computer. It didn't always do that.  I think it started after I tried connecting my (external) modem to the computer using USB instead of the serial cable. I never had any success getting the USB connection to work but after re-connecting the serial cable I noticed that the modem now connects while the computer it booting. Some other Linux disto's have a check box in the network configuration screen that allows you to indicate if you want the modem activated during boot, but I don't see that option in Ubuntu's network screen. Any ideas?

---

### Post by granny4linux on 2006-01-04
I have not used the Ubuntu networking program for awhile, I think this happened to me. Go to System>Administration>Networking>Properties>Options and  uncheck "retry if the connection breakes or fails to start"

I've since discovered Gnome PPP and prefer it; give it a try. It is available in Synaptic,

Good luck.

---

