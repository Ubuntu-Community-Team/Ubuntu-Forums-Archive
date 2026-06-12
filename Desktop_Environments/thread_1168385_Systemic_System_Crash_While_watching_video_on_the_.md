---
title: "Systemic System Crash While watching video on the web"
date: 2009-05-24
forum: Desktop Environments
---

### Post by sullenx on 2009-05-24
Okay I'm pissed.

I have been experiencing consistent TOTAL system crash since Ubuntu Hardy all the way now to Ubuntu Intrepid. When I say total, i mean total, everything goes, Xorg Freezes, no network, and a sound high pitch noise!

First let me give you my machine specs: 

My processor is a: 
```

model name      : Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz

```
Sound card:
```

*-multimedia                                                                                                                                
                description: Multimedia audio controller                                                                                               
                product: SB0400 Audigy2 Value                                                                                                          
                vendor: Creative Labs                                                                                                                  
                physical id: 2                                                                                                                         
                bus info: pci@0000:05:02.0                                                                                                             
                version: 00                                                                                                                            
                width: 32 bits                                                                                                                         
                clock: 33MHz                                                                                                                           
                capabilities: bus_master cap_list                                                                                                      
                configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2 module=snd_emu10k1 

```
Video Card
```

*-display                                                                                                                                   
                description: VGA compatible controller                                                                                                 
                product: G94 [GeForce 9600 GT]                                                                                                         
                vendor: nVidia Corporation                                                                                                             
                physical id: 0                                                                                                                         
                bus info: pci@0000:01:00.0                                                                                                             
                version: a1                                                                                                                            
                width: 64 bits                                                                                                                         
                clock: 33MHz                                                                                                                           
                capabilities: bus_master cap_list                                                                                                      
                configuration: driver=nvidia latency=0 module=nvidia 

```

I am running Kubuntu Jaunty 9.04. Kernel 2.6.28.9, I compiled it myself to enable 64 GB memory.

The total freeze happens when i'm watching a video either in youtube, hulu,etc,etc. It happens RANDOMLY and without warning. One day it will happen once or twice, another day it won't happen at all. Of course this is very annoying.  I have to physically reset the machine to reboot. 

I have installed the lastest nvidia driver from their site and it did nothing.  I suspect it has to be something with the adobe player, but to test that theory i tried playing the video on a virtual machine and it still crashed.  I tried looking for Xorg or kern logs, but NOTHING, it just goes.

Can someone please help me!

---

### Post by ckonestroh on 2009-05-24
I had to punch around the internet.....


Get a picture in my brain of this system....

This is not a laptop is it or are you running a multi monitor set up....


What I'm thinking is your having a heating problem that is leading to it failing every time you run movies causing your graphics card to over heat....


Or even system memory to crash....

The only possible tech thing I can come up with is dust siting in the case causing a overheating.....


Common problem will be heating your system have you ran Nvidia monitor your heat of your gpu.....


good luck...

---

### Post by sullenx on 2009-05-24
I'll give that a try, i'm not too good keeping things clean.
That was my first clue, but according nvidia setting temp, the card is running at 58-60*C, i see the limit is 100 or so. 60*C seems too high? i know the core temp should be around 50*C.

I also have a dual display.

---

### Post by Zorael on 2009-05-24
I imagine you're running the proprietary driver? Try the non-accelerated nv one. I'm not saying you should keep using it in perpetuity, just to see if it's the Nvidia blob driver that's causing it.

That said, there's a [whole slew](http://icanhascheezburger.files.wordpress.com/2008/05/funny-pictures-pony-mechanic.jpg) of stuff that could be at fault. Flash just being a 8¡+ch, busted RAM/VRAM, something overheating, something just plain broken, etc.

---

