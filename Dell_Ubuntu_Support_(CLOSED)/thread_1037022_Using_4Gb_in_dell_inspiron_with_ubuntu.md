---
title: "Using 4Gb in dell inspiron with ubuntu"
date: 2009-01-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by zeroed on 2009-01-11
Hi,

I have dell inspiron 1501.

I was with 2Gb of RAM but I have upgrade it to 4Gb.

Now both Ubuntu 32 and Windows XP 32 shows only 2.6 Gb.

I have downloaded Ubuntu x64 and tried to install it. I'have got a warning about "memory hole" and something about "iommu" in bios but couldn't find such option. After I try to install it or run live cd - it just stops to answer from some time.

I checked cd twice - everything is ok.

I tried to check memory - but computer saddenly halted..

The bios is latest.

Can anybody say if it's possible, using any workarrounds to use (really use, not fake) all 4Gb of RAM in ubuntu with dell inspiron 1501?

---

### Post by zeroed on 2009-01-11
Probably, computer halts during memtest because of cpu temperature.. And I don't know how to prevent it.

Also I noticed that ECC (or EEC) option is Off in memtest, is it ok?

Also I noticed that the memory hole really exists.

memtest shows values like: 

1 - 2.6 (gb) - this is what I see right now 
some value with 3 Gb
and then 4 - 5 Gb

How to disable this memory hole on 1501? I can not find it in bios. Can I turn it off on motherboard using switches? What is it, memory hole, why do I need it?

---

### Post by natehall on 2009-01-12
I've bought memory expansions for other computers that were bad. I suspect that is what is going on here: It will crash your system bigtime . If you realy think its temperature, cool your computer down (perhaps the frig? Not the freezer though! ) and then elevate it so a fan can cool it off on both sides. I have a one gigabyte 1420 running 64bit Ubuntu.  It originally came with a 32 bit install so its actually running BETTER than new.

---

### Post by zeroed on 2009-01-12
> **natehall said:**
> I've bought memory expansions for other computers that were bad. I suspect that is what is going on here: It will crash your system bigtime . If you realy think its temperature, cool your computer down (perhaps the frig? Not the freezer though! ) and then elevate it so a fan can cool it off on both sides. I have a one gigabyte 1420 running 64bit Ubuntu.  It originally came with a 32 bit install so its actually running BETTER than new.


It was cpu temperature, memory is ok. 

BTW, I have installed server kornel and booted using it. Now I can see 3.8 Gb on 32-bit system.

What is going on? I thought it's impossible. 

And I still can not install 64 bit system with regural kernel. And now I'm not sure if I really need it. I think 3.8 is enough. The reason of I have installed this additional memory is virtualbox. I need XP in it. So now it runs really good.

:guitar:

---

### Post by gibbylinks on 2009-10-19
I've got one of these (Inspiron 1501). I thought they could only take 2gb ?

I'm currently running Karmic with no problems

---

### Post by zeroed on 2009-10-19
Well, I have 4Gb on my Dell 1501.

Actually, I have 3.8 Gb on Ubuntu with server kernel and 4Gb in Gentoo.

---

### Post by gibbylinks on 2009-10-19
> **zeroed said:**
> Well, I have 4Gb on my Dell 1501.

Actually, I have 3.8 Gb on Ubuntu with server kernel and 4Gb in Gentoo.

Ah I think were at cross purposes here. I'm talking physical RAM not hard disk space.

Or do you have 4gb of RAM. If so what spec ?

---

### Post by zeroed on 2009-10-19
I mean RAM.

I have bought 2 additional GBs.

[http://support.dell.com/support/edocs/systems/ins1501/en/om_en/html/specs.htm](http://support.dell.com/support/edocs/systems/ins1501/en/om_en/html/specs.htm)

---

### Post by gibbylinks on 2009-10-19
> **zeroed said:**
> I mean RAM.

I have bought 2 additional GBs.

[http://support.dell.com/support/edocs/systems/ins1501/en/om_en/html/specs.htm](http://support.dell.com/support/edocs/systems/ins1501/en/om_en/html/specs.htm)

That's whats baffling me. The link you quoted states

[SIZE=2]**Memory **[/SIZE]
          [SIZE=2]Memory module connector[/SIZE]
         [SIZE=2]two SODIMM connectors[/SIZE]
           [SIZE=2]Memory module capacities[/SIZE]
         [SIZE=2]512 MB, 1 GB, and 2 GB[/SIZE]
           [SIZE=2]Memory type[/SIZE]
         [SIZE=2]1.8-V SODIMM DDR-2[/SIZE]
           [SIZE=2]Minimum memory[/SIZE]
         [SIZE=2]512 MB[/SIZE]
           [SIZE=2]Maximum memory[/SIZE]
         ***[SIZE=2][COLOR=Red]2 GB[/COLOR][/SIZE]***

---

### Post by zeroed on 2009-10-19
Yes, I know. 

But the fact is that I have at least 3.8 Gb in Ubuntu with server kernel =)

---

### Post by gibbylinks on 2009-10-20
Sounds good to me.

Could you tell me what you've got in there and where from ?

;0)

