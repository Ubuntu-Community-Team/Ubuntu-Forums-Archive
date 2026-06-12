---
title: "About RAM"
date: 2008-12-16
forum: General Help
---

### Post by rolodoom on 2008-12-16
Hello. I was reading my motherboard specifications and saw that it supports 8GB RAM. Then I remember that back in the time when I used win2s I only bought 3 GB RAM memory 'cause the seller told me that couldn't use more.

Well, Today I bought 4 GB more of RAM and then my Ubuntu box has 6 GB RAM, but System monitor tells me that I only have 3.2 GB. Weird. How can I use the full amount of ram, 'cause I'm planning to buy some other 4GB and use 8GB as the manufacturer says at the specifications book of my board.

BIOS recognizes the 6 GB RAM. Linux also says 6 GB but pc is not faster or anything.
I type 
```
$ sudo dmidecode --type 17
```and get:
```

# dmidecode 2.9
SMBIOS 2.3 present.
Handle 0x0018, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0017
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: J6H1
    Bank Locator: CHAN A DIMM 0
    Type: DDR2
    Type Detail: Synchronous
    Speed: 533 MHz (1.9 ns)
    Manufacturer: 0x2C00000000000000
    Serial Number: 0x00000000
    Asset Tag: Unknown
    Part Number: 0x000000000000000000000000000000000000

Handle 0x001A, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0017
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: None
    Locator: J6H2
    Bank Locator: CHAN A DIMM 1
    Type: DDR2
    Type Detail: Synchronous
    Speed: 533 MHz (1.9 ns)
    Manufacturer: 0x0000000000000000
    Serial Number: 0xFFFFFFFF
    Asset Tag: Unknown
    Part Number: 0x524D31474233383343412D34334443FFFFFF

Handle 0x001C, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0017
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: J6J1
    Bank Locator: CHAN B DIMM 0
    Type: DDR2
    Type Detail: Synchronous
    Speed: 533 MHz (1.9 ns)
    Manufacturer: 0x2C00000000000000
    Serial Number: 0x00000000
    Asset Tag: Unknown
    Part Number: 0x000000000000000000000000000000000000

Handle 0x001E, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0017
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: None
    Locator: J6J2
    Bank Locator: CHAN B DIMM 1
    Type: DDR2
    Type Detail: Synchronous
    Speed: 533 MHz (1.9 ns)
    Manufacturer: 0x0000000000000000
    Serial Number: 0xFFFFFFFF
    Asset Tag: Unknown
    Part Number: 0x524D31474233383343412D34334443FFFFFF
```My box is Intel DUal Core 2 Duo, so, maybe if I used the 64 Bit version I would see my 6GB RAM?? Or what could be happening??

---

### Post by oilchangeguy on 2008-12-16
is'nt 8gb overkill? adding more ram is not going to make a computer any faster, if it's not fully using what's already installed. for example if you're running several programs at once, and look at the system monitor and note the computer is only using say 1024mb of 2048mb. more is not better.

---

### Post by jerome1232 on 2008-12-16
64 bit is the answer, 32 bit operating systems can only use up to ~4 GB's of ram (usually only see's like 3.5 of it)

If your motherboard supports PAE and you have some overwhelming crushing desire to stay with 32 bit.... you could compile your own kernel to use PAE or use the server kernel which has PAE enabled by default.

---

### Post by damis648 on 2008-12-16
32-Bit Operating Systems cannot use more than 4GB ram (which includes video memory, that reserved for kernel, etc, so for you comes out to 3.2GB). In order to use >4GB, you must either:
A. Install 64-bit Ubuntu.
B. Install the Ubuntu server kernel which is compiled with PAE which allows you to use >4GB ram on a 32-bit system.
C. Compile your own kernel with PAE to support >4GB RAM, but this is a long and more advanced task. Post back if you want to undertake this.

---

### Post by reality1011 on 2008-12-16
Can anyone explain this, I have been stumped for some time...  < don't flame me for vista >

Btw ... I know about 32-bit limitations but this is something that is recognizing above more then ~3.2GB

[img]http://realitybasedsolutions.com:8000/misc_crap/ram.jpg[/img]

---

### Post by Arup on 2008-12-16
The impact of more ram would only be realized when you use memory intensive apps. Otherwise you would hardly feel the impact, since you are on quad core, I strongly suggest you upgrade to Ubuntu x64 to enjoy the full benefits from the quad core and 6gb RAM, I enjoy my dual quad with 8gb and will soon upgrade to 16gb when RAM prices drop.

---

### Post by reality1011 on 2008-12-16
^ I have 8gb :)

The only reason for vista is really for when I have to work from home (Lotus notes), CS3 suite, itunes, and turbolister...

Not to thread jack but I have been trying to convert to ubuntu 100% but Ive been focusing more on maintaining/developing my ubuntu based webserver

---

### Post by jerome1232 on 2008-12-16
Unless Vista 32 bit is PAE Enabled then it can't actually use all of that.

---

