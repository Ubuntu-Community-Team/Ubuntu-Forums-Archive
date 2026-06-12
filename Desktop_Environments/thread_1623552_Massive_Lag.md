---
title: "Massive Lag"
date: 2010-11-16
forum: Desktop Environments
---

### Post by Nix82 on 2010-11-16
I have Ubuntu 10.10 installed at work on my Dell Optiplex 755, which runs perfect.

So I decided to install Ubuntu on my home desktop, which so far has been a mistake. Booting up takes almost 5 minutes, after I login it takes about 2 minutes to get to my desktop, typing in any application (even a shell) is horribly lagged, almost to the point where the PC is unusable. I also get extreme lag when executing programs, or just simply clicking a submit button. It will take 2-10 seconds to actually click or execute. The weird part is visual effects extra works perfect and smooth.

CPU: i7 920
Ram 6Gb's
HD1: Veloci Raptor 300Gb 10k RPM
HD2: WD 1.5Tb (Storage)
Video: MSI N250GTS 1Gb


SmartD shows my Raptor healthy, here are the read test speeds. 
Min Read Rate 7.6Mb/s
Max Read Rate 128.2 Mb/s
Avg Read Rate: 105.5 Mb/s
Avg Access Time: 8.6ms
Note: The graph has quite a few drop downs (as you can see the minimum is very low). I've also ran badblocks on the drive which came back with 0 errors. Do I need a special driver for my hard drive?

With those specs, I should not be experiencing any lag. Any help on this would be greatly appreciated...



** UPDATE **: I'm attempting to watch a movie on hulu.com and it works fine as long as I continually move my mouse, when I stop moving the mouse the video gets jumpy.

---

### Post by soldier1st on 2010-11-16
are you running the closed video drivers or the free ones?

---

### Post by Nix82 on 2010-11-16
I installed the ones with the "Driver Finder", the name was Restricted Nvidia driver or something of that nature.

---

### Post by krismatth3 on 2010-11-16
Does your motherboard use the x58 chipset? Seems to be some problem with 10.10's kernel and the x58 chipset. Some people have reported success with a pre-release kernel update (System->Administration->Update Manager, click "Settings" at bottom left, on "Updates" tab check "Pre-released updates" to give it a try.)

---

### Post by Nix82 on 2010-11-17
> **krismatth3 said:**
> Does your motherboard use the x58 chipset? Seems to be some problem with 10.10's kernel and the x58 chipset. Some people have reported success with a pre-release kernel update (System->Administration->Update Manager, click "Settings" at bottom left, on "Updates" tab check "Pre-released updates" to give it a try.)


Yes I am running X58, thank you very much that worked perfectly. I can boot into Ubuntu in less than 30 seconds now and its blazing fast.

---

