---
title: "Inspiron 530 only can use 3g memory"
date: 2007-09-09
forum: Dell  Ubuntu Support
---

### Post by xzuo on 2007-09-09
I am wondering if anyone has tried to use Ubuntu 7.04 x86_64 on Dell Inspiron 530 with 4g or more memory.

I has 4g memory on it, BIOS shows 4g memory, 32 bit XP can only see 3g memory which is expected, because I have quite a few addon card use big address space.

I booted to Ubunutu x86_64 with the hope that it would see 4g memory. I was really surprised that it shows 3g memory too. I checked all bios setting, couldn't find any related settings.

I posted a message at Dell forum. Dell support said to use 4g memory I should use 64 bit XP. I am doubtful about it because Linux can't see it.  I am wondering if anyone has similar problem. Below is the kernel and memory information on my system:
 
# uname -a
Linux xzuo-linux 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux

# cat /proc/meminfo
MemTotal:      3090388 kB
MemFree:        855540 kB
Buffers:        104180 kB
Cached:        1657732 kB
SwapCached:          0 kB
Active:        1203080 kB
Inactive:       853536 kB
SwapTotal:     5119992 kB
SwapFree:      5119992 kB
Dirty:             112 kB
Writeback:           0 kB
AnonPages:      294676 kB
Mapped:          57880 kB
Slab:           139836 kB
SReclaimable:   106388 kB
SUnreclaim:      33448 kB
PageTables:      11348 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   6665184 kB
Committed_AS:   606452 kB
VmallocTotal: 34359738367 kB
VmallocUsed:     53100 kB
VmallocChunk: 34359676923 kB

- xz

---

### Post by AdamTheNewbie on 2008-01-09
Exact same problem. Dell 530. Gutsy.4 x 1gb sticks for a total of 4gb and system only shows 3.2gb User Memory in the "System Monitor". Bios properly shows 4gb.

Adam.

---

### Post by groggomoro on 2008-01-09
Isn't the 3,2 Gb max memory a limit due to a 32-bit OS can't handle more. 64-bit systems handle quit much more memory...

---

### Post by AdamTheNewbie on 2008-01-09
I'm running the x64 kernel on Intel E2160 (64 bit dual core).

---

### Post by xptweakerntn on 2008-01-09
Alright...I JUST got my 530n today, as well as my 4gb of 6400 from crucial. I as well only have 3.2GB availible in ubuntu...so has anyone yet tried the 64bit to see if it'll work?

---

### Post by toblernecro on 2008-01-23
I installed server version plus 64 bit version and non of them works.  Still showing 3.2G, I believe if i can flush Dell's bios then maybe i have a chance

---

### Post by MJN on 2008-01-24
Isn't the 'missing' memory down to the shared memory used by integrated devices such as graphics and PCI Express etc? Even a graphics card with on-board RAM can still require mapping onto the system memory map hence effectively 'hiding' that memory from use by the OS.
 
Mathew

---

### Post by drsaamah on 2008-01-25
but isn't 800 gigs of ram too much to simply blame on shared memory from the graphics card and what not?
I hope this isn't a universal ubuntu issue.  My old computer had a gig of ram and that's what I saw.  However, I specifically bought a 2 gig for my new computer to get my four gigs.  I hope this doesn't end up being the case...

---

### Post by MJN on 2008-01-25
800MB is not that much in the great scheme of things - it's all relative after all.
 
Note that whilst a device may have it's own on-board RAM - e.g. a video card - this RAM still needs addressing by the OS. Hence, this 'real' RAM must be mapped to addresses from the single memory address space. In the 32-bit world we can only address 4GB of memory and hence we cannot directly use 4GB of *real* RAM as well as the video card's *real* RAM as well as the PCI Express *real *RAM etc - there simply aren't sufficient numbers in 32bits to do so. It's all got to be mapped into the same 4GB address space hence the apparent wastage. Of course if you've only got 2GB of real RAM you won't notice any problem - the same 4GB memory space can easily accomodate your 2GB real RAM, the video RAM etc etc.
 
You might think that the solution to this is simply to install a 64-bit OS, however the success of this will rest on whether or not these Dell's are 'true' 64-bit platforms (i.e. supporting 64-bit architectures throughout the board, not just utilising a 64-bit CPU).
 
It maybe worth you searching around, perhaps on the Dell site, to find out what the score is - you guys can't be the first to have put 4GB in your new machines.
 
Mathew

---

### Post by Roger E Critchlow Jr on 2008-01-25
Hi Guys --

I think you're being confused by the terminology on the Ubuntu download pages.

If you've installed a 64 bit Linux, then uname -a will say x86_64 somewhere in the output, but if you've only installed a 32 bit linux, then uname -a will say i686.

When you go to the Ubuntu download page, the downloads labelled xf86_64 are 32 bit systems that run on intel or amd cpus with 32 or 64 bit processors. The downloads labelled amd64 are 64 bit systems that run on intel or amd cpus with 64 bit processors. 

I think the idea is to encourage the use of the 32 bit systems until you're really sure that you want a 64 bit system.

-- rec --

---

### Post by drsaamah on 2008-01-26
I apologize for my software incompetance, but here's what I'm confused about...
Is this inevitable?  In other words, I have 32-bit processor.  So is upgrading to 4 Gb's of ram pointless?  Because if so, I need to get a refund for the 2gb stick I just bought.

