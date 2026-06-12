---
title: "Gaming graphic quality is so bad"
date: 2021-05-26
forum: Gaming &amp; Leisure
---

### Post by veerverma007 on 2021-05-26
I am using ubuntu gnome version and tried other too like kubuntu and many other distro i have a problem in which when i run game its works fine but the graphics are so bad i tried both steam and wine games and linux native game too such as supertuxkart this issue is not occur when i am using linux mint and when i run games in past it worked fine but now its make game unplayable i request to give me some solution for this.:) wait for your reply eagerly.

---

### Post by ajgreeny on 2021-05-26
We need to know a lot more about your hardware and software so please for a start run terminal command ```
inxi -Fzx
```

You may have to install **inxi** in order to do this but I think it is a default in Ubuntu now so try first.

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by mastablasta on 2021-05-26
well not much information to go on here. so see this first: [https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)

and in the mean time what does it mean graphics are so bad? define bad? you get atrefacts? screen is flickering? resolution is low? you see squares in the lines? the look quite well to me. my kids have a much better PCs than i do (GPU wise at least). and their graphics are quite good. they play on HD resolution. they have native steam games, wine games and games via proton. most GPU intense i saw so far is Doom 2016. but Subnautica, Bioshock infinite though with older engines all look great.

---

### Post by veerverma007 on 2021-05-26
Thanks for reply,

the terminal output is-

