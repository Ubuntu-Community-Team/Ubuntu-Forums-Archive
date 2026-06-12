---
title: "Ubuntu 8.10 lags big time!"
date: 2009-01-31
forum: Desktop Environments
---

### Post by GetOutOfBox on 2009-01-31
Hi, I just installed Ubuntu 8.10 from the alternate installer because the normal installer also lagged a lot. When I say lag, I mean responsivness and graphical lag. Moving the mouse around the screen is like watching a slide-show. Then if I click somthing, it takes forever to respond. This occured in the GUI installer and then after I successfuly installed to the disk. I remember reading somthing somewhere about VGA problems, but I can't remember where or what. Heres my specs:

CPU: Intel Pentium 4 2.8GHZ HyperThreading Prescott core socket LGA775

mobo: Fujitsu-Siemens P5SD2-FM microATX

HDD: 250GB WD Caviar SATA2

vid card: MSI Radeon 4350 PCIe

RAM: 1.25GB DDR2 RAM (PC5300)

The system is kept very cool (for a prescott cpu, at least) at CPU temp 45C and mobo temp 26C average. This is because I have an awsome Zalmans CPU fan + a big desktop fan blowing into the case a 2nd setting (3 settings).

---

### Post by GetOutOfBox on 2009-01-31
It just hit me, I had trouble with partitions when installing and had to manually creat the partitions. I did not make a swap partition because it took me long enough to make a root partition, so that may be the problem. I had to manually rezize the windows xp partition with Partition Magic, then I split the partition into an NTFS and a ext3 partition, but forgot the swap. Can I just manually use Partition Magic to creat a swap partition, and if I can, what size should it be?

---

### Post by jrusso2 on 2009-01-31
I am thinking your problem is graphics related.  Having the ATI video and all.

---

### Post by jrusso2 on 2009-01-31
I am thinking your problem is graphics related.  Having the ATI video and all.

There are no fast rules about swap being one and half times ram anymore.  But if you want to suspend to ram you want at least the size of your ram.

---

### Post by sandy8925 on 2009-01-31
I've never heard of Fujitsu-Siemens mobo and am not sure how good it is. That might be a problem. As jrusso2 said the graphics card might be a problem but I don't think ATI is all that bad.

If you bought some cheap RAM it's probably not working properly and is slowing down the system and causing some errors. Having good and proper (and enough)RAM is very(VERY) important.

Is a lot of hard disk activity taking place? If so it's possible that (for some reason) DMA is not enabled and the hard disk is working in PIO mode which would slow down the system a lot.

I have a way slower comp and it works pretty well for me.

Having said all that benchmark the system and see what you get. I don't know any benchmarking utilities but for the hard disk run:

sudo hdparm -t /dev/sda

3-4 times and see what speeds you get.

---

### Post by sandy8925 on 2009-01-31
And create a swap partition too. Yes you can do it manually. Just get an empty partition and format it as a linux swap partition using gparted.  I guess 1 GB is the max you'll ever need.

---

### Post by GetOutOfBox on 2009-01-31
I created a swap partition and it still lags. I heard that ubuntu has compatibility issues with some ATI cards. Im a linux noob, I understand the basics about linux (e.g kernel headers, etc) but I dont know how I can fix this. Im pretty sure this is a video issue, as GUI installer also lagged, but the text based installer ran fine. Ubuntu only requires about have of what windows needs to run and windows runs flawlessly on my machine. Is their any kind of specific startup options I should use? Plz help!

---

### Post by skunkbad on 2009-01-31
Maybe you should try 8.04, and if it still lags, then you know it's your hardware. I installed 8.04 on a super old computer with a 20GB HDD and 500MB RAM, and it is doing fine. This computer is about 9 years old, and has a pentium 3 processor.

---

### Post by toasty_ghosty on 2009-01-31
I have a system with just about the same specs. I tried running 8.10 on it as well as 8.04 and while 8.04 is much less of a hog then 8.10, it still had its laggy moments. I'm currently using a Pentium 4 with 512 memory and the Ubuntu derived Fluxbuntu. It couldn't be snappier. Now fluxbox may be a bit too lean for you, after getting used to it, I love it...I'd suggest that to you give it a try. With your gig of ram, there should be no lag. I've ran Fluxbuntu with 256mb of ram without issues.

