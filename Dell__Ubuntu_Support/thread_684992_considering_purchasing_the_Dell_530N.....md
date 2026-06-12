---
title: "considering purchasing the Dell 530N...."
date: 2008-02-01
forum: Dell  Ubuntu Support
---

### Post by ericmc783 on 2008-02-01
Was wondering what everyone who has tried this machine with Ubuntu has thought.

The specs I want to get: 
250GB hard drive, 4GB DDR-RAM, 256MB Nvidia GeForce 8300-GT.

right now, the price on this is $829, not including tax and shipping. the $829 price is also after Dell's "Instant savings" of $100 dollars.

I realize there are some existing threads about this, but they are rather old, so i figured i'd start a new one.

---

### Post by gbrainin on 2008-02-02
I've been extremely happy with mine for the past 6+ months.  I would, however, save some money and get your extra memory elsewhere.

---

### Post by SpiderGorilla on 2008-02-02
I have more or less the same configuration and paid twice that with 4GB of RAM. It makes me want to punch myself in the crotch because I bought mine about 6-8 months ago and it already half the cost. And I waited for the new ones to come out so this wouldn't happen. Argh? Argh.

---

### Post by ericmc783 on 2008-02-02
> **gbrainin said:**
> I've been extremely happy with mine for the past 6+ months.  I would, however, save some money and get your extra memory elsewhere.

first, glad to hear. 

But as far as a memory upgrade, what options should i consider. (im a n00b who has never upgraded hardware on a pc). Any particular products or websites you would recommend I check when shopping for memory?

---

### Post by gbrainin on 2008-02-02
Sorry, I haven't upgraded the memory in this particular machine, but I know others have.  Doing the upgrade is a matter of snapping the memory sticks into the appropriate slots; the Dell hardware manual (available on their website) explains this in some detail.  As for what to purchase, I don't know but if you search around you'll get plenty of opinions.

---

### Post by Trenchbroom on 2008-02-03
> **ericmc783 said:**
> first, glad to hear. 

But as far as a memory upgrade, what options should i consider. (im a n00b who has never upgraded hardware on a pc). Any particular products or websites you would recommend I check when shopping for memory?

Crucial memory has always worked well for me and their website has a laptop memory finder:  very easy install.

[LINK HERE]("http://www.crucial.com/store/drammemory.aspx")

---

### Post by ericmc783 on 2008-02-03
i looked at Crucial and put in the inspiron 530n. They didnt seem to have a whole lot different than I could get from dell directly, in terms of specs and price. but maybe im wrong.

nonetheless, im glad to hear some of you (in this thread as well as a few others) are generally happy with this PC.

---

### Post by MJN on 2008-02-05
I can second the Crucial recommendation, at least here in the UK the price difference compared with upgrading via Dell is significant.
 
Note thatthe 530N can only address a total of 4GB virtual memory (32-bit limitation of the BIOS/chipset), hence given the graphics card and PCIExpress architecture requires its memory mapping into this you will effectively only 'see' around 3.2GB of your physical RAM.
 
Hence, if the default configuration is 1GB (likely on a matched-pair of 512MB sticks) then I would only recommend adding another 2GB (a matched-pair of 2 x 1GB sticks) as you will be throwing away most of anything higher than this.
 
Mathew

---

### Post by BertP on 2008-02-05
I just received my I530N yesterday and am very pleased.   I only have 1gb but everything I have tried has been lightning fast so far.

