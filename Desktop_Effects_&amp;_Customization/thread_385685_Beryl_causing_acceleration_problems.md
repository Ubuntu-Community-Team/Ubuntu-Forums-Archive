---
title: "Beryl causing acceleration problems"
date: 2007-03-16
forum: Desktop Effects &amp; Customization
---

### Post by kevinf311 on 2007-03-16
Hello all. 

I've been using Beryl version .1.99.2 for awhile with no problems whatsoever. When .1.9999.1 came out I upgraded but everything broke, so I forced version .1.99.2 again. A couple of days ago I wanted to change my theme and noticed that the themer was still in .1.9999.1

I decided that I should install the .1.9999.2 updates that had been sitting in my system tray for a few weeks. After installing the updates I noticed some strange going ons. When I'd go into cube mode (I have two monitors set up for the "use two cubes"  option) the secondary monitor would draw the windows on the first monitor off to the left of the second cube (in "space"). In addition to that, when I'd switch desktops/viewports the window would be out 3D and then snap to the desktop instead of zooming out. A similar loss of frame would happen with my animations.

I got the idea that maybe my video card driver was messed up. I opened up glxgears and it was running all choppy and bad. If I dropped back to metacity, glxgears would run smoother than a well lubricated V8. I decided to reinstall my driver anyway, but to no avail, after reinstalling the driver and beryl a couple times, I ended up kernel panicking and decided a fresh install was in order.

So, after a painless install and update I found that the .2.0 version of Beryl had been released. I decided to give that a go and installed from the ubuntu.beryl-project repo. I was impressed by the new settings manager look, even better than .1.9999.2, unfortunately the same lack of acceleration issues came with it. 

My specs are:
AMD socket 939 3200+ processor
1GB PC2700 RAM
nVidia 7600GT 256MB (pci_e) video card
Edgy

I'm attaching the important parts of my xorg.conf file and the output of glxinfo. Let me know if there is something else that would be helpful.

Thanks in advance for your help.

P.S. I'll check out the Beryl sites forum, too, but I don't like the layout as much as here ;)

[edit]

Well, I had a nice long informative edit but I had to lose it. I was going to update my xorg.conf file and also attach the result of glxinfo whilst Beryl was running. Unfortunately in my workings last night I had installed Compiz, which froze upon opening. For some reason my Beryl-manager wanted to default to the Compiz wm, which froze and I had to restart x. So, pending I still have the updated xorg.conf file I saved, I will upload that. The glxinfo will not be available until I reinstall Beryl.

After making these changes to the file, I still experienced the same lack of acceleration and strange drawing.

[edit 2]

I decided to give Ultimate Ubuntu a try, since it is built of Edgy and shoud recognize my /home partitions organization. Beryl broke even worse. So, I came to the conclusion that there was something in my /home partition (config file) that was borking Beryl. After a quick DVD back-up of my /home partition (music, documents, etc) and a fresh complete install, I was back on my way. I started up Beryl again, but after some configuring, I am getting the same problems as before. The only difference is that the result of glxinfo when Beryl is running now says "yes" for Direct Rendering. I shrank down the distance that the windows rise out from the cube to keep that frame drop issue less noticible. 

The benchmark plugin claims around 650 Frames/sec on the desktop and then drops to about 100 Frames/sec in cube mode. 

If anyone has all the debs for Beryl version 0.1.99.2 I would be forever grateful to you if you could give me a copy of them.

[edit 3]

So I'm on Sabayon Linux now. Beryl works. I wish I knew why as aside from formatting, the xorg.conf files are almost Identical. Sabayon, like Ultimate, uses the latest nVidia beta drivers. All I know is that it works without dropping frames. The strange window draw when in cube mode still happens, but I am assuming that that is just a bug in the multiple cube option. If anybody wants, I can post the Sabayon xorg.conf file for some option pointers.

I'll be back to Ubuntu once Feisty becomes completely stable.

---

