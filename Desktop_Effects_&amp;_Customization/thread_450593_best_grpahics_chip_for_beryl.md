---
title: "best grpahics chip for beryl"
date: 2007-05-21
forum: Desktop Effects &amp; Customization
---

### Post by purpledavec on 2007-05-21
Hi, I'm soon to be buying a new laptop (when someone buys my desktop!) I am interested in peoples opinions of which of the these mobile graphics chips would run Beryl/XGL/Compiz etc the best my budget is tight so the three most obvious chips on offer are:
ATI Radeon xpress 200m upto128mb?
Intel GMA 950 upto i think 224mb?
Nvidia 6100/6150 (is the difference massive betwen them) at about 256mb?

I'm not worried about compiling drivers etc so that isnt of concern, it is merely the performance of the effects that I am worried about. My current laptop (Fujitsu Siemens 2055!) has a Via Unichrome P4M800/CE chip which won't run Beryl etc wasn't the easiest to get going with 3D!

What do you think? Which one do you think is the best bet? does the memory really count? if so is the GMA 950 the best. Or is the Nvidia and Ati name worth a shot? How do they compare is what i'd really like to know?
Thanks for any help/comments.

DC

---

### Post by Ateo on 2007-05-21
without a doubt, NVIDIA. Don't say I didn't tell you so. =)

NVIDIA doesn't *need* AIGLX nor XGL. So, it's the best bet and works excellent.

---

### Post by Kobalt on 2007-05-21
Intel graphic card works fine as well.

---

### Post by John.Michael.Kane on 2007-05-21
Not sure about the ati card. Some folks have had issues with their drivers. This is not to say it's not possible to run beryl on the card in question,however. it may take a little more effort.

Looking over the Intel GMA 950 specs it should run beryl with out issue


As for the Nvidia 6100/6150 I'm currently using the 6100 series, and have tested beryl on it with out issue. 

As for the difference between the 6100 6150 their clocked differently.6100 is clocked at 425mhz while the 6150 is clocked 475mhz, and has DVI, and video-out.

---

### Post by fsckedagain on 2007-05-22
Well, I have an Intel 950 and can say beryl simply kicks *** with no effort other than 915resolution and some adesktop shenanigans to get my desklets working right.

Dell XPS M140 -- Ubuntu 7.04 (FF)

woot, go me...

---

### Post by purpledavec on 2007-05-22
thanks for the replies, would it be fair to say that the performance difference  between the nvidia and intel chips is minimal then? Reason i ask is because i can find the intel's cheaper than the nvidia.

thanks again

---

### Post by eentonig on 2007-05-22
I don't know the exact speed differences between Intel and Nvidea. But three plusses I see in favor off Intel:

- Recognized out of the box
- Driver support. You don't need closed source drivers to get everything out of your card.
- Price

---

### Post by purpledavec on 2007-05-29
Hello, thanks again for replying. I was browsing a Currys website on their clearance laptop section and came across a COMPAQ F502EU, its got good specs and an NVIDIA 6150 graphics card wooo wooo it was the best specified one I could find that had a decent enuf chip. plus I am quite sure in future I can upgrade the CPU to a Turion. Only thing is I think its wireless card is a BCM4311 (gulp) which appears to be tricky to setup etc. Anyone recommend a Ubuntu based distro that will work 'out of box' as such?

thanks again

---

### Post by digimatic on 2007-06-10
> **purpledavec said:**
>  Only thing is I think its wireless card is a BCM4311 (gulp) which appears to be tricky to setup etc. Anyone recommend a Ubuntu based distro that will work 'out of box' as such?


I have the BCM4318 wireless chipset on one of my machines and it was a doddle to set up with feisty, all I had to do was sudo apt-get install bcm43xx-fwcutter which automatically downloads and extracts the missing firmware image you need.

AFAIK the BCM4311 should be no different.

---

### Post by purpledavec on 2007-06-10
thanks, just finished getting it all working with ndiswrapper doh. thanks for the reply tho :-)

---

### Post by patrickfromspain on 2007-06-10
between NVIDIA 6100 and Intel GMA 950, I'd go with Intel: they will have more or less the same performance and the Intel drivers will give you no trouble at all. Also, battery will last longer using the intel card, I believe. If you could... an nvidia 7300, 7400 or (even better) 8300,8400 would be better options than the intel 950 (or the newer 965).

Anyway, I'd wait a little to get a new laptop: intel has upgraded the centrino platform, so there are better procs (with 4mb L2 cache and 800MHz FSB), new graphic card (intel 965) and new wifi card (intel 4965). So I'd wait until they get a little cheaper and get one of these.

---

### Post by Toontwnca on 2007-06-10
I have ATI Radeon xPress 1100 graphics on my Acer laptop.
It was a breeze to set up with the restricted drivers setup.

Beryl runs just fine with xgl.

---

### Post by FA22RaptorF22 on 2007-06-10
For now just use nvidia, as it is fully supported natively and works without a doubt ATI is currently very slow at initiating AIGLX support, and XGL slows down the computer too much to make good use of on a laptop.  The Intel chips are not my favorite, but they are not too shabby either.

1st choice: nvidia
2nd: ati
3rd: intel

---

### Post by patrickfromspain on 2007-06-11
don't go with ati!!!

The drivers are a pain, you will need to set up XGL and so on... I'd never get an ATI card for linux..

---

### Post by Lem on 2007-06-11
I have two pcs.. one with nvidia 6150. The shared memory issue blights this card and beryl/desktop effects don't run that well. My old intel 915 based laptop runs beryl/compiz/desktops effects like a breeze and I didn't have to configure anything.

Considering I'd bought the 6150 specifically for Ubuntu and only put it on my laptop when the hdd with the default windows install died, I'd plump for the Intel for an integrated solution.

---

### Post by styven on 2007-06-12
Hold the front page, just did sudo apt-get install bcm43xx-fwcutter, and the blue light for my wireless card came on for the first time, can't find a wireless network to try yet, but my god the excitement:p

I only came to this thread researching a beryl issue.

Steve.

---

