---
title: "Xubuntu works terrible on a PIII 1GHz 128MB ram"
date: 2007-11-10
forum: Desktop Environments
---

### Post by ashrack on 2007-11-10
I installed it the Xubuntu Gutsy alternative CD. And after an hour long installation I was finally at the desktop. But I couldn't do anything since the HDD was constantly working. Just to open the Start Menu I had to wait for a minute and the mouse was jerky. So then I reinstalled with only the command line. And then install XFCE and XORG and Synaptic, Firefox with aptitude. Its better but the HDD is still constantly working. And for google to open in FF I must wait for more than a minute since the HDD is so busy.

I thought 128MB ram is enough for normal work in XFCE. I mean even WinXP which was 3years old and full of software worked much better on this lappy.


Specs:
Laptop HP OMNIBOOK
HDD 10GB
128MB SDR PC 133
PIII 1GHZ

---

### Post by kast on 2007-11-10
Well I do see one possible  issue and that would be the hard drive, 10G is more then enough for the install, but how old is that thing? :) 

Hard drive could be the source of the issue, slow seek/read times etc.

Oh and Memory is on the cheap a little more may also help.

---

### Post by tgalati4 on 2007-11-10
I assume you have a swap drive.  Post the output of:

>free

---

### Post by kerry_s on 2007-11-10
> **ashrack said:**
> I installed it the Xubuntu Gutsy alternative CD. And after an hour long installation I was finally at the desktop. But I couldn't do anything since the HDD was constantly working. Just to open the Start Menu I had to wait for a minute and the mouse was jerky. So then I reinstalled with only the command line. And then install XFCE and XORG and Synaptic, Firefox with aptitude. Its better but the HDD is still constantly working. And for google to open in FF I must wait for more than a minute since the HDD is so busy.

I thought 128MB ram is enough for normal work in XFCE. I mean even WinXP which was 3years old and full of software worked much better on this lappy.


Specs:
Laptop HP OMNIBOOK
HDD 10GB
128MB SDR PC 133
PIII 1GHZ

128 is not enough, xubuntu is bloated as much as gnome. the only way your going to see performance is a custom install or mini distro. try debian less bloat-> [http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso)

---

### Post by bodycoach2 on 2007-11-10
I have to agree with Kerry S. At[ Free Geek Central Florida]("http://freegeekcentralflorida.org"), we've found the need to make sure at least 256 mb ram is installed for our Xubuntu installations. Since most of the donations are between 500 MHz and 1 Ghz, Xubuntu is our primary install. Even a P2 with 384 mb ram does Xubuntu very well.

The biggest bottleneck seems to be bus speed. If I was to shop for a new computer, my focus would be on bus speed, not processor or amount of memory. I can always add memory, and the processor speed seems to only be really important when doing any photo rendering or video editing.

---

### Post by ashrack on 2007-11-10
SDR RAM is expensive and its quite hard to get at least in our country. 
I did the custom install and installed just the essentials of XFCE but it still works slow.

the free command:

```
clean boot with only XFCE terminal opened
tom@laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           114        111          2          0          0         17
-/+ buffers/cache:         94         20
Swap:          149          0        148
```
```
clean boot with firefox and XFCE terminal opened
tom@laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           114        112          2          0          0         20
-/+ buffers/cache:         92         22
Swap:          149         32        116

```

---

### Post by kast on 2007-11-10
Send me a pre-paid envelope and I will send you some. :)

---

### Post by ashrack on 2007-11-10
where U from? I am from balkan, Slovenia

---

### Post by kast on 2007-11-10
Boston MA
I really will send you some,  you can send me a pre-paid and i will hook you up.

drop me a mail [email]eratcliff@inbox.com[/email] and i can give you my address if you like.

---

### Post by AndyLovesLinux on 2007-11-11
heh im down for some free RAM if the offer is for anyone who is in need drop me an email or an IM if you wana talk

---

### Post by ashrack on 2007-11-11
so XUBUNTU lies about there release that it works on 64MB of RAM  but works much better on 128MB RAM. Since if they say it works much better on 128 RAM I expect normal performance and not sluggishness.

ps. I've opened up Bug Report for this incident:
[https://bugs.launchpad.net/ubuntu/+bug/161962](https://bugs.launchpad.net/ubuntu/+bug/161962)

---

