---
title: "Window/Application - 'Appearance' corruption"
date: 2010-06-23
forum: Desktop Environments
---

### Post by Pixtu on 2010-06-23
I have a problem (corruption) with the 'appearance' of some applications when using Emerald/Compiz. I have attached 2 screenshots to show the problem. The first (compiz-1.png) shows the 'corruption' on the row/column numbers and menu bar, when using Compiz. The second image (compiz-2.png) shows the same application having switched to Metacity, without the 'corruption'.

It doesn't appear to be affecting all applications - 2 that I know of are Open Office and Wine.

Although the problem is not affecting the Window border management, if I switch to Metacity from Compiz everything is OK (although obviously I can't then use the various effects that come with Compiz).

I am using 32 Bit Ubuntu 10.04 (Lucid) on a Sony Laptop (Intel Mobile CPU), with nVidia graphics, although I also had the problem with 09.10 and hoped it would be solved by updating. However, I had previously been able to use Compiz without any problems.

What is even stranger is that I also have a deskside PC (although this is AMD rather than Intel) which also has nVidia graphics. I have used both 32 bit and 64 bit Ubuntu 10.04 on this with the same applications and Emerald/Compiz theme.

So, although I have re-installed my Laptop, I assume that I have somehow corrupted some settings somewhere, but can't see what/where this may be.

Can anyone offer any ideas on where to look, or actually solve  this problem.

Update:
I have found a solution which would indicate that there may be a proble with the latest nVidia driver on Sony Laptops.

It appeared that I had not installed the nVidia driver correctly, so I re-installed and the 'Hardware Drivers' indicated that I was using the 'Version Current - Recommended' nVidia driver. This, in itself, did not resolve the display corruption. However, I then selected the 'Version 173' nVidia driver and I no longer see any corruption with the display.

---

### Post by swiftsam on 2010-11-18
Thanks so much for posting this.  I'd been coping for a while by resizing the windows and zooming in and out which would fix the problem for a while.  Switching the NVIDIA driver from Recommended to 173 seems to have fixed it.

For reference, the problem only affected open office and wine for me.  A screenshot of how things looked before the fix is below.

---

