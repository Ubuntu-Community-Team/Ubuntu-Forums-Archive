---
title: "&quot;Cannot display this video mode&quot;?"
date: 2006-06-19
forum: Desktop Environments
---

### Post by rchesterton on 2006-06-19
I installed Ubuntu onto my Shuttle yesterday, using a CRT monitor, and all was well.

The problem occurred when I brought the Shuttle into work today and connected it to a TFT.

I think the problem is because of the refresh rate, which would have been set higher than 60Hz for my CRT.

Because of this, I get "Cannot display this video mode" as soon as it gets to the login screen (although I can see this screen if I plug it into a higher-res panel, but get the "Cannot display this video mode" message as soon as I logon).

I understand that the login screen only displays on the higher res screen due to a 'bug' whereby the res of this screen is higher? i've seen an article on how to sort this, so am not too worried about that.

Could someone tell me how i can change my refresh rate/resolution?  I can't get to the GUI, so assume I would need to do it in the 'Reecovery Mode' that is offered in the boot menu?

A step-by-step would be good as I am fairly new to Linux.

Thanks
Richard

---

### Post by cskeide on 2006-06-19
Switch to console mode with Ctrl+Alt+F1, then run the following command after logging in.
```
sudo dpkg-reconfigure xserver-xorg
```
You should be able to change the refresh rate from there.

---

### Post by rchesterton on 2006-06-19
Thanks cskeide :)

Worked a treat.

---

