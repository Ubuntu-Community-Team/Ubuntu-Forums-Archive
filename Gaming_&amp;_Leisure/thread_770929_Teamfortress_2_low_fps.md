---
title: "Teamfortress 2 low fps"
date: 2008-04-27
forum: Gaming &amp; Leisure
---

### Post by imaniman on 2008-04-27
i cant seem to get any higher than 20fps on team fortress 2 on my computer im running:

Ubuntu Hardy 8.04 amd64
Nvidia 7600GT
Nvidia 7600GT

Its really frustrating i actually have 2 nvidia 7600gt's installed running on sli steam is working fine, it took me a while to get it running at 20fps before that it was between 5-10

I am currently running it from steam with the launch options set to 
-gl dxlevel 81 -window -w 800 -h 600


If i run glxgears it says my fps are around 3000
14400 frames in 5.0 seconds = 2879.909 FPS
15494 frames in 5.0 seconds = 3098.787 FPS
15526 frames in 5.0 seconds = 3105.113 FPS

if i run glxinfo | grep version it shows i am using the latest nvidia driver:

server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.3
OpenGL version string: 2.1.2 NVIDIA 169.12

This driver was automatically detected by ubuntu and installed for me. I did search for the driver manually incase it was out of date, but it showed on the nvidia site as the 169.12 being the driver i would have to install anyway so it seems up to date.

If anyone has any advice hints tips anything, seems like i have tried most things.

---

### Post by FrozenFox on 2008-04-27
Im getting 8,200 fps on glxgears on an fx5950 with max settings in nvidia-settings, and got similar stuff when i used ubuntu. So yeah, its a video driver problem. Perhaps try installing the new beta 173.08 drivers manually and see if you have any luck.

---

### Post by imaniman on 2008-04-27
thanks, well i tried the new driver and it installed fine but when it rebooted into X it showed nvidia logo etc but didnt work it went to some default settings and didnt recognise it properly.

Managed to reinstall the original driver and everything is back where it was, sadly still low fps.

I guess its just waiting for a new driver?

Unless there is anything else i can do.

---

### Post by noerrorsfound on 2008-04-27
I've got the same video card (mine's actually a 7600 GT KO, but it's probably not that different) with the same driver version, and have better performance in glxgears.

server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.3
OpenGL version string: 2.1.2 NVIDIA 169.12
nef@nef-desktop:~$ glxgears
47687 frames in 5.0 seconds = 9537.263 FPS
50055 frames in 5.0 seconds = 10010.968 FPS
50489 frames in 5.0 seconds = 10097.800 FPS
50043 frames in 5.0 seconds = 10008.428 FPS
50042 frames in 5.0 seconds = 10008.396 FPS
50454 frames in 5.0 seconds = 10090.750 FPS
50075 frames in 5.0 seconds = 10014.832 FPS

This is with only one video card, too.

---

### Post by imaniman on 2008-04-27
hmm well i dunno what to do im using the same driver.

Can i see your xorg.conf? or anything other graphics related settings?

---

### Post by imaniman on 2008-04-27
eh just had a thought i recently bought a 500gb sata hd and installed it.

My pc only has a 500w power supply i'm thinking that may have reduced the performance of my graphics cards.

I havent actually tested it on windows since i added the hd but if i get the same performance then i prolly need a better psu.

---

### Post by imaniman on 2008-04-28
ok well it was just a thought about my psu but i guess i was wrong.

I booted back into windows and run team fortress 2 and i get 60fps at 1280x1024

compared to my 20fps on ubuntu at 800x600

so it must be some kind of configuration im missing.

Ubuntu - 20fps - 800x600
[http://imaniman.com/myspace/temp/Screenshot.png](http://imaniman.com/myspace/temp/Screenshot.png)

Windowx - 60fps - 1280x1024
[http://imaniman.com/myspace/temp/cp_badlands0000.png](http://imaniman.com/myspace/temp/cp_badlands0000.png)


bah can anyone help

---

### Post by Sleaka J on 2008-04-28
I get about 4,500fps running glxgears and I have Ubuntu 8.04 Hardy 32-bit running an nVidia GeForce 7600GS with the 169.12 drivers.

Under Windows I can get quite good fps at 1024x760 4xFSAA at High/Very High detail. However under Linux, my performance is so bad I can't play, even on low detail. It stutters and jumps around, making online play impossible.

I'm getting the feeling it's just a problem with Wine, as I can run the Linux Enemy Territory: Quake Wars client at exactly the same detail level as the Windows ET:QW client and get exactly the same fps in both. That's telling me the drivers are working fine.

For the time being, I run TF2 from my Windows XP install. If it aint broke, don't fix it.

"Need a dispenser here"

---

### Post by xionxgp on 2008-04-28
at least you can play tf2 on ubuntu 8.04 i cant even get it to run, the valve loading screen comes up , but when it goes to the main menu it just quits. i dont know if this matters for my issue but i have a radeon X1600 pro , and get about 6000 fps in glxgears

---

### Post by Sleaka J on 2008-05-12
> **xionxgp said:**
> at least you can play tf2 on ubuntu 8.04 i cant even get it to run, the valve loading screen comes up , but when it goes to the main menu it just quits. i dont know if this matters for my issue but i have a radeon X1600 pro , and get about 6000 fps in glxgears

Add a launch option to TF2: -window

I've got it working at playable speed now, but had to use the -dxlevel 81 option to get ok framerates. It's a real pity that it doesn't work properly using DirectX 9.0c. That's a real killer for me.

I had the same problem you did. A black screen after the Valve and Source intro movie ran. -window launch option at least gets me to the main menu where I change back to fullscreen in video options.

While I have it working under Wine, I don't play it under Wine. I still use my Windows XP install to play TF2. Getting it working under Wine was just a test for me.

---

### Post by NR1224 on 2008-05-13
2 things, first i assume youre running in wine, which isn't know for having the best frames compared to windows. 2nd, i wasnt aware that sli worked in linux, maybe it does, but i have heard that it doesnt support sli. Maybe thats part of the problem?

---

### Post by 1337 on 2008-05-13
Try turning OFF Compiz Fusion that should be a quite noticible FPS gain I guess.

Regards

---

### Post by Frem on 2008-05-15
What he said. Also, running full screen.

---

### Post by killguta on 2008-09-12
I have the same problem, even with the directx level trick and the compiz off and fullscreen it doesn't work :( .

---

