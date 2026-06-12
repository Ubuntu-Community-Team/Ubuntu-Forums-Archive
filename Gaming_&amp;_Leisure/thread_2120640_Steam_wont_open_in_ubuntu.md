---
title: "Steam wont open in ubuntu?"
date: 2013-02-27
forum: Gaming &amp; Leisure
---

### Post by ianlikescake on 2013-02-27
I posted this in the steam community but I haven&#8217;t got a response yet and I figure I'd get more help posting my problem here :P So I recently installed Ubuntu 12.10 on my brand new computer. I wanted  to try out Steam for Linux so I went to install it off the steam  website. The installation seemed to go alright but when I click on the  steam icon... nothing. It doesn&#8217;t open up or anything. I'm totally new  to Ubuntu and Linux in general but I know I know enough to open up the  terminal and try to open up steam from there, When I do that it shows this 
```
Running Steam on ubuntu 12.10 64-bit
STEAM_RUNTIME is enabled automatically
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
Installing breakpad exception handler for appid(steam)/version(0_client)
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadAlloc (insufficient resources for operation)
```Can someone help me out with this? 

My Computer setup is
> Motherboard: Gigabyte F2A85X-UP4 (Dual UEFI Bios)
CPU: AMD A10 5800K (3.8GHz,  4.0MB Cache)
GPU:AMD Radeon&#8482; HD 7660D (built into CPU)
SSD: Mushkin 120GB
RAM: 8GB Mushkin 996770 DDR3

---

### Post by myromance123 on 2013-02-27
It looks like your Steam installation could be messed up.

Before installing Steam, did you make sure to update Ubuntu?
I know this is basic steps, but it's best to get it out of the way first.

Some things you can also try alternatively, is to install Steam from Ubuntu's Software Center or redownload the Steam installer.

EDIT: It looks like, if you're using 64Bit you won't be able to see Steam in the USC. I've just tried and can confirm this. Sorry about that.

---

### Post by Bölvaður on 2013-02-27
I got 64-bit Ubuntu and installed steam from their website. During the install the installer asked if it can additionally get certain libraries that are missing (which I would need if I am running a 64-bit OS).

I do not know what libraries those are, and after a short google search I do still not know which ones they are, but it still should be able to help you.

Try googling this > steam linux library 64bit
one of the most important libraries to run steam is ia32-libs so start with this terminal command ```
sudo apt-get install ia32-libs
```


Insufficient resources is obviously wrong error, but indicates steam is missing something to run.

---

### Post by ripps818 on 2013-02-28
I believe that Steam and virtually all of Valve's games are 32-bit only. But, like Bölvaður says, this is easily remedied by installing the 32-bit libraries.

Some of the games might come with both 32-bit and 64-bit versions, like FTL. It contains libraries and executables for both architectures and the Launch script determines which set to use.

I can understand why Valve would choose 32-bit as the default arch, it's possible for it to be compatible with either architecture and only requires some minor extra software to be installed to make compatible for 64 bit.

Although, their games might have better performance on 64-bit if they were compiled to naively use the extra registers on the 64-bit CPU's. So, maybe, in the future Valve with have different builds for both. But I wouldn't be predicting it anytime soon. They have far too many bugs and things to be concerned about than optimizing for a single architecture.

---

### Post by darkcrimson on 2013-03-03
> **myromance123 said:**
> 

EDIT: It looks like, if you're using 64Bit you won't be able to see Steam in the USC. I've just tried and can confirm this. Sorry about that.

Not true. I have 12.10 64-bit installed and acquired Steam from the USC.
[http://ubuntuone.com/2AwOAXHymz0MSV6AElJa7j](http://ubuntuone.com/2AwOAXHymz0MSV6AElJa7j)

Be sure to use "steam-launcher" as your search string. ;)

---