---

### Post by zeroed on 2009-10-20
Sorry, I don't understand your question =)

---

### Post by gibbylinks on 2009-10-20
[SIZE=2]**Memory **[/SIZE]
          [SIZE=2]Memory module connector[/SIZE]
         [SIZE=2]two SODIMM connectors[/SIZE]
           [SIZE=2]Memory module capacities[/SIZE]
         [SIZE=2]512 MB, 1 GB, and 2 GB[/SIZE]
           [SIZE=2]Memory type[/SIZE]
         [SIZE=2]1.8-V SODIMM DDR-2[/SIZE]
           [SIZE=2]Minimum memory[/SIZE]
         [SIZE=2]512 MB[/SIZE]
           [SIZE=2]Maximum memory[/SIZE]
         [I][B][SIZE=2][COLOR=Red]2 GB

[/COLOR][/SIZE][/B][/I][SIZE=2][COLOR=Red][COLOR=Black]For example have you got 2x 2gb [/COLOR][/COLOR][/SIZE]200 Pin SO DIMM DDR2 PC2-4200 533MHz ram[SIZE=2][COLOR=Red]
[/COLOR][/SIZE]

---

### Post by zeroed on 2009-10-20
Ok, now I see =) (English is foreign language for me...)

2x:

[IMG]http://i027.radikal.ru/0910/6e/fe5de9ffee26.jpg[/IMG]

[IMG]http://s53.radikal.ru/i142/0910/8b/92b0e9c633af.jpg[/IMG]

Information from hardinfo:

```

-Memory-
Total Memory		: 3982936 kB
Free Memory		: 3266360 kB
Buffers		: 24020 kB
Cached		: 411336 kB
Cached Swap		: 0 kB
Active		: 301288 kB
Inactive		: 334124 kB
Active(anon)		: 206144 kB
Inactive(anon)		: 0 kB
Active(file)		: 95144 kB
Inactive(file)		: 334124 kB
Unevictable		: 16 kB
Mlocked		: 16 kB
High Memory		: 3152328 kB
Free High Memory		: 2529676 kB
Low Memory		: 830608 kB
Free Low Memory		: 736684 kB
Virtual Memory		: 5654840 kB
Free Virtual Memory		: 5654840 kB
Dirty		: 320 kB
Writeback		: 0 kB
AnonPages		: 200064 kB
Mapped		: 71516 kB
Slab		: 26312 kB
SReclaimable		: 17076 kB
SUnreclaim		: 9236 kB
PageTables		: 4756 kB
NFS_Unstable		: 0 kB
Bounce		: 0 kB
WritebackTmp		: 0 kB
CommitLimit		: 7646308 kB
Committed_AS		: 703788 kB
VmallocTotal		: 122880 kB
VmallocUsed		: 38888 kB
VmallocChunk		: 81872 kB
HugePages_Total		: 0
HugePages_Free		: 0
HugePages_Rsvd		: 0
HugePages_Surp		: 0
Hugepagesize		: 2048 kB
DirectMap4k		: 8184 kB
DirectMap2M		: 901120 kB

```

But keep in mind that you have to install server kernel, restart your ubuntu and load with server kernel.

But after that you can find some problems with video adapter.. unfortunately =(

Before server kernel:

[IMG]http://s45.radikal.ru/i108/0910/c1/2093e8227228.png[/IMG]

After server kernel:

[IMG]http://s45.radikal.ru/i110/0910/59/73c0707d9d0c.png[/IMG]

If you know any command that will help to identify ramm details - show me.

---

### Post by gibbylinks on 2010-03-04
Hi,

Yes this works. I now have 4gb in my Dell 1501 laptop, although it also works with the 64 bit kernel. No need to use the server kernel.

This is an issue with 32 bit kernels not recognizing over a certain amount of memory. I forget the exact figure.

:P

---

