---
title: "Kynaptic; Synaptic problems"
date: 2005-04-18
forum: Desktop Environments
---

### Post by tyrannicalpolitics on 2005-04-18
Okay,

Firstly I can't get online in Linux because I have a damn winmodem. Secondly because I can't get online I can't really install anything using Kynaptic. Thirdly I want synaptic not kynaptic, but I can't find it even in Konsole. I think this is because it has to be included in the bin file for the packages and not just in the /var/cache/apt/archive directory. When I try to install synaptic using: *apt-get install* it doesn't work and cannot find the file. My friend burned me a bunch of files and I dropped them into aforementioned directory but I still cannot install **anything**. I think I am missing dependencies for some of my files which wouldn't be as much a problem if I was using synaptic. Also I have a vague conception of what Universe Repository is, but can anyone elaborate? I've been surrounded by so many esoteric Linux terms in the past few day that my head hurts. I'm a N00b, by the way.  I think Linux is awesome, but they should have easier and better methods available to those poor bastards that can't get online easily because of evil winmodems.  Any tips would be very appreciated. Thanks.

Cheers,

-b-

---

### Post by Gezzer on 2005-04-18
[QUOTE=tyrannicalpolitics]Okay,

Firstly I can't get online in Linux because I have a damn winmodem. Secondly because I can't get online I can't really install anything using Kynaptic. Thirdly I want synaptic not kynaptic, but I can't find it even in Konsole. I think this is because it has to be included in the bin file for the packages and not just in the /var/cache/apt/archive directory. When I try to install synaptic using: *apt-get install* it doesn't work and cannot find the file. My friend burned me a bunch of files and I dropped them into aforementioned directory but I still cannot install **anything**. I think I am missing dependencies for some of my files which wouldn't be as much a problem if I was using synaptic. Also I have a vague conception of what Universe Repository is, but can anyone elaborate? I've been surrounded by so many esoteric Linux terms in the past few day that my head hurts. I'm a N00b, by the way.  I think Linux is awesome, but they should have easier and better methods available to those poor bastards that can't get online easily because of evil winmodems.  Any tips would be very appreciated. Thanks.

Cheers,

-b-[/QUOTE]
 synaptic is in universe which is not enabled by default

u want so much, but it is best to learn first ...

---

### Post by tyrannicalpolitics on 2005-04-18
[QUOTE=Gezzer]synaptic is in universe which is not enabled by default


u want so much, but it is best to learn first ...[/QUOTE]

Hmm no..Didn't help much... I already knew all that, but thanks at any rate... I know synaptic is disabled by default, but knowing that isn't helping me much...Yes I am learning and already know quite a bit. Anyone that can actually answer **ANY** of my questions, I would really appreciate it. Thanks

-b-

---

### Post by Jonathan2007 on 2005-04-18
To add the universe repository check out [this](http://www.ubuntuguide.org/#extrarepositories) site. It has lots of other tips on there to so be sure to look at the whole site. But I guess I don't see what good enabling extra repositories is if you can't get online. Kynaptic, Synaptic, and apt-get all need the internet. So I don't know if this will help but if you can get internet enable the repositories as mentioned on that site and then open Kynaptic (just one time so you can install Synaptic) and it should refresh its list from the repositories and then go find Synaptic and install it. You could also use apt but make sure you do an apt-get update first so it will refresh its list.

---

