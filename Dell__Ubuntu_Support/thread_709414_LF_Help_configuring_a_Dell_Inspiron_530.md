---
title: "LF: Help configuring a Dell Inspiron 530"
date: 2008-02-27
forum: Dell  Ubuntu Support
---

### Post by Don Taylor on 2008-02-27
I am considering buying an Inspiron 530 quad core from Dell Canada.  There is a good deal available this week that I want to take advantage of:
[http://configure.dell.com/dellstore/config.aspx?c=ca&CS=cadhs1&l=en&OC=D530QV_F_1E&dgc=AF&cid=3881&lid=77903](http://configure.dell.com/dellstore/config.aspx?c=ca&CS=cadhs1&l=en&OC=D530QV_F_1E&dgc=AF&cid=3881&lid=77903)

They will not sell me this particular machine with anything other than Vista so I will be installing Ubuntu myself.

When configuring the machine is there anything I should avoid or expect to have problems with?

I understand that there is little to be gained by having 4gb instead of 3gb because most of the top 1gb is shadowed by hardware - is this true?

Can I get a copy of the Dell Ubuntu install CD anywhere?

FWIW.  I will want to run two monitors and the machine will be used mostly for sw. development.

TIA Don.

---

### Post by notwen on 2008-02-27
Everything you want can be found [here]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10").  They have 2 custom Ubuntu images available(for the Inspiron 530) depending on which nVidia card you choose.  Also listed at the bottom of the link is known issues w/ their models and Ubuntu.  The 530 looks to work great, no issues/fixes are posted.  I personally own a Inspiron 1420n and have no complaints.  Best of luck with your future purchase.  =]

---

### Post by Don Taylor on 2008-02-27
> **notwen said:**
>  They have 2 custom Ubuntu images available(for the Inspiron 530) depending on which nVidia card you choose.  

Hmmm... The system that I am looking at is not available with either of the nVidea cards described in the wiki.

I can choose from:
Integrated Intel Graphics Media Accelerator 3100,
128MB NVIDIA GeForce 8300GS,
128MB Radeon ATI HD 2400 PRO,
256MB Radeon ATI HD 2600 XT

I suspect that the nVidea card driver is not FOSS, so how about the others? 

Don.

---

### Post by notwen on 2008-02-27
You are referring to a Inspiron 530n, while Dell's Linux Wiki is referring to a [Dimension 530n deskto]("http://linux.dell.com/wiki/index.php/Clients/Products/Dimension_530n")p.  They also have a list of the available nVidia cards using restricted drivers [here]("http://linux.dell.com/wiki/index.php/Tech/Video/nVidia").  My Inspiron 1420n was only offering the Intel X3100 chipset when they were first introduced, the only issue w/ it is that Compiz-Fusion blacklisted it, so I'm stuck ignoring the blacklist and using 'no xv' when watching videos.  I'm guessing that Dell will provide a fix/workaround for any issue that may arise if they're offering it w/ their Ubuntu pre-installed systems.  I would research the rest of the forum, outside fo the Dell sub-forum for compatibility issues w/ any of the hardware you are considering before adding it to your custom PC to ensure as few problems as possible.  Hope this helped.  =]

---

### Post by Don Taylor on 2008-02-27
Notwen:

I think that you have told me all I need to know - once I read the references properly!

I think I will order the 128MB NVIDIA GeForce 8300GS.

Anybody got any observations on the 3gb. vs. 4gb. question?

Thanks,

Don.

---

### Post by bigfootnmd on 2008-02-29
You do not have to buy a 530N to have Ubuntu on a DELL.  I purchased a refurbished DELL INSPIRON 531S with two gigs of RAM, 250 G HD, Geoforce
6300 on board graphics, Vista Home Basic.  Since I occasionally need Windoze I left Vista in place.  I resized the VISTA partition (splitting the drive) and I loaded Ubuntu 7.10 in the new partition.  Everything works great.
I don't know if you can buy "refurbished DELL" computers  in Canada(look on the Home/office page and see if OUTLET is there).  I saved about $250 US by buying a refurbished unit.  You get the same 1 year warranty.

If you don't want VISTA at all, you can just WIPE it away.  

As to your memory question, I find that two gigs is more than enough.
You might want to go to [www.crucial.com](www.crucial.com) to check prices on memory and compare them with what DELL charges.

Best of luck.

---

### Post by Don Taylor on 2008-02-29
Bigfoot, thanks for this.  I can't find Outlet in the Dell Canada site and I left the bargoon 530 too late as they took it off special overnight.

No matter, I can wait until something good come up again.

---

### Post by RedRat on 2008-03-01
> **Don Taylor said:**
> Notwen:

I think that you have told me all I need to know - once I read the references properly!

I think I will order the 128MB NVIDIA GeForce 8300GS.

Anybody got any observations on the 3gb. vs. 4gb. question?

Thanks,

Don.
Only the Ubuntu for 64 bit cpu will be able to use 4Gb, if you are loading the 32 bit version of Ubuntu, it can only see 3Gb. My understanding is that the 3Gb limitation is in the 32 bit kernel. Perhaps wiser ones here can further elucidate on that.

I have the 530n with 2Gb memory and am running the vanilla 7.10 Ubuntu (due to a screw up on my part) and it runs fine. Love it.

---

### Post by Don Taylor on 2008-03-01
Redrat:

Yes, that is my understanding too.  

The Dell's that I can afford top out at 4Gb but 32-bit OS's can only address 3.25GB of that 4GB.  If I bought 4GB and installed 64-bit 7.10 then I would see all 4 GB, but the 64-bit instruction set is a lot less dense than the 32-bit set so you lose memory that way instead.

It seems to me that it would only be worth going to a 64-bit OS if you had, say 8GB of memory available.

So, with current mainstream mobos it seems that 3GB is the sweet spot for memory.

I run Eclipse which is a memory hog and like to test using virtual machines so lots of memory is nice to have.

Looks like Dell Canada have another nice [deal]("http://configure.dell.com/dellstore/config.aspx?c=ca&CS=cabsdt1&l=en&OC=D400QX_F_1E%20&dgc=AF&cid=3881&lid=77903") ($500 off) on a quad Vostro 400 this week - so I think I will spring for that.

Looking forward to my nice new box.

Don.

---

### Post by zl2k on 2008-03-05
> **Don Taylor said:**
> Redrat:

Yes, that is my understanding too.  

The Dell's that I can afford top out at 4Gb but 32-bit OS's can only address 3.25GB of that 4GB.  If I bought 4GB and installed 64-bit 7.10 then I would see all 4 GB, but the 64-bit instruction set is a lot less dense than the 32-bit set so you lose memory that way instead.

Did you ever tried 4GB + 64bit 7.10? I have a dell inspiron 530 with 4GB and I tried 64bit 7.10 server, 32bit server and 32bit desktop, none of them see 4GB, all can only see 3GB. 

Too many people saying 64bit system will see 4GB for sure. No they can not without doing something extra. And nobody say what the extra is and how.

zl2k

---

