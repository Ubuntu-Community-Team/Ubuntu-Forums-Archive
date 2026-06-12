---
title: "Steam Ubuntu 14.04 Metro 2033 Redux"
date: 2014-12-13
forum: Gaming &amp; Leisure
---

### Post by bio2 on 2014-12-13
SO I just bought Metro 2033 redux and when I click play it gives me 2 options.
1. Play Metro 2033 Redux
2. Launch
I click on option 1 and then a popup says "OpenGL 4.0 or later has not been found. Please make sure that your video card and driver support OpenGL 4.0"
So I click "close"
I then try option 2 , launch, and it gives me the missing executable error. I try going on steam support to do whatever they say to do in a missing executable error.
Same results.
I try reinstalling.
Same results.
I try disabling the steam overlay.
Same result.
Plz Help!

---

### Post by DanglingPointer on 2014-12-14
What sort of hardware have you got?

---

### Post by bio2 on 2014-12-14
i5 core, amd graphics card on my motherboard hp probook 4540s

---

### Post by DanglingPointer on 2014-12-14
Sorry to break it to you mate but it doesn't look like your hardware cuts it.
Your probook uses the i5's HD 4000 graphics which isn't capable enough for Metro Redux.

I used this site to view your specs and underneath is an image of the minimum and recommended requirements for Metro Redux... [URL="http://www.cnet.com/products/hp-probook-4540s-15-6-core-i5-3210m-windows-7-pro-64-bit-4-gb-ram-500-gb-hdd-series/specs/"]
http://www.cnet.com/products/hp-probook-4540s-15-6-core-i5-3210m-windows-7-pro-64-bit-4-gb-ram-500-gb-hdd-series/specs/[/URL]
[ATTACH=CONFIG]258567[/ATTACH]

---

### Post by bio2 on 2014-12-14
WT@ Thats is not true ALL MY OTHER GAMES like cod advanced warfare work!
If you could tellme how to install open gl?

---

### Post by bio2 on 2014-12-14
i looked at the site 2. My computer came with like 12-16 gb ram with windows 8 preinstallled. I switched to ubuntu and deleted windows 8 then i dual booted a 32bit version of windows 7 which is corrupt cos my computer is 64bit and windows 7 is takiing up more ram than usual. How do i delete windows 7 completely without damaging my ubuntu?

---

### Post by DanglingPointer on 2014-12-14
Hi bio2, all those other games you mentioned (like Advanced Warfare) were played on Windows via DirectX11.  Unfortunately Intel hasn't updated the Linux driver for the HD 4000 up to OpenGL 4.x standard.  The hardware can theoretically perform the task but unfortunately there is no API available yet.

My recommendation for games like Redux, get a desktop rig with a discreet card.  Or build a steamMachine.

---

### Post by deathapunu on 2014-12-14
Could you provide us with the contents of the below command. This might make it easier for us to assist you.

glxinfo | grep OpenGL

You may need to install mesa-utils for this.

sudo apt-get install mesa-utils

---

### Post by dannyboy79 on 2014-12-15
maybe try out the latest development of mesa and the i915 driver but you're not going to get many FPS outta an internal gpu, especially with intel.  you can get it from xorg-edgers i believe

---

### Post by bio2 on 2014-12-16
This is what I get when i typed the command in.
killjoy@killjoy-HP-ProBook-4540s:~$ glxinfo | grep OpenGL
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile 
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.1.3
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 10.1.3
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:

---

### Post by dannyboy79 on 2014-12-16
yeah that's an older version of mesa/opengl. i would suggest trying out xorg-edgers ppa

---