Toast

---

### Post by GetOutOfBox on 2009-01-31
Ok, Im sure my pc can handle ubuntu. 2.8GHZ cpu ubuntu reccomends 750mhz, 1.25GB DDR2 (PC5300) RAM ubuntu reccomends 384MB. My PC should not have any trouble running ubuntu. Windows XP is a 1000x more performance hogging then ubuntu, and it runs flawlessly. And remember that even the installer lagged the same way as os did, which did not happen on the text based installer. So I'm thinking maybe Ubuntu's GUI system might be the problem because think, an os installer should not lag, as it does not run any background services, it it basicaly the only proccess running. Ubuntu used to run fine on my 1.3GHZ P3, with SDRAM and ATA HDD, so my new pc should have no trouble. So what I'm saying is I'm pretty sure its a video thing, I may be wrong, just a hunch ;).

---

### Post by GetOutOfBox on 2009-01-31
bump.

---

### Post by Monsieur Gonzalez on 2009-02-01
Follow the directions you'll find on the [Binary Driver How to (Ati)]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") . Everything should be smoother once you activate direct rendering.

---

### Post by clhsharky on 2009-02-01
Hello GetOutOfBox

    I think it is video problem to, not because its ATI or Ubuntu but maybe hardware compatibility.

    Your motherboard Fujitsu-Siemens P5SD2-FM and chip set - North bridge:SiS 649DX & South bridge :SiS 966, they are 1st gen: PCI Express X16.
    And your video card : MSI Radeon 4350 PCIe, is a PCI Express 2.0 x16 that is 2nd gen PCI Express. Searching I have found some first gen 4350's, but not MSI there all 2nd gen cards.

    Now computer components are usually backwards compatible, like runing a PCI slot card (specs match) on your board. But not as good for Forward compatibility, your 1st gen motherboard trying to run a 2nd gen card (specs don't match). I under stand that PCI Express 2.0 has twice the bandwidth and 2 times the wattage(75W) as 1st gen.

    I have found that matching all your computer components gives the best stability (and less headache) . I may be wrong in this case, but think about it and maybe check it out.
People mix parts all the time and many times it works, but no one has your hardware.

    Have you checked for newer Bio's at Fujitsu-Siemens for your board,it might help. Also check out your 12V power rail, you can see that in the bio's (that's at idle of course not under load). The reason I say that is most of your computer runs on that rail-the CPU,video card,fans and more. Seeing that you have upgraded several components and if you still have the original power supply. PC builders(company's) use what they need to get by with (cost you know)and not much more. And power supply's do weaken with age.

    Ubuntu 8.10 supports ATI and Nvidia as long as there not old, other wise go 8.04. Plus installing drivers is not that difficult, lots of How To's. The drivers for ether one is pretty good right now, I do have both.

Good Luck

---

### Post by GetOutOfBox on 2009-02-01
So I should try 8.4 then? I saw all the ati driver fixes, but everything is slow slow that it would probable take hours if I half to do it while logged in.

---

### Post by GetOutOfBox on 2009-02-02
I know everyone here is a fan of ubuntu, but please be open minded for this question I have, would openSUSE probably not have this problem? I have read that openSUSE has very good hardware auto-detect and config. Its a big file to dl and would take long time to install, I'm just wondering if it might work better with an ati card. Thx!

---

### Post by Crafty Kisses on 2009-02-03
Try something lighter maybe Xubuntu, see if that doesn't give you any results.

---

### Post by GetOutOfBox on 2009-02-03
ok will do. Thnx!

---

### Post by jamesmcm on 2009-03-07
I've got a machine with an AMD64 processor, 4GB DDR2 RAM, and an ATI Radeon HD 3600 and 8.10 lags like mad. The only time I've used Ubuntu before was 8.04 on an older machine with a Nvidia card and that was fine. I think ATIs drivers must still suck.

---

### Post by EspenHoh on 2009-03-08
I have the same graphics card, I think this hd4350 is causing the troubles. 3d performance is actually good, 2d sucks. Since this card is quite new and low end I don't think it is a priority. Only the latest driver from AMD support it. Do we get an open source driver for this card anytime soon?

---