---

### Post by naelphin on 2008-01-26
The Inspiron 530 has had its BIOS tweaked so that it is not possible to use all 4GB, including windows (Even in 64-bit mode). It is a subtle way of them to make you get their more expensive products.

---

### Post by MJN on 2008-01-26
That's a little harsh - it is the unavoidable consequence of the use of 32-bit Intel chipsets to minimise cost. Perhaps the net effect is the same, but this is not the intentional crippling of architectures for no other advantage.

Let's not debate the theory - will one of you guys with a Dell and 4GB memory give them a call to get the 'official' line on how much of that RAM they can actually use (and why)? I suspect it might be on of those questions where you'll have to speak to three different people and take an average of the replies! ;)

Mathew

---

### Post by sirchmeister on 2008-02-03
Try this update: [COLOR="Red"]**This is for the Inspiron 530 and 530s**[/COLOR]

[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R174855&SystemID=INSP_DSKTP_D530&servicetag=&os=BIOSA&osl=en&deviceid=14390&devlib=0&typecnt=0&vercnt=4&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=237513](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R174855&SystemID=INSP_DSKTP_D530&servicetag=&os=BIOSA&osl=en&deviceid=14390&devlib=0&typecnt=0&vercnt=4&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=237513)

---

### Post by tuxtt on 2008-02-03
> **sirchmeister said:**
> Try this update: [COLOR="Red"]**This is for the Inspiron 530 and 530s**[/COLOR]

[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R174855&SystemID=INSP_DSKTP_D530&servicetag=&os=BIOSA&osl=en&deviceid=14390&devlib=0&typecnt=0&vercnt=4&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=237513](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R174855&SystemID=INSP_DSKTP_D530&servicetag=&os=BIOSA&osl=en&deviceid=14390&devlib=0&typecnt=0&vercnt=4&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=237513)

Thanks but this update doesn't help. (Was already applied on my inspiron)

---

### Post by noogen on 2008-02-03
I can confirm that over 3gb is a no go for this machine.  

You can search dell community forum and get the same answer.  The manual said 4 gb max with note(*) that you will not see 4 gb; so you cannot win this argument with dell.  It is crippled in the bios.

This is Dell line of low end desktop so people will tell you that Dell will probably not going to uncripple the bios.  This is kind of bad what Dell did but then I can understand.  I only blame my self.  I too, should've RTFM before making the purchase.

I have this machine and have tried pretty much everything but finally gave up.  I bought a better machine and it simply recognize 8 gb after ubuntu 64bit installed.

---

### Post by ericmc783 on 2008-02-03
The following is on the Dell webpage when you go to purchase the 530N.... at the final screen where it shows you all the specs, before you click checkout:

> *Systems configured with 4GB memory or more: The total amount of available memory will be less than 4GB. The amount less depends on the actual system configuration.

So it does say in the fine print that you won't have all 4GB of memory available to you. I just thought it was worth pointing out.

---

### Post by Trindol on 2008-03-26
Anyone with a Dell 530N and 4GB of ram needs to flash the BIOS to ver. 1.0.12. This will allow Ubuntu to see 4GB of ram installed. I'm trying to spread the word across the many threads this has come up in, as I know it annoyed many people.

---

### Post by drsaamah on 2008-04-07
Uh, I highly doubt its a BIOS issue, considering that my BIOS recognizes all 4 gigs.  It definitely seems from what I've read here and elsewhere that its a limitation of the 32-bit OS.

---

### Post by MJN on 2008-04-07
You misunderstand. It is not that the BIOS does not recognise the full 4GB but whether it can allow the host OS access to the full 4GB (along with other addressable memory such as that uesd by the video card, PCI Express bus etc).
 
Upgrade the BIOS as Trindol suggests, then you will be in a better position to suspect the BIOS or not.
 
Mathew

---

### Post by motoperpetuo on 2008-04-07
> **xzuo said:**
>  Dell support said to use 4g memory I should use 64 bit XP. I am doubtful about it because Linux can't see it.  I am wondering if anyone has similar problem. 
- xz

i'm not sure if you still need an answer to this question, but yes that's what i've seen where i work. that is, we have high-power 64-bit computers with 16GB RAM installed. if you install 64-bit Windows XP, they see all 16GB of RAM. if you install 32-bit XP, they only see 3GB.

---

### Post by littlebattler on 2008-04-19
how do you install the BIOS upgrade from Ubuntu? I dont have Vista installed anymore.

---

### Post by drsaamah on 2008-04-19
thats something I would love to know myself.  ive never upgraded or replaced my bios before.  and knowing how would be nice so I can check out that linux bios.

---

### Post by Jackster on 2008-04-19
Was there not an issue with the design of some Intel chipsets? Can't remember the details of it all, but I know on this Macbook I'm on it's got a 64 bit OS and a 64 bit CPU but the chipset used in it prevents the OS from addressing more than 3GB of RAM.

Just thought I'd throw that into the conversation.

---

### Post by MJN on 2008-04-19
It's a good point but in this case the 530 uses Intel's G33 chipset which is good for upto 8GB RAM.

Mathew

---

