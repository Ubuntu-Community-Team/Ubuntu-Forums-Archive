---
title: "Bandwith question"
date: 2010-01-05
forum: Desktop Environments
---

### Post by ElevenWarrior on 2010-01-05
I had a question about bandwith. I ran a few speed tests and I was getting a download rate, (according to them) of 936KB, and upload of 386 KB.
Yet when I download things, I almost never over 124KB, so why is this?
I know it has something to do with the servers i download from, but i'm not totally sure.
Any thoughts?

---

### Post by warfacegod on 2010-01-05
Sounds like you have a 1Mb service. You'll never down load anything at your bandwidth limit. 124Kb seems a *little* low for 1Mb service but not by much. Try downloading two or three sizeable (20 MB or so) files at the same time, they'll each probably get about 90 - 100 Kb depending on where you get them.

---

### Post by ElevenWarrior on 2010-01-05
If I download files at that size, the connections get split. One gets 20-25k, the other gets 60k, and the last one gets 10-15K. Is there any way I can get more out of my connection?

---

### Post by lisati on 2010-01-05
A number of things can affect performance, including the route the data takes between a server and your machine, traffic intensity on the route, and the quality of your connection. There might even be a longer electronic route between a server that's geographically close than one that's a few hundred (or thousand) miles away. The dynamics of network connections is a rich subject!

---

### Post by ElevenWarrior on 2010-01-05
so then there is nothing I can do?

---

### Post by warfacegod on 2010-01-05
> so then there is nothing I can do?


Not necessarily.

Read this, it may help allot, a little, or not at all.


