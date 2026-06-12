---
title: "PS3 OtherOS Help~ Oblivion Question"
date: 2010-06-26
forum: Gaming &amp; Leisure
---

### Post by Taliathion on 2010-06-26
I am interested in the Capabilities of the PS3's OtherOS feature.
I have an early version firmware that still allows me to use OtherOS, and am already an avid user of Ubuntu, so I don't think I'll have a problem with the actual installation, but I have a question about it's capabilities. I know the Synergistic Processing Elements (SPE's) Can be accessed by OtherOS, but because of HyperVisor RDX can't be accessed.
The root of my question is two parts;

1. [I]Does Ubuntu have access to the full capabilities of the PS3's hardware, eg. can it use the SPE's and Graphics Capabilities, or does it only access its Single 3.2Ghz PPE when it is running applications?
[/I]
2. I have advanced knowledge of the usage of WINE and already have instructions to install Oblivion using WINE, as well as a PC copy of the game. What I want to know, and this is completely dependent on Question One, *Would I be able to Install and Run The Elder Scrolls IV: Oblivion using Ubuntu on OtherOS?*

   Many Thanks,
     Taliathion

---

### Post by oedipuss on 2010-06-26
2. I'm afraid not . WINE needs a x86 cpu, and can't run in ps3's cell cpu. 

I don't know about question 1 though.

---

### Post by Taliathion on 2010-06-26
Thanks, and here's a continuation.
OK, so yes, WINE only works on X86 Arch's, but there are ways of configuring WINE to work on some non-X86 systems. Lets say even one of these work on PS3 and I manage to get WINE running on PS3. (Tangent, and this may sound stupid, but how would you define PS3's Architecture?) Would the modified WINE setup have an effect on my ability to run the Oblivion Installer? Of course, this is all a moot point if Ubuntu can't use the SPE's, but I would like to cover all possibilities. 
Thanks again and in advance for any more help you provide.

---

### Post by tgm4883 on 2010-06-26
That seems to be a lot of work considering the game is available on PS3  

[http://www.amazon.com/Elder-Scrolls-IV-Oblivion-Playstation-3/dp/B000TVT7U4/ref=sr_1_1?ie=UTF8&s=videogames&qid=1277597721&sr=8-1](http://www.amazon.com/Elder-Scrolls-IV-Oblivion-Playstation-3/dp/B000TVT7U4/ref=sr_1_1?ie=UTF8&s=videogames&qid=1277597721&sr=8-1)

---

### Post by oedipuss on 2010-06-27
[This Wikipedia article]("http://en.wikipedia.org/wiki/OtherOS") says access to the GPU from otherOS is restricted. Possibly for exactly that reason, though I wouldn't know :P 
Maybe there could be ways to circumvent that, but even so, I imagine there wouldn't be any high performance drivers ready. 
Short story: No
Long story : Possibly no :P

---

### Post by ucal on 2010-06-27
> **tgm4883 said:**
> That seems to be a lot of work considering the game is available on PS3  

[http://www.amazon.com/Elder-Scrolls-IV-Oblivion-Playstation-3/dp/B000TVT7U4/ref=sr_1_1?ie=UTF8&s=videogames&qid=1277597721&sr=8-1](http://www.amazon.com/Elder-Scrolls-IV-Oblivion-Playstation-3/dp/B000TVT7U4/ref=sr_1_1?ie=UTF8&s=videogames&qid=1277597721&sr=8-1)

PC version gets access to mods, which add hundreds of hours of gameplay.  The two aren't comparable at all, sadly.  Given how successful Little Big Planet was with it's online user generated content distribution, I'm hoping Bethesda will follow suit for console users on TES V.

---

### Post by rabbotz on 2010-06-27
> **Taliathion said:**
> I am interested in the Capabilities of the PS3's OtherOS feature.
I have an early version firmware that still allows me to use OtherOS, and am already an avid user of Ubuntu, so I don't think I'll have a problem with the actual installation, but I have a question about it's capabilities. I know the Synergistic Processing Elements (SPE's) Can be accessed by OtherOS, but because of HyperVisor RDX can't be accessed.
The root of my question is two parts;

1. [I]Does Ubuntu have access to the full capabilities of the PS3's hardware, eg. can it use the SPE's and Graphics Capabilities, or does it only access its Single 3.2Ghz PPE when it is running applications?
[/I]
2. I have advanced knowledge of the usage of WINE and already have instructions to install Oblivion using WINE, as well as a PC copy of the game. What I want to know, and this is completely dependent on Question One, *Would I be able to Install and Run The Elder Scrolls IV: Oblivion using Ubuntu on OtherOS?*

   Many Thanks,
     Taliathion

i doubt it. im pretty certain nvidia havent released a driver for such a niche 'market', and the open drivers for nvidia are bleh at best.

---

### Post by kiddykoff on 2010-06-28
i believe there was a trick to open up the hypervisor so that restricted areas could be used as swap space. I'm fuzzy on the details ever since upgrading my firmware.

check out [http://psubuntu.com/](http://psubuntu.com/) for more info

---

### Post by Taliathion on 2010-06-29
Not gonna lie, I'm thankful for the replies, even if they seem to point to a negative result.
Well, I know of course Oblivion is on the PS3, I play it often, but as was pointed out, I would love access to the mods. I appreciate the help and am glad to be part of the Ubuntu community.
Also, if anyone gets any news on this matter, I would LOVE to get an update about it, you can reach me either through the Ubuntu Forums (Of Course XP,) or through Gmail, which I check much more often. 
[EMAIL="Yoshi1029384756@gmail.com"]Yoshi1029384756@gmail.com[/EMAIL]
or, AIM
Yoshi1029384756

Oh, and Also, I know about GeoHots HyperVisor Bypass, but I don't think it would be very relevant. Thanks though.

---

### Post by Taliathion on 2010-07-01
/Hopeful-and-looking-for-more-info-Bump

---

### Post by Taliathion on 2010-07-05
/Oh-Cmon!-Bump

---

### Post by benmoran on 2010-07-05
Weren't all your questions answered already? If not, what do you still need to know?

---

### Post by Taliathion on 2010-07-05
I'm sorry if I wasn't clear enough, but I never got a definitive answer to my second question with one stipulation.

Assuming that I can get wine to function on my PS3, and I manage to install Oblivion, would the PS3 be able to utilize the SSE's to run the game, and would the PS3's graphical engine be able to contribute to it?

---