### Post by dcstar on 2008-12-17
> **reality1011 said:**
> Can anyone explain this, I have been stumped for some time...  < don't flame me for vista >

Btw ... I know about 32-bit limitations but this is something that is recognizing above more then ~3.2GB
........

There are many posts in the 64-bit forum addressing this issue, search them out if you want a detailed explanation.

---

### Post by sdennie on 2008-12-17
> **oilchangeguy said:**
> is'nt 8gb overkill? adding more ram is not going to make a computer any faster, if it's not fully using what's already installed. for example if you're running several programs at once, and look at the system monitor and note the computer is only using say 1024mb of 2048mb. more is not better.

No, in this case, more is always better.  On linux, adding more memory will almost always make your computer more responsive as time goes on because of the disk cache.  You can open every application on the system in 1G or less of RAM but, the more RAM you have the larger your disk cache can grow and the less the disk has to be accessed.  As the disk is by far the slowest part of your machine, the less frequently you access it, the faster your machine will run.  

You can potentially speedup the population of the disk cache using preload instead of waiting for it to fill naturally:

```

sudo apt-get install preload

```

It doesn't usually need further configuration but, you can look in /etc/preload.conf for more information.

> **damis648 said:**
> 32-Bit Operating Systems cannot use more than 4GB ram (which includes video memory, that reserved for kernel, etc, so for you comes out to 3.2GB). In order to use >4GB, you must either:
A. Install 64-bit Ubuntu.
B. Install the Ubuntu server kernel which is compiled with PAE which allows you to use >4GB ram on a 32-bit system.
C. Compile your own kernel with PAE to support >4GB RAM, but this is a long and more advanced task. Post back if you want to undertake this.

Yes, this is correct.  Some information about the pros and cons of these three methods can be found here: [ Ubuntu with 4GB+ of memory]("http://ubuntuforums.org/showthread.php?t=855511")

---

### Post by jespdj on 2008-12-17
> **reality1011 said:**
> Can anyone explain this, I have been stumped for some time...  < don't flame me for vista >

Btw ... I know about 32-bit limitations but this is something that is recognizing above more then ~3.2GB



32-bit Windows Vista (with Service Pack 1) can see that you have 6 GB RAM, but that does not mean it can use all of it - like all 32-bit systems (without [PAE](http://en.wikipedia.org/wiki/Physical_Address_Extension)) it cannot use more than 4 GB.

---

### Post by rolodoom on 2008-12-17
have another question, is there any need to change the size of swap partition??? 
Thanks for the answers. I'm downloading ubuntu 64.

> **oilchangeguy said:**
> is'nt 8gb overkill? adding more ram is not going to make a computer any faster, if it's not fully using what's already installed. for example if you're running several programs at once, and look at the system monitor and note the computer is only using say 1024mb of 2048mb. more is not better.
A. Well, don't know who told you that but I really think that I'm gonna see the change in my pc when rendering blender stuff.
B. I want 8GB RAM, 'cause I want it. Isn't linux about fun and freedom, anyway? The reason I changed to Linux was 'cause I started to play with ubuntustudio, and multimedia stuff, so, how am I going to be sure that 8gb of ram are a waste if I don't give it a try by myself??? For me, more could always be better!!! Cheers.

---

### Post by Elfy on 2008-12-17
If you want to hibernate then swap should equal or be greater than RAM so the swap size is up to you.

---

### Post by jasonkirk2006 on 2008-12-17
> **reality1011 said:**
> Can anyone explain this, I have been stumped for some time...  < don't flame me for vista >

Btw ... I know about 32-bit limitations but this is something that is recognizing above more then ~3.2GB

[img]http://realitybasedsolutions.com:8000/misc_crap/ram.jpg[/img]

Since SP1, Vista displays the amount of all installed physical memory, not the amount of available RAM. (see [KB946003]("http://support.microsoft.com/kb/946003")).

But that does not mean that it can handle all of it. I think the most trusted source about available memory is the Start>Programs>Accessories>System Tools>System Information, which displays the correct amount in the **Total Physical Memory** section.

For more reading:
[http://blogs.technet.com/markrussinovich/archive/2008/07/21/3092070.aspx]("http://blogs.technet.com/markrussinovich/archive/2008/07/21/3092070.aspx")

---

### Post by rolodoom on 2009-03-25
> **jasonkirk2006 said:**
> Since SP1, Vista displays the amount of all installed physical memory, not the amount of available RAM. (see [KB946003]("http://support.microsoft.com/kb/946003")).

But that does not mean that it can handle all of it. I think the most trusted source about available memory is the Start>Programs>Accessories>System Tools>System Information, which displays the correct amount in the **Total Physical Memory** section.

For more reading:
[http://blogs.technet.com/markrussinovich/archive/2008/07/21/3092070.aspx](http://blogs.technet.com/markrussinovich/archive/2008/07/21/3092070.aspx)

Dude, I think we're talking about Ubuntu here, go to talk about win2s somewhere else.

**Solution: **
I installed Ubuntu Intrepid Ibex 64 bits and now I can access all my RAM :-)

Thanks for all your replies.

---

