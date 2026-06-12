---
title: "Best new graphics card for me?"
date: 2009-09-24
forum: Gaming &amp; Leisure
---

### Post by bluejeansummer on 2009-09-24
I bought a used computer from a friend of mine several months ago. It's been running just fine, but the graphics are a bit slow, and I'd like to replace the video card. The computer is a Dell Precision 650, and the current card is an Nvidia FX 5200.

According to [the online specs]("http://support.dell.com/support/edocs/systems/ws450/en/ug/info.htm#1118040") posted by Dell, my computer has the following available slots:
[LIST]
[*]3 PCI-X 1.0 slots (3.3V)
[*]2 PCI 2.2 slots (one is 3.3V, other is 5.0V)
[*]1 AGP 8x Pro 3.0 slot (1.5V)
[/LIST]
Most of the cards I'm seeing on [Newegg]("http://www.newegg.com/") use PCI Express, something that my computer doesn't have. I don't have enough money to get a whole new computer, so I'd like to know what you guys think is the best Linux-compatible graphics card I can get that will work in my computer. I'd prefer Nvidia, as I've heard that they have better Linux drivers than ATI. As for price, I'd like to keep it less than $150, but I'll pay a bit more if I have to.

 -- Nick

---

### Post by gordintoronto on 2009-09-24
A new motherboard and CPU would be a better way to spend money.

---

### Post by NewlyHuman on 2009-09-24
> **gordintoronto said:**
> A new motherboard and CPU would be a better way to spend money.

He said he can't afford a new system. Replacing the motherboard and CPU entails a new video card and RAM, because you're not going to find a worthwhile LGA775 motherboard that can use DDR with an AGP slot.

However, it's the best option in the long run. AGP is dead, DDR is dead, and Socket 604 is also dead.

As for a graphics card upgrade... I'm not sure. You can swing an AGP 7300GT for  about $75, but that's absurdly expensive for the performance.

Could also buy a 6200 for around $30-40, which is substantially more powerful than an FX 5200 - But it's still obsolete.

You could also get an ATI HD 3850 for around $90-100, which is a fairly modern card - But it's overkill compared to your CPU, and I've had mediocre experiences with ATI drivers.

---

### Post by bluejeansummer on 2009-09-24
[QUOTE="NewlyHuman"]Could also buy a 6200 for around $30-40, which is substantially more powerful than an FX 5200 - But it's still obsolete.[/QUOTE]
I found a 6200 on eBay for ~$40, so I think I'll buy that as an upgrade until I have enough money saved up to build a new, modern computer. Thanks for the advice.

-- Nick

---

### Post by Mike'sHardLinux on 2009-09-24
Be careful you do not end up with a 6200 LE or TC. You might get same or worse performance as your 5200.

---

### Post by bluejeansummer on 2009-09-24
[This]("http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=380159968797&ssPageName=STRK:MEWAX:IT") is the one I was planning on getting. Any objections?

---

### Post by NewlyHuman on 2009-09-24
> **bluejeansummer said:**
> [This]("http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=380159968797&ssPageName=STRK:MEWAX:IT") is the one I was planning on getting. Any objections?

Seconding what Mike'sHardLinux said. 6200 LE/TC models are mostly discontinued, replaced simply by '6200'.

The TC is rather odd - It uses up to 256MB of memory, but only 64MB of that is on the graphics card - The rest is borrowed from your RAM.

The vanilla 6200 has 256MB of onboard memory and, as a newer part, likely performs better.

---

### Post by sloggerkhan on 2009-09-24
The most modern/economical card you can get agp is probably a radeon 4650. Costs maybe $80 for agp version.

On linux it will probably be a great card outside of accelerating hi-def video decode.

If you properly do the ati driver. (Which will build ubuntu *.deb packages for you.)

---

### Post by tuxxy on 2009-09-24
Stay clear of ATI cards the drivers are a nightmare

---

### Post by sloggerkhan on 2009-09-25
> **tuxxy said:**
> Stay clear of ATI cards the drivers are a nightmare

Depends on the card you have and how clueless you are.
Nvidia are somewhat better driver wise, excluding the fact that you have to reinstall them with every kernel update. However, ATI's cards are not as bad as they're made out to be by nearly everyone.

However the card you've chosen is fine, at least in term of being substantially better than what you have now.

---

### Post by gordintoronto on 2009-09-25
> **sloggerkhan said:**
> 
Nvidia are somewhat better driver wise, excluding the fact that you have to reinstall them with every kernel update.


Huh?  I've done several kernel updates and never reinstalled my nVidia drivers.

My bet is the OP will not notice any performance improvement unless he plays games in Windows.  And I could be wrong!

