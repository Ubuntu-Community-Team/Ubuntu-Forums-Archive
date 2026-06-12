---
title: "dell inspiron 1564 intel 64 bit processor"
date: 2010-04-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ritendragoel on 2010-04-05
Hi,
Recently I purchase dell ispiron 1564, intel core i3 64 bit laptop, which comes with default windows7 OS. I am a linux professional and want to install Linux on my laptop as dual boot. I tried installing ubuntu 32 bit 9.04 desktop edition,64 bit ubuntu server edition, 64bit ubuntu AMD desktop edition, but nothing works for me now. I need to install ubuntu urgently.
ubuntu installation is not successful. Windows 7 is working fine. I tried all 64bit AMD desktop, too but kernal image is not loading .Finally I installed 9.04 ubuntu 32 bit on my 64 bit intel processor. I am not upgrading it to 9.10 as once it will upgrade to 9.10 it starts hanging even in small application. I tried installing 9.10 32 bit and 64 bit both desktop for AMD processor but after installing successfully even. The kernel image is not loading .
So i kept my system to 9.04, but I am surprised to see that no gcc and g++ compiler is working on my laptop.. I checked the gcc and g++ version they are latest one. I installed build-essential too. After searching for suitable solution, I came to know that I should installed intel 64 bit gcc and g++ compiler for ubuntu (1GB). (it will take couple of days to download) :(
still R &D is going on.
Please help me in this matter.

Help in this regard is highly appreciated!!!!!!!!

---

### Post by stardustdk on 2010-04-05
Even though 10.04 ain't released yet, I'll suggest one of two: 
1: Upgrade to 10.04 (update-manager -d)
2: Wait for Beta2 release and install that (recommended).

Your hardware is *very* new, that's why. 
And 9.10 has a lot of bugs as I found out.

Hope this helps.

Best regards

Stardustdk

---

### Post by ritendragoel on 2010-04-05
But if I upgrade to 9.10 from 9.04 then internet starts hanging.Or should I do the fresh installation of ubuntu 10 via live cd. will it support all the g++ and gcc compilation.

---

### Post by stardustdk on 2010-04-05
In that case either 1 of 2:
1: DL Beta1 and update (much)
2: DL Beta2 by the 8. April

It's a LTS, can't imagine it don't support g++ and gcc compilation's.

Best regards

---

### Post by ritendragoel on 2010-04-05
Thanks a lot...........I installed ubuntu 10.04 beta version and my gcc and g++ compilers are also working very fine...10.04 is really awesome.

---

### Post by stardustdk on 2010-04-05
NP... 10.04 looks like their best to date, by far.
And that they use Debian Testing instead of Debian Unstable means fewer problems to begin with :).

I guess that they'll get back to Unstable on the "standard" releases, meaning non-LTS releases.

Best regards and happy working ;)

---

### Post by hallboy3 on 2010-04-29
Hi guys.
I updated my Ubuntu (x64) from 9.10 to 10.4 without problems.
My laptop:
DELL Inspiron 1564

[LIST]
[*]Intel i3 330M
[/LIST]

[LIST]
[*]ATI Radeon HD 4330
[/LIST]

[LIST]
[*]HDD 500Gb.
[/LIST]

[LIST]
[*]All functional keys work fine.
[/LIST]

[LIST]
[*]All drivers are available.
[/LIST]

[LIST]
[*]Aggregate report in attached file for example..
[/LIST]
Enjoy :guitar:

---

### Post by earnoth on 2010-05-03
> **hallboy3 said:**
> Hi guys.
I updated my Ubuntu (x64) from 9.10 to 10.4 without problems.
My laptop:
DELL Inspiron 1564

[LIST]
[*]Intel i3 330M
[/LIST]

[LIST]
[*]ATI Radeon HD 4330
[/LIST]

[LIST]
[*]HDD 500Gb.
[/LIST]

[LIST]
[*]All functional keys work fine.
[/LIST]

[LIST]
[*]All drivers are available.
[/LIST]

[LIST]
[*]Aggregate report in attached file for example..
[/LIST]
Enjoy :guitar:

I'm thinking of buying this exact model.  Is ACPI working?  I'd read on other posts that some Dell's had issues there in Linux.

Have you experienced any issues on the 1564?

---

### Post by ritendragoel on 2010-05-06
Hi ,
I Install 10.04 stable version and now things are working fine.

---

### Post by dosht on 2010-05-06
Hi every one,

