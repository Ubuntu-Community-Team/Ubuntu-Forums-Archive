---
title: "unity not working. switched to gnome"
date: 2011-09-16
forum: Desktop Environments
---

### Post by bobthe on 2011-09-16
When I first logged into Ubuntu, I got a message something like that I didn't have the hardware for Unity to work..and I just recently bought this laptop: hp dv6-6135dx, AMD A8, Quad Core and radeon dual graphics.

Any idea on why it isn't working?? and also, the boot time is really long. like it takes longer than any of my other ubuntu machines as well. any explanation on this?

Please help!

---

### Post by Frogs Hair on 2011-09-16
Try installing the recommended proprietary graphics driver from additional drivers . I received the same message until the driver was installed. I have an Nvidia graphics card. I don't know why you have a long boot time though .

---

### Post by Nutria on 2011-09-16
> **bobthe said:**
> also, the boot time is really long. like it takes longer than any of my other ubuntu machines as well. any explanation on this?

Probably some network timeout.

Since it's a laptop, maybe it's scanning for something wireless?

---

### Post by Blasphemist on 2011-09-16
You have switchable graphics and I think this is still a problem in Linux. Please google these two projects, bumblebee and debumblebee. There are people working on getting switchable graphics to work on Linux and I don't know just what the state of that effort is right now. The deal is that you have 2 gpu's.

---

### Post by walt.smith1960 on 2011-09-16
> **Blasphemist said:**
> You have switchable graphics and I think this is still a problem in Linux. Please google these two projects, bumblebee and debumblebee. There are people working on getting switchable graphics to work on Linux and I don't know just what the state of that effort is right now. The deal is that you have 2 gpu's.

Isn't bumblebee for the Nvidia/Intel Optimus or whatever it's called? The O.P. has AMD Radeon but installing proprietary drivers still seems like a good idea. AMD/ATI graphics support for recent devices is supposed to be improving.

---

### Post by Blasphemist on 2011-09-16
Good catch Walt! I did look at this site (link at the end of the text) and here is what it says for the status of the ati hybrid.
> ATI hybrid:
The PowerXpress pre-4.0 models have a mux solution to switch between
discrete and integrated card.
For most ATI/Intel hybrid configurations:

a) try the latest closed-source Catalyst Driver for login/logout card switching,
 or
b) try vga_switcheroo and open-source graphics drivers (kernel 2.6.35 or newer).

The PowerXpress 4.0+ models have a muxless solution to use both cards
and switch on/off the discrete card.
For Muxless PowerXpress 4.0+ models, please submit your DSDT tables
information as described here:
[http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)
Here is the ubuntu doc on vga_switcheroo.
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

---

