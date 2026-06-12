---
title: "Cpu spike in Ubuntu"
date: 2006-10-03
forum: Desktop Environments
---

### Post by nemonullus on 2006-10-03
Hi all,

I have a general problem and this seemed to be the best place to ask about it. (I did search for similar posts, but no luck. I apologize if I missed something obvious.)

I have Ubuntu (Dapper Drake) on a dual boot with Windows XP. Everything is great - I love Ubuntu - but I have one very annoying issue.

My cpu fluctuates very very wildly and weirdly I get spikes where it ramps up to 100%. I started watching with a monitor, and although the "normal" usage is low - 0-10%, the cpu frequently cycles up and shoots to 100%. When this happens, I get screen flashes (white lines running horizontally on the screen). I have tried to track when it happens but there is no very obvious pattern: usually I have open, say, a terminal, Thunderbird and Firefox. I am certainly not doing anything that Windows or OS X would find "heavy" and I thought Linux was especially good at multi-tasking.

Also, for what it is worth I have a pretty new, relatively healthy chip (HP Pavilion a1510n - the chip is an AMD 64, 2.4 ghz).

If anyone has any suggestions for how to track or solve this issue, I would really appreciate it.

Thanks, Nemo

---

### Post by doobit on 2006-10-03
Open a terminal and type ```
top
``` to see the way your system resources are being used. You can leave that teminal open and monitor it in real time as you do other things. There is no problem with getting 100% CPU usage once in a while. It's actually a good sign that the CPU is getting used to it's full advantage. However, the screen flashes don't sound like a good sign. Do you have your computer plugged unto a UPS or line filter? What video card are you using, and does it share RAM or have it's own?

---

### Post by nemonullus on 2006-10-03
Thanks for the quick reply. I will try the tip on the terminal as soon as I can and report back on the results. The spikes are unfortunately more than once in a while - it's as often as once or twice every ten minutes. The computer has an Nvidia Ge Force 6150 LE video chip with (I think) 256 mb of video memory for itself. 

Again, what seems weird to me is that (so far as I can tell) I am not doing anything very fancy and the machine is relatively powerful, so I am surprised.

---

### Post by nemonullus on 2006-10-07
> **doobit said:**
> What video card are you using, and does it share RAM or have it's own?

Hi again. I have made some changes that seem to help (I am now using the k7 kernel and a much lighter windows theme), but I still get flashes sometimes. 

The video card is an NVIDIA GeForce 6150 LE. It has 256 mb of ram, but it is described as "integrated", so perhaps it does share ram with the os more generally. (I admit, I don't quite know how this works.) Edit: I am pretty sure that it shares memory. HP says it has something called "TurboCache supporting up to 256MB shared video memory." Hmm.

Anyone else have any tips? (Top mostly revealed that Firefox is a memory hog, so I am also using Opera now - which is fast and lighter, but not the world's best browser. I miss my plugins.)

---

