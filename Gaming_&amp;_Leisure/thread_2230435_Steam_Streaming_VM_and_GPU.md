---
title: "Steam Streaming VM and GPU"
date: 2014-06-19
forum: Gaming &amp; Leisure
---

### Post by AmbiguousOutlier on 2014-06-19
Hello, 

I have a Xeon E3-1230v2 with 16GB of ECC ram, this is located in a spare room connected via a gigabit switch. I would like to use my lightweight noiseless client connected to my tv to do some steam streaming from the server. I currently use it for streaming movies at 1080 with 5.1 sound. 

I think however I need a graphics card, as my server is headless I don't have a monitor connected to it and it's using a VM with a virtual GPU. 

Should I buy a GPU, is there a particular one I should buy or will any do? Is it possible to allocate the entire GPU to one of the VMs?

---

### Post by oldrocker99 on 2014-06-19
I simply don't know whether you should buy a GPU; but if you're in the market, the GeForce 750ti (~$140) is twice as fast as my 650ti, and uses half the power, for what it's worth.

---

### Post by Ranko Kohime on 2014-06-19
Keep in mind that while it worked earlier in the Beta, (that is, streaming a game from a Linux host), that is currently disabled, and Steam streaming only allows Windows hosts, at present.  (You didn't say whether your server is running Linux or Windows)

---

### Post by AmbiguousOutlier on 2014-06-20
My Server is running Debian. You're right in home steam streaming is completely disabled. I installed virt-manager to access an ubuntu VM running steam on the debian host, but I get about 10fps. Also tried No Machine NX with similar results. 

I'm thinking my only options are;

1) Buy Win8 and install on a VM to enable steam streaming
2) Buy a graphics card that can be used for hardware acceleration in a VM to hopefully get more than 10fps

Any other solutions I should try investigating first?

---

### Post by Ranko Kohime on 2014-06-20
Well, the graphics card is pretty much mandatory for most games.  As for Windows, how are you streaming now?  It MIGHT work, if your streaming setup is capable of the low latency necessary.

---

### Post by AmbiguousOutlier on 2014-06-23
I'm currently not streaming, I can use the client on the lowest settings to run games in steam. However I can't get steam to load a game in the Linux VM host, so I will buy the cheapest graphics card for the host machine and see if I can virtualise it. If that fails I'll buy a copy of a Win8 and create a VM to Steam Stream.

---