[COLOR=#000000]```
[/COLOR]
System:
  Kernel: 5.8.0-53-generic x86_64 bits: 64 compiler: N/A 
  Desktop: Gnome 3.36.7 Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:
  Type: Laptop System: LENOVO product: 80G0 v: Lenovo G50-30 
  serial: <filter> 
  Mobo: LENOVO model: Lancer 5A6 v: NANANANANO DPK serial: <filter> 
  UEFI [Legacy]: LENOVO v: A7CN23WW date: 03/26/2014 
Battery:
  ID-1: BAT0 charge: 12.1 Wh condition: 17.3/31.7 Wh (55%) model: Lenovo 
  status: Discharging 
CPU:
  Topology: Quad Core model: Intel Pentium N3530 bits: 64 type: MCP 
  arch: Silvermont rev: 8 L2 cache: 1024 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 17333 
  Speed: 1113 MHz max: 2582 MHz Core speeds (MHz): 1: 1209 2: 606 3: 1487 
  4: 2170 
Graphics:
  Device-1: Intel Atom Processor Z36xxx/Z37xxx Series Graphics & Display 
  vendor: Lenovo driver: i915 v: kernel bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.9 driver: i915 resolution: 1366x768~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics (BYT) v: 4.2 Mesa 20.2.6 
  direct render: Yes 
Audio:
  Device-1: Intel Atom Processor Z36xxx/Z37xxx Series High Definition Audio 
  vendor: Lenovo driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
  Sound Server: ALSA v: k5.8.0-53-generic 
Network:
  Device-1: Realtek RTL8723BE PCIe Wireless Network Adapter 
  vendor: Lenovo Z50-75 driver: rtl8723be v: kernel port: 2000 
  bus ID: 02:00.0 
  IF: wlp2s0 state: down mac: <filter> 
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Lenovo driver: r8169 v: kernel port: 1000 bus ID: 03:00.0 
  IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: <filter> 
Drives:
  Local Storage: total: 465.76 GiB used: 31.82 GiB (6.8%) 
  ID-1: /dev/sda vendor: Toshiba model: MQ01ABD050 size: 465.76 GiB 
  temp: 32 C 
Partition:
  ID-1: / size: 456.95 GiB used: 31.82 GiB (7.0%) fs: ext4 dev: /dev/sda5 
Sensors:
  System Temperatures: cpu: 49.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 221 Uptime: 9m Memory: 7.66 GiB used: 1.18 GiB (15.4%) 
  Init: systemd runlevel: 5 Compilers: gcc: N/A Shell: bash v: 5.0.17 
  inxi: 3.0.38
[COLOR=#000000]
```[/COLOR]

---

### Post by veerverma007 on 2021-05-26
> **mastablasta said:**
> well not much information to go on here. so see this first: [https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)

and in the mean time what does it mean graphics are so bad? define bad? you get atrefacts? screen is flickering? resolution is low? you see squares in the lines? the look quite well to me. my kids have a much better PCs than i do (GPU wise at least). and their graphics are quite good. they play on HD resolution. they have native steam games, wine games and games via proton. most GPU intense i saw so far is Doom 2016. but Subnautica, Bioshock infinite though with older engines all look great.


I mean that its like bad pixel quality in game i cant tell you what its like but i upload an image from which you can check what i am talking about.

---

### Post by veerverma007 on 2021-05-26
Is any one here to help me!

---

### Post by coffeecat on 2021-05-26
> **veerverma007 said:**
> Is any one here to help me!

Please do not expect help in real time. Volunteer members of the forum come from many time zones in many countries, and many have real lives to attend to first. It is unreasonable to bump your thread before about 12-24 hours. 

Also, please re-read post #2. ajgreeny asked you to enclose your terminal output between BBCode code tags to make it readable. ajgreeny also referred to a code tag howto in their signature if you need it. There's one in mine too. Please edit your post #4 and enclose the terminal output between code tags.

---

### Post by veerverma007 on 2021-05-26
> **coffeecat said:**
> Please do not expect help in real time. Volunteer members of the forum come from many time zones in many countries, and many have real lives to attend to first. It is unreasonable to bump your thread before about 12-24 hours. 

Also, please re-read post #2. ajgreeny asked you to enclose your terminal output between BBCode code tags to make it readable. ajgreeny also referred to a code tag howto in their signature if you need it. There's one in mine too. Please edit your post #4 and enclose the terminal output between code tags.

Ok,thanks now i edited it.

---

### Post by ajgreeny on 2021-05-26
I see from that **inxi** output that you are using an integrated graphics system on an Intel Atom CPU, probably simply not good enough for gaming.
```
Graphics:
  Device-1: Intel Atom Processor Z36xxx/Z37xxx Series Graphics & Display 
  vendor: Lenovo driver: i915 v: kernel bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.9 driver: i915 resolution: 1366x768~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics (BYT) v: 4.2 Mesa 20.2.6 
  direct render: Yes 

```
It may be good enough for some low resource gaming but for many other games, I suspect not; I am not a gamer so I can not give more detailed info about this so wait for other people to comment.

---

### Post by mastablasta on 2021-05-27
is this your laptop?
> **[B]Lenovo G50 30** Full **Specifications**[/B][COLOR=#202124][FONT=arial]
[LIST]
[*]General. Brand. **Lenovo**. Model. ...
[*]Display. Size. 15.60-inch. ...
[*]Processor. Processor. Intel Pentium Quad Core 4th Gen N3540. ...
[*]Memory. RAM. 4GB. ...
[*]Graphics. Graphics Processor. Intel Integrated Graphics. ...
[*]Storage. Hard disk. 500GB. ...
[*]Connectivity. Wi-Fi standards supported. 802.11 ac. ...
[*]Inputs. Web Camera. 0.3-megapixel.
[/LIST]
[/FONT][/COLOR]


you won't really be able to game with this one, however supertuxcart should still work nicely and look good on this one. this could a bug of sorts. are other games also giving you issues? 

> 
[LIST]
[*][COLOR=#252525]Processor Graphics ‡[/COLOR][COLOR=#003C71]Intel® HD Graphics for Intel Atom® Processor Z3700 Series[/COLOR]
[*][COLOR=#252525]Graphics Base Frequency[/COLOR][COLOR=#003C71]313 MHz[/COLOR]
[*][COLOR=#252525]Graphics Burst Frequency[/COLOR][COLOR=#003C71]896 MHz[/COLOR]
[*][COLOR=#252525]Graphics Max Dynamic Frequency[/COLOR][COLOR=#003C71]896 MHz[/COLOR]
[/LIST]


slow, but should still be able to do some light gaming. old games (like source engine based ones, games from arround 2005-2010) should be playable on low settings. 

i don't know much about intel graphics, but you can try a few simple things:
1. switching to old xorg instead of wayland (at login)
2. run game sin full screen mode. i believe Ubuntu now also has a system settings option that will suppress special desktop effects when programs (games) run in full screen. special desktop effects can interfere with GPU usage and reduce it's efficiency. 
3. check how much ram the GPU has reserved in BIOS. Maybe increase that to 1 GB at least. 
4. Intels (especially a bit older ones)  behave quite differently when they are on battery or if they have power plugged in. it gives them a major boost. so make sure power is plugged in when you game.
5. check system settings and make sure any power management settings and such are boosted for performance when you play games. 
6. play arround with game settings a bit. resolution, view distance, antialiasing, vsync, special effects etc. all have some effect on GPU usage. and they might not have a big effect on game if you reduce some or increase some. lliek for example in CS:GO you can actually see the enemy better if you reduce some settings to low. so pros would have these gaming machines and they would set resolution and almost everything to low.
7. you can also try a lighter more 2D oriented desktop (such as Lubutnu. Xubuntu) to conserve your small resources and use them for gaming instead. for example i have a netbook with Kubuntu but the desktop is set to that it uses some old openGL and does not look as fancy. but this creates more resources for applications and games.

---

### Post by veerverma007 on 2021-05-27
> **mastablasta said:**
> is this your laptop?


you won't really be able to game with this one, however supertuxcart should still work nicely and look good on this one. this could a bug of sorts. are other games also giving you issues? 



slow, but should still be able to do some light gaming. old games (like source engine based ones, games from arround 2005-2010) should be playable on low settings. 

i don't know much about intel graphics, but you can try a few simple things:
1. switching to old xorg instead of wayland (at login)
2. run game sin full screen mode. i believe Ubuntu now also has a system settings option that will suppress special desktop effects when programs (games) run in full screen. special desktop effects can interfere with GPU usage and reduce it's efficiency. 
3. check how much ram the GPU has reserved in BIOS. Maybe increase that to 1 GB at least. 
4. Intels (especially a bit older ones)  behave quite differently when they are on battery or if they have power plugged in. it gives them a major boost. so make sure power is plugged in when you game.
5. check system settings and make sure any power management settings and such are boosted for performance when you play games. 
6. play arround with game settings a bit. resolution, view distance, antialiasing, vsync, special effects etc. all have some effect on GPU usage. and they might not have a big effect on game if you reduce some or increase some. lliek for example in CS:GO you can actually see the enemy better if you reduce some settings to low. so pros would have these gaming machines and they would set resolution and almost everything to low.
7. you can also try a lighter more 2D oriented desktop (such as Lubutnu. Xubuntu) to conserve your small resources and use them for gaming instead. for example i have a netbook with Kubuntu but the desktop is set to that it uses some old openGL and does not look as fancy. but this creates more resources for applications and games.



I know the graphic is not much good but i play heavy games thrrought it even less graphic game and supertuxkart work perfect in my pc in linux mint but in ubuntu i have this problem i dont know why this is occuring in manjaro is also runs without any issue but ubuntu :confused: when i play games on ubuntu it worked fine but now there is a issue even i switch to many other ubuntu distro but not benefit only linux mint works, and now i switched to it,hope i came back when issue fixed but i think it cant possible for me,and last thing i want to tell you my pc run heavy enough games even i tried low resources game thanks for reply i wait for that day when the ubuntu community helps people to solve there bugs easily,if that day not come more of its user switch to other distro by the way i love linux very much and encourage all my friends and members to switch to linux but now you see what my own problem is a big problem,thanks for giving time hope all community will help people friendy to ensure the continuation of this great linux.

[https://www.youtube.com/watch?v=WpRi6nCuTcA&ab_channel=TheLinuxExperiment](https://www.youtube.com/watch?v=WpRi6nCuTcA&ab_channel=TheLinuxExperiment)

[https://www.youtube.com/watch?v=TNxoLcP4gNk&ab_channel=DistroTube](https://www.youtube.com/watch?v=TNxoLcP4gNk&ab_channel=DistroTube)

[https://www.youtube.com/watch?v=L7uL50zVZJA&ab_channel=ChrisTitusTech](https://www.youtube.com/watch?v=L7uL50zVZJA&ab_channel=ChrisTitusTech)

---

### Post by veerverma007 on 2021-05-27
Why linux has so much bugs,thats why window is on top
[https://www.youtube.com/watch?v=WpRi6nCuTcA](https://www.youtube.com/watch?v=WpRi6nCuTcA)

[https://www.youtube.com/watch?v=L7uL50zVZJA&ab_channel=TheLinuxExperimentTheLinuxExperimentVerified](https://www.youtube.com/watch?v=L7uL50zVZJA&ab_channel=TheLinuxExperimentTheLinuxExperimentVerified)

[https://www.youtube.com/watch?v=TNxoLcP4gNk&ab_channel=DistroTubeDistroTubeVerified](https://www.youtube.com/watch?v=TNxoLcP4gNk&ab_channel=DistroTubeDistroTubeVerified)

---

### Post by Shibblet on 2021-05-27
```
Graphics:
  Device-1: Intel Atom Processor Z36xxx/Z37xxx Series Graphics & Display 
  vendor: Lenovo driver: i915 v: kernel bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.9 driver: i915 resolution: 1366x768~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics (BYT) v: 4.2 Mesa 20.2.6 
  direct render: Yes 
```

I can't imagine an Intel Atom Processor is going to produce good graphics at all.  Also, you screen resolution is lower (1366x768) - a quasi-720p.

Have you considered streaming game services such as Stadia, or possibly Nvidia GeforceNow?

---

### Post by mikewhatever on 2021-05-27
> **veerverma007 said:**
> I know the graphic is not much good but i play heavy games thrrought it even less graphic game and supertuxkart work perfect in my pc in linux mint but in ubuntu i have this problem i dont know why this is occuring in manjaro is also runs without any issue but ubuntu :confused: when i play games on ubuntu it worked fine but now there is a issue even i switch to many other ubuntu distro but not benefit only linux mint works, and now i switched to it,hope i came back when issue fixed but i think it cant possible for me,and last thing i want to tell you my pc run heavy enough games even i tried low resources game thanks for reply i wait for that day when the ubuntu community helps people to solve there bugs easily,if that day not come more of its user switch to other distro by the way i love linux very much and encourage all my friends and members to switch to linux but now you see what my own problem is a big problem,thanks for giving time hope all community will help people friendy to ensure the continuation of this great linux.

[https://www.youtube.com/watch?v=WpRi6nCuTcA&ab_channel=TheLinuxExperiment](https://www.youtube.com/watch?v=WpRi6nCuTcA&ab_channel=TheLinuxExperiment)

[https://www.youtube.com/watch?v=TNxoLcP4gNk&ab_channel=DistroTube](https://www.youtube.com/watch?v=TNxoLcP4gNk&ab_channel=DistroTube)

[https://www.youtube.com/watch?v=L7uL50zVZJA&ab_channel=ChrisTitusTech](https://www.youtube.com/watch?v=L7uL50zVZJA&ab_channel=ChrisTitusTech)

Ubuntu hater alert!
Troll controll mode activated.
:lolflag:

---