[http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by garvinrick4 on 2010-01-05
The Ubuntu mirrors are all different bandwidths and days behind or up to date. I switched to
a mirror with larger bandwidth and made big, big difference in download speeds. There are over 325 mirrors though out the world. 


[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

### Post by sanderj on 2010-01-05
> **ElevenWarrior said:**
> I had a question about bandwith. I ran a few speed tests and I was getting a download rate, (according to them) of 936KB, and upload of 386 KB.
Yet when I download things, I almost never over 124KB, so why is this?


I think you're mixing kilobits and kilobytes:

I you have a 1 Mbps (=1 mega**bit** per second = 1000 kilo**bit** per second) connection, you can download at that speed. However, the important thing is that typical applications (like Firefox) will show the downloadspeed in BYTES per second. As there are 8 bits in 1 byte, and there is protocol overhead, getting 124 kBps (capital B) on a 1000 kbps (small b) is quite good. I normally divide the bits by 10 to get the bytes, which would give you 100 kBps on a 1000 kbps connection.

HTH

---

### Post by hvidehenning on 2010-01-05
> **ElevenWarrior said:**
> I had a question about bandwith. I ran a few speed tests and I was getting a download rate, (according to them) of 936KB, and upload of 386 KB.
Yet when I download things, I almost never over 124KB, so why is this?
I know it has something to do with the servers i download from, but i'm not totally sure.
Any thoughts?

if you are using a router try to reset it then give it a new firmware if avalibel then run your setup it worked for me some network companies change from ppoE to ppoA and they have old own brand config in the routers hope it helps. after go to [www.tdconline.dk](www.tdconline.dk) and in the serch box "søg" type 1090 then you have a 100mbit test box "(søg) is danish for serch"

---

### Post by warfacegod on 2010-01-05
> I think you're mixing kilobits and kilobytes:

I you have a 1 Mbps (=1 megabit per second = 1000 kilobit per second).... As there are 8 bits in 1 byte, and there is protocol overhead, getting 124 kBps (capital B) on a 1000 kbps (small b) is quite good. I normally divide the bits by 10 to get the bytes, which would give you 100 kBps on a 1000 kbps connection.


1 Mbps should be 1024 KB not 1000

If it's 8 bits to a byte then why are you diving bits by 10 to get bytes? You should be multiplying bits by 8 to get bytes.

Elevenwarrior your 124 KB (assuming F.F.'s KB are actual KB not really Kb) is, now that I did the math, is excellent. 124 X 8 = 992 Kb. That means you're utilizing nearly 100% of your bandwidth. The only way to improve your download speeds would be to pay for a faster connection. I still suggest reading the thread I posted earlier, it will help you to gain a better understanding of things and help you to get your browser itself using your bandwidth and your hardware more efficiently.

---

### Post by ElevenWarrior on 2010-01-05
no I'm not using most of my bandwith.lets say I downloaded 4 files. I get 124KB of download speed, divided by 4,not times 4.so each file gets 31 KB not 124., 124/4= 31KB a second. And yes I'm sure it kilobytes, not bytes.

---

### Post by ElevenWarrior on 2010-01-05
> **warfacegod said:**
> Not necessarily.

Read this, it may help allot, a little, or not at all.


[http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")

actaully it did help FF run faster and smoother, but I'm still only getting about 1/10th of my connection speed on my download. :(

---

### Post by warfacegod on 2010-01-05
Yes you are. 124 KB is almost exactly the same thing as 1024 K*_b_*. Which is, according to your first post, just about what your bandwidth tested at. I'm glad the post helped.

---

### Post by warfacegod on 2010-01-05
Internet uses K*_b_*

Firefox show it to you in K_*B*_


Big B = Bytes

little b = bits

8 bits to 1 Byte

---

### Post by ElevenWarrior on 2010-01-07
> **warfacegod said:**
> Internet uses K*_b_*

Firefox show it to you in K_*B*_


Big B = Bytes

little b = bits

8 bits to 1 Byte

okay now I'm throughly confused.
I thought their were 1,000 bytes in a kilobyte.
and their were 1,000 KiloBytes in a Megabyte.

---

### Post by vhinz on 2010-01-07
I would like to echo Warfacegod's post:

1 Mbps should be 1024 KB not 1000.

Do not confuse this with other scientific conversions that goes by power of 10's (adjusting zeroes).  conversion of this type is quite different.  Ever wonder why memory is not exactly 100, 250, 500, 1GB, etc...its 128, 256, 512, 1024, 2048, 4096.  But in general terms of memory, starting 1GB, they are rounding it off but just note the difference.

I'm not familiar with your ISP but some ISP (atleast here in Philippines) would advertise as 1MB but note that this is shared with other subscribers.  Ask for your guaranteed upload and download speeds.  If you are on dedicated line and that line is connected to just one unit, your download should hit about 700kb.

---

### Post by warfacegod on 2010-01-07
Using 1000 instead of 1024 is fine for estimating. It's easier for people think in 1000's but for computers 1024 is easier. That's why the specs you see on hardware are always divisible by 8.

I agree with vhinz, you're most likely on shared bandwidth but unless you try downloading big files during peak time (mornings and mid to late afternoon) you shouldn't notice.

---

### Post by ElevenWarrior on 2010-01-07
> **warfacegod said:**
> Using 1000 instead of 1024 is fine for estimating. It's easier for people think in 1000's but for computers 1024 is easier. That's why the specs you see on hardware are always divisible by 8.

I agree with vhinz, you're most likely on shared bandwidth but unless you try downloading big files during peak time (mornings and mid to late afternoon) you shouldn't notice.

ahh that makes sense. Other people in our area do have a Verizon internet as well. Hence its probably shared. this makes sense. 
thank you!

---

### Post by warfacegod on 2010-01-07
Glad to help. Again, if you want to have faster downloads, you'll need to ask Verizon to upgrade your service.

---

### Post by cascade9 on 2010-01-07
> **warfacegod said:**
> 1 Mbps should be 1024 KB not 1000

If it's 8 bits to a byte then why are you diving bits by 10 to get bytes? You should be multiplying bits by 8 to get bytes.

Correct. However, I've seen the '10bits to the byte' convention a lot. The few times I've pressed anybody about it, the best answer I've got is "8bits =1 byte, sure, but with overheads, etc, you are very lucky if you can 1byte of every 8 bits of rated speed, people get upset when they arent getting 'full speed' so we just use 10bits to the byte to save trouble'. 

I can understand that logic, but IMO, they should stop selling internet connections in bits,and move to bytes. Or at least change '1Mb' to 1Mbit' so its more clear. I was tired of explaining bits and bytes to newbies 8 years ago :|

---

### Post by warfacegod on 2010-01-07
With all the modern hardware having all these big sounding specs (2.4 GB quadcore, 3G RAM, etc.) it would be pretty hard to sell the average Joe a 256 KB internet connection. Although, in theory, I agree. I also think that calling 768 Kb connections or even 3 Mb connections "highspeed" needs to stop too. It's highspeed only when compared to dial-up. With companies like Cox or Comcast offering 20 - 30 Mb speed tiers, "highspeed" is misleading at best and I might go so far as to call it fraudulent.

---