---

### Post by doorknob60 on 2009-09-26
> **tuxxy said:**
> Stay clear of ATI cards the drivers are a nightmare

Not always. I'm running happy with my integrated Radeon 3100 with Catalyst 9.9 drivers right now (loaning my 8400GS to my brother). Everything is working great. [http://doorknob60.is-a-geek.org/wordpress/?p=6](http://doorknob60.is-a-geek.org/wordpress/?p=6)

---

### Post by sloggerkhan on 2009-09-26
> **gordintoronto said:**
> Huh?  I've done several kernel updates and never reinstalled my nVidia drivers.

My bet is the OP will not notice any performance improvement unless he plays games in Windows.  And I could be wrong!

You probably use distro-packaged drivers.

If you actually want the latest drivers (I have nvidia 190.x series), you will have to reinstall them with every kernel update. It's highly worth using the latest drivers IMO, at least if you have a graphics card that's 8000 series or better, because of ongoing improvements and bug fixes to vdpau and opengl 3.0 support, not to mention normal bug fixes/improvements.

With ATI, they are set up so that even if you use the latest drivers (I think they update about once a month, maybe every 2 months) dkms allows for kernel updates without reinstallation/recompilation of the kernel module/interface.

---

### Post by coldReactive on 2009-09-26
nVidia GTS 250 1 GB works wonders on my system on Linux. But unfortunately, it's PCI Express. I would save up for a new motherboard and processor and power supply to be honest.

---

### Post by DivineTemplar on 2009-09-28
I can say from experience that the ATI drivers are not as bad as everyone claims. They may have been at one point, but they work just fine for me now. 

Honestly from looking at your specs, you should just overhaul pretty much the whole thing. You are going to struggle to find a useful card that will work with your older motherboard. PCI Express (x16) is pretty much the standard now. 

I wish I had better news for you. :(

---

### Post by Perfect Storm on 2009-09-28
+1 @ Nvidia card.

Though ATI is getting better, but their driver isn't up to pair with the Nvidia driver yet. In a couple of years hopefully.

---

### Post by handy on 2009-09-28
I own both ATi & nVidia GPU driven machines.  I would always advise nVidia, was the way to go until recently.

The ATi open-source drivers have been getting a huge amount of work & are moving fast, there are changes starting to be incorporated into the Linux kernel starting with the newly released .31 version, that will make supporting the ATi GPU's easier & more effective.

It won't be all that long & the ATi GPU's will be the FOSS darling.  Which will certainly be a turnaround because they have been hell for most of this year.

Have a look at this thread for more info' on the topic, there are some worthwhile links at the bottom of the original post too:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

---

### Post by rajeev1204 on 2009-10-27
> **bluejeansummer said:**
> I bought a used computer from a friend of mine several months ago. It's been running just fine, but the graphics are a bit slow, and I'd like to replace the video card. The computer is a Dell Precision 650, and the current card is an Nvidia FX 5200.

According to [the online specs]("http://support.dell.com/support/edocs/systems/ws450/en/ug/info.htm#1118040") posted by Dell, my computer has the following available slots:
[LIST]
[*]3 PCI-X 1.0 slots (3.3V)
[*]2 PCI 2.2 slots (one is 3.3V, other is 5.0V)
[*]1 AGP 8x Pro 3.0 slot (1.5V)
[/LIST]
Most of the cards I'm seeing on [Newegg]("http://www.newegg.com/") use PCI Express, something that my computer doesn't have. I don't have enough money to get a whole new computer, so I'd like to know what you guys think is the best Linux-compatible graphics card I can get that will work in my computer. I'd prefer Nvidia, as I've heard that they have better Linux drivers than ATI. As for price, I'd like to keep it less than $150, but I'll pay a bit more if I have to.

 -- Nick

I suggest an ATI Radeon 4650 AGP.It will give you a phenomenal leap in performance, but your cpu will slow this gpu down.But if you could wait a bit till you have more money, i suggest a new amd cpu and motherboard ,because even the onboard radeon 4000 series is faster than that nvidia 6200 discreet card you are going to buy.

Its available online you should search a little.Is around 80 dollars.

Stay away from the 6200, its worthless and wont give you any speed increase really.

ATI drivers are not as bad as being suggested here,they work good now.

Also read this link [http://www.brighthub.com/computing/hardware/articles/48374.aspx](http://www.brighthub.com/computing/hardware/articles/48374.aspx)

and this one [http://www.tomshardware.com/reviews/radeon-4650-agp,2383.html](http://www.tomshardware.com/reviews/radeon-4650-agp,2383.html)

---