Be sure to checkout this page:
[http://direct2dell.com/one2one/archive/2007/12/19/38924.aspx](http://direct2dell.com/one2one/archive/2007/12/19/38924.aspx)

and be sure to watch the video at the bottom of the page.  The computer they demonstrate , I believe, is a 1 gb 530N

---

### Post by valke on 2008-02-05
so i'm assuming it's gnome by default, eh?

---

### Post by BertP on 2008-02-05
>so i'm assuming it's gnome by default, eh?

yes

---

### Post by zesty on 2008-02-07
I purchased my 530N a few months ago.  Crucial was a lot cheaper for memory for me.  I went with the 1GB from Dell and then bought another 2GB to add in.  The process is simple, there's two open RAM slots in the Dell so you can just add the Crucial memory and you're up to 3GB.

I have the 1.8 GHz processor and 128MB video card.  I don't really push the computer but it handles everything with speed and ease, including the desktop effects.  The cost for my box was less than $400 but I didn't get a monitor or any other upgrades.

---

### Post by RedRat on 2008-02-11
I have now had my 530n for about a month. I have 2GB of memory and running gnome. Other than a botch up by me, requiring a clean install of Ubuntu from the disk provided, I have had no problems. The machine works like a charm. I have now found many programs that do what my old Windows programs do and am quite happy with the machine. I have been pleasantly surprised at how the usb ports worked very neatly with my Sony camera to download pictures quickly and with out a problem. It also recognized my SanDisk 2Gb thumb memory. 

While it works pretty well out of the box, you might want to check out this in the Ubuntu forums:
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
if you are interested in more multimedia and streaming audio functions. Do not be afraid of using the Terminal Editor to give the various command line orders. Read it carefully and you will have a pretty complete set of software for doing just about anything.

---

### Post by Trindol on 2008-02-11
> **MJN said:**
> I can second the Crucial recommendation, at least here in the UK the price difference compared with upgrading via Dell is significant.
 
Note thatthe 530N can only address a total of 4GB virtual memory (32-bit limitation of the BIOS/chipset), hence given the graphics card and PCIExpress architecture requires its memory mapping into this you will effectively only 'see' around 3.2GB of your physical RAM.
 
Hence, if the default configuration is 1GB (likely on a matched-pair of 512MB sticks) then I would only recommend adding another 2GB (a matched-pair of 2 x 1GB sticks) as you will be throwing away most of anything higher than this.
 
Mathew

The 530N has a Core 2 Duo which is a 64 bit processor, is there something I'm not understanding?

---

### Post by MJN on 2008-02-12
The CPU is but one link in the chain. The 'bottleneck' (for want of a better phrase) in this case is the BIOS.
 
Mathew

---

### Post by Trindol on 2008-02-12
Hm I see. I have a 530N with 4 gigs of ram and it does indeed show 3.2 in Ubuntu, but 4096MB in the the bios.

So are you saying that .8 gigs of ram will be taken up by other things no matter how much ram you have purchased? (if I had 2 gigs, would ubuntu only see 1.2?) That seems like a lot.

---

### Post by MJN on 2008-02-12
No, only when you've got 4GB installled.
 
If you picture it like this - you've got 4GB worth of 'virtual memory' space and hence all you can address is memory within this 4GB. All components within the system that contain real (physical) memory must be mapped into this 4GB space. Hence if you've only got 2GB real RAM installed then you've got 2GB left in which to map the memory from your graphics cars, PCI Express etc so you'll have no overlap.
 
Mathew

---

### Post by Trindol on 2008-02-12
Ah ok. The idea is starting to make sense now. However what doesn't really make sense is why Dell would bother using a 64 bit processor and then still have this "limitation". I don't suppose it is easily solvable without replacing hardware. I am already running gutsy AMD64, that made no difference.

I guess it is not such a big deal, I can't really imagine needing this much RAM ever...

---

### Post by MJN on 2008-02-12
Cost (vs requirement) mainly.
 
The more cynical reason might be that it also provides diffrentiation across the product range - i.e. the higher level models (XPS, Vostro etc) may well support more.
 
Mathew

---

### Post by BertP on 2008-02-12
> **Trindol said:**
> Ah ok. The idea is starting to make sense now. However what doesn't really make sense is why Dell would bother using a 64 bit processor and then still have this "limitation". I don't suppose it is easily solvable without replacing hardware. I am already running gutsy AMD64, that made no difference.

I guess it is not such a big deal, I can't really imagine needing this much RAM ever...

For more detail on the ram limitation check out this thread
[http://ubuntuforums.org/showthread.php?t=574494](http://ubuntuforums.org/showthread.php?t=574494)

I think I recall some of the posters talking about using the 64 bit version of Ubuntu and recompiling the 32 bit version with the appropriate flags in order to use the whole 4gbs of ram

---

### Post by Trindol on 2008-02-12
Thanks, I have read that thread before. Actually I did attempt to compile my own kernel from kernel.org, the newest stable release, I think it was 2.6.24.1. I didn't see a high memory option in there...maybe I missed it but I'm fairly sure there was no such option when I ran menu config. The kernel loaded up and everything alright but still only recognized 3.2GB. I might try again but with an older kernel as that one did not have any driver support in synaptic and I didn't have th energy to mess with it then.

---

### Post by MJN on 2008-02-12
Let's not get confused here. This is a *hardware* limitation - there is nothing you will be able to do about it even with a 64-bit OS.
 
There is a good summary at the following MS KB article: [http://support.microsoft.com/kb/929605](http://support.microsoft.com/kb/929605)
 
As the article reads we need to satisfy the following to enable a full 4GB of real RAM to be available:
 
- Compatible chipset (This is fine - the 530N uses the Intel G33 chipset which supports upto 8GB RAM)
 
- Compatible CPU (This is fine - all the 530N CPUs are 64-bit)
 
- Compatible BIOS supporting PCI memory remapping (**This is where we fall** - the 530N BIOS does not do this (by design or configuration I don't know but the end effect is the same))
 
- Compatible OS (This is fine - we have 64-bit Ubuntu available, although even the 32-bit can support 4GB)
 
Mathew

---

### Post by Trindol on 2008-02-12
Okay then bear with me for one more question. What factor is limiting me to 4GB of virtual memory if it is not the CPU? You mentioned PCIExpress and the videocard...sorry I'm kind of an idiot with hardware. And software too haha, just a little less so.

Edit: alright, your edit answers my question. I don't think there are any options in the stock bios that would help. But it seems like maybe, if dell wanted, there would still be a way to address this with a new bios...oh well.

---

### Post by MJN on 2008-02-12
Don't hold your breath though.. ;)

---

### Post by paul6 on 2008-02-13
I am about to purchase this PC for a relative and I have a question - suppose I don't upgrade, and stay with 1 GB of RAM - Will he be able to keep multiple Firefox tabs open with music applications playing and no slowdown? The general impression I have gotten is that you only need 2 GB for gaming or video editing, or some other resource intensive activity.

---

### Post by MJN on 2008-02-13
It's kind of difficult to directly correlate RAM and end-user performance. Sure, more generally equals better but as the system takes a finite time to do *anything* you can never completely eliminate slowdown.

But, notwithstanding that, I don't see it being a problem. I am regularly in the scenario you describe on an ancient PIII (with 1GB RAM for what it's worth) and don't have any trouble - indeed there's usually plenty more (server apps mainly) running besides.

At least here in the UK it is far cheaper (half the price pretty much) to buy your extra RAM elsewhere (e.g. Crucial) than via Dell as part of the system-ordering process so I'd say it's a moot point. Unless there are circumstances which don't allow, go with the 'basic' 1GB and then buy an upgrade later (elsewhere) if need be (perhaps they might want to do more than Internet/music in due course).

Mathew

---

### Post by Trindol on 2008-03-26
Update: Hooray, it seems that Dell either realized their mistake or gave in to the consumer on this one. **Bios update 1.0.12 lets me see 3.9 GB of RAM in Ubuntu amd64** (I have 4GB installed).

Previously, the 530N bios limited (as Matthew explained) the system to 3.2 GB RAM, even though it was capable of 4 (at least).

Now the bad part, flashing the bios was a real pain. The 530N is apparently not in Dell's little repo for easy bios updates so the handy "update_firmware" command won't work. I tried using biosdisk to make an image for grub to load, that didn't work. I tried making a bootcd with freedos, that didn't work either. I think it has to do with the fact that dell provides an autoextracting executeable designed for windows to flash the bios, not the actual rom file. But maybe someone who knows what they're doing can make one of those methods work.

So I had to use windows. I made a BartPE cd and loaded the exe file with it, and it worked perfectly.

---

### Post by tkmud on 2008-03-26
I have found mine to be the best machine on all i want it to do for me. dell is a lable not a clone, procced with pleasure

---

### Post by frotzed on 2008-04-06
I would just like to get a faster processor.  Does anyone know which processors would be compatible with this mother board?

---

### Post by altairpayne on 2008-04-07
Quite happy here, inspiron 530N, no such thing as TOO MUCH RAM and I could afford to max it out.  Ubuntu setup was 1/5 the time of the Vista machine that I sent back to HP, and Ubuntu immediately recognized my Epson 777i printer that Vista refused to work with.  

With all sorts of backroom deals and OEM incentives its hard for the consumer to compare the true cost of a machine with different OSs.  Dell has improved their Ubuntu pricing, and I'm interested in escaping from Microsoft bondage more than worrying about nickels and dimes.  Maybe some consumer crusader is gonna get Dell to lower their prices further but I'm not gonna beat myself up or regret not waiting. 

Every technological migration has a problem, requires some effort and learning curve; no exception here.

Early on I got frustrated trying to download upgrade Feisty Fawn 7.04 codecs and tried installing Kaffiene to watch my mpg's but then I just started letting Ubuntu's built in Update Manager take care of it.  After a few sessions it finally downloaded all of the files it needed, everything started working (including Kaffiene) with no more worries for me.  I'm freely doing my consulting business with OpenOffice and nobody suspects I'm no longer a slave to Microsoft WinDoze.

Open Source RULEZ !

---

### Post by Ikshaar on 2008-04-17
Any info on what kind of motherboard the 530N have ? slot available ?

---

### Post by gbrainin on 2008-04-17
It's the same motherboard as on the 530: [http://www.dell.com/content/products/productdetails.aspx/inspndt_530?c=us&cs=19&l=en&s=dhs&~ck=mn]("http://www.dell.com/content/products/productdetails.aspx/inspndt_530?c=us&cs=19&l=en&s=dhs&~ck=mn") 

Expansion Slots
PCI: 2 Slots
PCIe x1: 1 Slot
PCIe x16 (Graphics): 1 Slots

But of course the graphics slot is used for the video card.

---

### Post by Ikshaar on 2008-04-19
I was wondering what brand and model ? Dell is not making their own motherboard ?!

---

### Post by MJN on 2008-04-20
Dell don't make them (themselves) but they are for all intents and purposes customised motherboards made exclusively for Dell. There have been numerous suppliers over the years - indeed my old Dimension is based on a modified Intel SE440BX motherboard. Whilst the differences can often be subtle (e.g. non-accessible internal temperature sensors on the Dell version) they can also be blatant barriers to compatibility/upgrade (e.g. the use of what appears to be a standard ATX power supply header but actually has all the wires swapped around!).

Mathew

---

### Post by gbrainin on 2008-04-26
> **Ikshaar said:**
> I was wondering what brand and model ? Dell is not making their own motherboard ?!

I have now seen a couple of sources that indicate the 530 motherboard is made by Foxconn.  It's Intel G33/ICH9R chipset.

---

### Post by nanog on 2008-04-27
The sad thing is that I was able to buy a 530 with Q6660 2.4 GHz quadcore for 650. 

Throw away xp, useless 1 gb dimms, 250 gb drive.

Bought 3 750 gb drives (134) 2 sata cables, 5.4-->3.5 converter, and 4 2gb 667 generic dimms.

For less than $1200 I have a Quadcore box with 1.5 GB RAID 5 and 8 Gigs of RAM.

---

### Post by Dragon, Interrupted on 2008-05-01
I ordered one of these earlier today, with all the default options and no monitor.  I have a very tight budget at the moment and this looked like the best deal, even over barebones kits . . . it all adds up!  I'm replacing a machine that has been rebuilt, piece by piece at least three times now, and has suddenly started acting very sluggishly.

I've been using Ubuntu for about two years, but also love FreeBSD.

Quick Q; has anyone updated a 530N to Hardy yet?  If so, how did it go?

---

### Post by frotzed on 2008-05-01
> **Dragon, Interrupted said:**
> I ordered one of these earlier today, with all the default options and no monitor.  I have a very tight budget at the moment and this looked like the best deal, even over barebones kits . . . it all adds up!  I'm replacing a machine that has been rebuilt, piece by piece at least three times now, and has suddenly started acting very sluggishly.

I've been using Ubuntu for about two years, but also love FreeBSD.

Quick Q; has anyone updated a 530N to Hardy yet?  If so, how did it go?
Yeah, I have a 530n and am currently running Hardy.  I had two issues:

1) Change the BIOS setting (I forget what it's called) from IDE to RAID.  This is a lot simpler than it sounds, just have to reboot, edit your BIOS and look around for an option for changing IDE to RAID.

2) Must install from the Alternative CD using the text-based interface.  Insert the CD, reboot and on the options screen have "install Ubuntu" highlighted.  Then hit f6 and at the end of the line that appears at the bottom type pci=nomsi.  I found that solution in another thread here on the ubuntu forums, but I forget where.

---

### Post by Not Sure on 2008-05-24
Received my new Dell, 530 about two weeks ago. It shipped with Ubuntu 7.10.
Here are my specs: Inspiron 530. Intel Pentium Dual Core Processor E2180,
4GB DDR2 SDRAM at 667 MHz, 256MB NVIDIA GeForce 8600GT-DDR3, 19 inch digital monitor (S199WFPF), Sound Bar for Monitor, 16X DVD+/-RW Drive.
Everything works fine out of the box. Great system - fast and quiet.  Decided to upgrade to 64-bit Ubuntu 8.04.  I had to change the integrated peripherals in the BIOS from IDE to RAID - as posted in many threads. In order to get the NVIDIA X-setting and adjustments such as GAMMA, Brightness, Contrast; etc., I downloaded the 64-bit driver file from the NVIDIA website. I received error messages while installing that I was missing some development libraries. I downloaded the files from the Synaptic Package Manager, ran the 64-bit Linux, NVIDIA drivers and it works fine now (see attached screen shot).  The 64-bit Hardy works great.  All four gigabytes of ram are available (limited to 3.2 gigabytes in 32-bit Ubuntu), and my Firefox web browser is the Linux x86_64 version.  The Adobe Flash has not been developed yet for the 64-bit version of Mozilla Firefox.  This is OK for me since I have other 32-bit computers to use when I really need Adobe Flash.  Someday, the 64-bit Firefox browser will have flash - I hope. In conclusion, I am happy to say that I now have a new 64-bit system, with a 64-bit operating system, that will take me into the future for at least a few years.  The system was not marketed as a 64-bit system, however it does work with the 64-bit Ubuntu. I read somewhere that if your system has any kind of a dual core processor, then your system should be capable of running a 64-bit operating system.                               
                                      :popcorn:

---

### Post by newlinux on 2008-06-25
does anyone have the 530N with the X3100 chip instead of nvidia (seems to be what they are currently offering)? I'm curious about the MOBO if it is different (# of slots, SATA and IDE headers, storage spaces for hard drives. Thinking of building a cheap fileserver...

---

### Post by newlinux on 2008-07-07
For anyone that cares I have mine with X3100 and the rest of the mobo specs are the same. I threw in 2 1TB drives and now have a nice fileserver running Hardy (had to upgrade, but that was painless). Great deal and system. The drives cost more than the computer :)

---