Thanks for this info; Now i'll try ubuntu 10.4.
But what about the wireless driver? I couldn't use it on 9.4.
And do we have to use 32bit or we can use 64AMD?

Thanks a lot.

---

### Post by ene_dene on 2010-05-10
I'm also thinking about buying Dell Inspiron 1564. The system I'll use is Ubuntu 10.04 x64.
Here are the questions:
1. Do the property ATI drivers work well, is it stable?
2. Does the wireless work fine, is it stable?
3. Does web camera work?
4. Does microphone work?

---

### Post by binary10 on 2010-05-10
I've just (today) gotten a new 1564 i3-330m (N0056401), intel GMA. 230GB 5400rpm, The lowest cost one.

I had an existing Lucid 10.04 64-bit build (full encrypted lvm disk working) so I just cloned it swapped out the factory supplied disk and booted the cloned disk :).

Only few issues experienced.

- Wireless - At first had no wireless, just hardwired the laptop and first tried the fwcutter, but was getting quite a few hangs. So de-activated and installed 'Broadcom STA proprietary wireless driver'

- Odd system freeze with Virtualbox running but I can't rule out other things. VB is running now and its fine.

- No sound - Solved by making sure I had the 'Analog Speakers' selected in the output connector, don't just have 'Analog Output' 

- No suspend/hib - but that's because I've got to sort out encryption issues.


All in all very happy (skype webcam works assume mic will work), ubuntu zips along on this i3 - Windows 7 default disk was painful on logoff/shutdown it seemed just too slow. I made up my mind that Win7 would be placed in the safe emergency pile (ready to be used as a backup drive, one day).

---

### Post by ene_dene on 2010-05-10
> **binary10 said:**
>  intel GMA
This will probably make your head hurt. My friend has that card and experiences constant crushes, for example when watching youtube, movies etc.

---

### Post by binary10 on 2010-05-11
> **ene_dene said:**
> This will probably make your head hurt. My friend has that card and experiences constant crushes, for example when watching youtube, movies etc.

Why would it make my head hurt ? 

I've been watching Youtube and BBC iPlayer videos no crashes, so far, all 64bit mode and compiz. The fan kicks in now and then that's about all so far.

---

### Post by ene_dene on 2010-05-11
> **binary10 said:**
> Why would it make my head hurt ? 

I've been watching Youtube and BBC iPlayer videos no crashes, so far, all 64bit mode and compiz. The fan kicks in now and then that's about all so far.
I'm glad to hear that. My friend had stability issues with that graphic card. Perhaps the issue was resolved on 10.04.

---

### Post by binary10 on 2010-05-11
> **ene_dene said:**
> I'm glad to hear that. My friend had stability issues with that graphic card. Perhaps the issue was resolved on 10.04.
Possible.

I made sure that ubuntu lucid 64bit was going to be about 95% working by booting off of my cloned backup usb drive first doing a few tests (webcam,vb,compiz,cairo-dock) installing wireless drivers etc, then I then made the clone of my backup drive to insert in the drive bay.

My hackintosh experiment with it didn't go so smoothly - irratic mouse movement during osx install quickly choose the path I wanted to get back on.

---

### Post by hallboy3 on 2010-05-14
> **earnoth said:**
> I'm thinking of buying this exact model.  Is ACPI working?  I'd read on other posts that some Dell's had issues there in Linux.

Have you experienced any issues on the 1564?

Don't worry. All worked perfect.

---

### Post by hallboy3 on 2010-05-14
> **dosht said:**
> Hi every one,

Thanks for this info; Now i'll try ubuntu 10.4.
But what about the wireless driver? I couldn't use it on 9.4.
And do we have to use 32bit or we can use 64AMD?

Thanks a lot.

Select proprietary Broadcom driver.
I use 64AMD OS (native multithreading, hyper-threading mode)

---

### Post by hallboy3 on 2010-05-14
> **ene_dene said:**
> I'm also thinking about buying Dell Inspiron 1564. The system I'll use is Ubuntu 10.04 x64.
Here are the questions:
1. Do the property ATI drivers work well, is it stable?
2. Does the wireless work fine, is it stable?
3. Does web camera work?
4. Does microphone work?

You can buy it and install Ubuntu 10.04 without fear.
the only one drawback of this notebook: the maximum resolution of the display only 1366px x 768px.

---

### Post by stitch3 on 2010-05-17
Does anyone have suspend working with 10.04?  I have tried both 32 and 64 bit with no luck.

---

