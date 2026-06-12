---
title: "Building a Ubuntu gaming system"
date: 2006-10-28
forum: Gaming &amp; Leisure
---

### Post by draky87120 on 2006-10-28
So I'm looking at building a non-Windows gaming system because I am tired of giving all my hard earned cash to such a greedy company.

I'm looking for suggestions for hardware to play games at a minimum 1280x1020 resolution. I'm looking to go with the new core2 duo and a 965 mobo and of coarse 2 gigs of ram. I'm looking for what vid cards would be the minimum so I can go from there. I was also looking at this Cedega to use with it or is there something else that would work better. 
I mainly play World of Warcraft. I'd also like to play the new FEAR on the system as well and maybe Oblivion and NWN2. 
Thank you in advance for your assistance.

---

### Post by curvedinfinity on 2006-10-29
Firstly, gaming on ubuntu is a bit of a chore compaired to Windows. Generally challenges will come from games that use DirectX exclusively. Some will work at reduced speed with programs such as Wine, but others simply won't work. I don't like Cedega, but others do.

Generally, ID and Epic games (Doom,Quake,Unreal) will work brilliantly running natively on Linux.

I am able to run Doom 3 at the highest settings at 1280x1024 resolution with 16x FSAA at around 45 FPS average. Here are my specs:

Pentium D 805 (OCed to 3.5 GHz)
1 GB DDR2 667
2x 80 GB 7200 RPM HDDs running in RAID 0
GeForce 7600 GT

Back when RAM was cheaper -- its gone up by about 40% in the last month, this system cost around $650 on newegg.

Some extra notes: Only get Nvidia graphics cards -- ATIs run very poorly on Linux (due to their drivers). If you use Wifi, make sure your wireless card is in the supported wireless cards list. You can get most wireless cards working in Linux, but the ones on that list need no setup ... they will just work after you install Ubuntu. The GeForce 7600 GS is the best bang for the buck right now and will definitely play all games on very high settings, but the GT is great for maxing settings. Linux has much better memory management than Windows, so generally 1 GB is all you need for playing the current games.

Also, as you play WOW, I would highly recommend RAID 0, as MMOs especially require accessing the HDD often, and RAID 0 will double your bandwidth. -- Just fyi, though, RAID can be a real pain to setup with the RAID "controllers" on motherboards, as they aren't really raid controllers as in the dedicated ones that you get for a PCI slot. There is a ton of discussion on this -- its called "Fake RAID". I run fake RAID, but I had a lot of trouble setting it up my first time.

---

### Post by draky87120 on 2006-10-29
Thank you very much for the reply and info. I have been into computer hardware in a major way for a long time (since the celeron 300A) and am very familiar with hardware. I just wasn't sure about how the hardware works on Ubuntu (or Linux for that matter as I am a complete newb outside of Windows and Mac). The RAID I've used ever since mobo's started to put them for good prices. Just seems like a no brainer to me. I was actually looking at the 7600GT as well as I have to completely agree that for the price I can't see anything else beating it.
For the memory, I am very glad to hear how Ubuntu handles memory better then windows. I have had 2 gigs of ram in my win system for quite some time now and was not looking forward to spending the money on 2gigs of DDR2 because all I have is regular DDR ram.
Thank you very much for the info!

---

### Post by WinterWeaver on 2006-10-29
Just thought that I'd give my wee bit of info on Cedega :P

I use it, mainly because I play Guild Wars. This is one game that does not aggree with wine, and even has hassles with Cedega. But I must admit that I was impressed with Cedega.

After a weekend of tweaking, reading forums etc, I actually had my Guild Wars running at Higher Graphics, and Faster, than what it ran on my now-removed XP box.

I do however still have one biggie problem with GW, which is garbled up text (something very important). But as far as I understand, this is a problem with the latest NVIDIA drivers, and since I use TwinView, I'm not interested in rolling back them drivers :P ... guess I'll just wait for the new drivers, and hope it's fixed hehe

All in all.... I think Cedega is quite good. I installed the win version of DoomIII the other day (just to test), and it ran perfectly. I know you get a native client for Doom, but it was just to test, I don't like the game neway ^.^

kk, hope you have fun =D

---

### Post by curvedinfinity on 2006-10-30
About Guild Wars, I've played it a tad using my Ubuntu rig using Wine. Just a few Random Arena matches, but it seemed to be running fine after patching wine with a couple things that someone specified in a post here. -- Just very limited shader support using Wine, but it ran alright otherwise.

---

