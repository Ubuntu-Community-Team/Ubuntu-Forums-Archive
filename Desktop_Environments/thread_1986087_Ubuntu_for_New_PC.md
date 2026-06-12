---
title: "Ubuntu for New PC"
date: 2012-05-24
forum: Desktop Environments
---

### Post by GirishSharma on 2012-05-24
Hello,
 
I am going to buy a new desktop for my home usages and learning purpose. The PC will 16GB RAM, 1 TB HDD, Core i 7 64 bit machine. Till now I have planned that my host OS will be ubuntu, so first question is :
 
1.Should I use 32bit or 64 bit Ubuntu, which version you recommend.
2.I wish that version should support mobile internet.
3.I will keep Win 7, Oracle Enterprise Linux in Virtual machine, so please tell me the name for the virtulazation for said version.
4.In the VM i wish to install .net 10 on windows 7, so will it work ?
5.In the Oracle Enterprise Linux I will install Oracle 11g version for my main study/testing and learning purpose.
6.Something good which you suggest to insall/configure.
 
Keeping in view my requirement, kindly tell me the Ubuntu version and bit info.
 
Thank you and Regards
Girish Sharma

---

### Post by eleftg on 2012-05-24
1. with 16GB RAM i guess it's best to stay with the 64 bit version
2. Mobile internet? You can't be sure.

that's what i can answer.

---

### Post by soumoks on 2012-05-24
> **GirishSharma said:**
> Hello,
 
I am going to buy a new desktop for my home usages and learning purpose. The PC will 16GB RAM, 1 TB HDD, Core i 7 64 bit machine. Till now I have planned that my host OS will be ubuntu, so first question is :
 
1.Should I use 32bit or 64 bit Ubuntu, which version you recommend.
2.I wish that version should support mobile internet.
3.I will keep Win 7, Oracle Enterprise Linux in Virtual machine, so please tell me the name for the virtulazation for said version.
4.In the VM i wish to install .net 10 on windows 7, so will it work ?
5.In the Oracle Enterprise Linux I will install Oracle 11g version for my main study/testing and learning purpose.
6.Something good which you suggest to insall/configure.
 
Keeping in view my requirement, kindly tell me the Ubuntu version and bit info.
 
Thank you and Regards
Girish Sharma
first of all,install ubuntu 64 bit,if u have processors built by AMD,since ur goin with an i7,i recommend u to use a 32 bit version,i don't know what u mean by mobile internet,but rest assured as ubuntu 12.04 supports the latest technologies..:),if ur plannin of dual booting with windows now or in the future,i suggest u to install windows before intsalling ubuntu as windows overwrites the grub bootloader..as for virtualisation,use oracle virtualbox.Most of the os's will be supported by virtualbox(btw oracle virtualbox is a free..:)).

---

### Post by GirishSharma on 2012-05-24
> **eleftg said:**
> 1. with 16GB RAM i guess it's best to stay with the 64 bit version
2. Mobile internet? You can't be sure.
 
that's what i can answer.
 
 
Thanks for your reply.  Which version do you recommend i.e. 9,10,11 or 12 please ?
 
Version should support mobile internet (I have run mobile internet in 10.04 LTS without any issue, but no luck in 11.04), because I don't have broadband connection; uses only mobile, so mobile interenet support is also my main requirement please.
 
Thanks again for your reply.
 
Regards
Girish Sharma

---

### Post by GirishSharma on 2012-05-24
> **soumoks said:**
> i don't know ,but rest assured as ubuntu 12.04 supports the latest technologies..:),if ur plannin of dual booting with windows now or in the future,i suggest u to install windows before intsalling ubuntu as windows overwrites the grub bootloader..as for virtualisation,use oracle virtualbox.Most of the os's will be supported by virtualbox(btw oracle virtualbox is a free..:)).
 
I bit confused by your reply :
>first of all,install ubuntu 64 bit,if u have processors built by AMD,since ur goin with an i7,i recommend u to use a 32 bit version,
You mean if I don't have AMD processor then should I use 32 bit else 64 bit ? or what, kindly elaborate it.
 
>what u mean by mobile internet
Since I don't have boradband connection, so I usages nokia mobile (at this time using the same from XP box), so I wish that version should support mobile internet connectivity easy as smooth as it was in 10.04 LTS.
 
I don't want to have dual boot with win 7.  I just want windows in VM only.  Will .net 10 run smoothly (if you or anyone have such setup please).
 
Regards
Girish Sharma

---

### Post by cortman on 2012-05-24
> **soumoks said:**
> first of all,install ubuntu 64 bit,if u have processors built by AMD,since ur goin with an i7,i recommend u to use a 32 bit version,i don't know what u mean by mobile internet,but rest assured as ubuntu 12.04 supports the latest technologies..:),if ur plannin of dual booting with windows now or in the future,i suggest u to install windows before intsalling ubuntu as windows overwrites the grub bootloader..as for virtualisation,use oracle virtualbox.Most of the os's will be supported by virtualbox(btw oracle virtualbox is a free..:)).

Whew! Please don't use text speak when replying to support questions- it's difficult to understand and unsuitable for the nature of the forums.
To OP; you must have 64 bit if you want to utilize all 16 GB of RAM, or use a PAE kernel, and still that limits you to utilizing 3 GB or less per application.
As far as mobile internet goes, I use easytether with Android and it works great- they make a .deb for Debian/Ubuntu. I would test run it with a live CD on any existing machine to confirm.

---

### Post by GirishSharma on 2012-05-24
Thank you cortman for your reply.  Actually earlier when I was running ubuntu 10.04 LTS on my P4 32 bit machine, I have used nokia c5-03 (symbian) device; it worked like a charm, but due to some reasons, I installed 11.04 on the same PC but could not able to configure the same device on it.  So, I am bit confused that whether the current 12.04 supports mobile interenet or should I go with 10.04 (my tested version).
 
What else should I have on a new PC in the world of Ubuntu.
 
Regards
Girish Sharma

---

### Post by Erik1984 on 2012-05-24
> **soumoks said:**
> first of all,install ubuntu 64 bit,if u have processors built by AMD,since ur goin with an i7,i recommend u to use a 32 bit version,i don't know what u mean by mobile internet,but rest assured as ubuntu 12.04 supports the latest technologies..:),if ur plannin of dual booting with windows now or in the future,i suggest u to install windows before intsalling ubuntu as windows overwrites the grub bootloader..as for virtualisation,use oracle virtualbox.Most of the os's will be supported by virtualbox(btw oracle virtualbox is a free..:)).

You must be confused by the naming of the ubuntu images. amd64 means 64 bit Ubuntu, _not_ only for AMD processors. 

@TS definitely 64 bit. You can use 32 bit with PAE kernel but that is slower than 64 bit.

---

### Post by cortman on 2012-05-24
> **GirishSharma said:**
> Thank you cortman for your reply.  Actually earlier when I was running ubuntu 10.04 LTS on my P4 32 bit machine, I have used nokia c5-03 (symbian) device; it worked like a charm, but due to some reasons, I installed 11.04 on the same PC but could not able to configure the same device on it.  So, I am bit confused that whether the current 12.04 supports mobile interenet or should I go with 10.04 (my tested version).
 
What else should I have on a new PC in the world of Ubuntu.
 
Regards
Girish Sharma

If it ran on Ubuntu 10.04 it should run on 12.04. Are you able to download a 12.04 ISO image and burn it to a disc? If so, I would recommend booting from it and trying it on there.
If it worked in the past it almost certainly is workable in the future.
As far as what else, that sounds like a pretty potent PC. I think you'll be happy with it.
Check out what graphics card you'll be getting, and google "graphics_card_name drivers ubuntu" or "xxx compatibility with ubuntu" to see what others' experience with it has been.

---

### Post by GirishSharma on 2012-05-24
> **cortman said:**
> If it ran on Ubuntu 10.04 it should run on 12.04. Are you able to download a 12.04 ISO image and burn it to a disc? If so, I would recommend booting from it and trying it on there.
If it worked in the past it almost certainly is workable in the future.
As far as what else, that sounds like a pretty potent PC. I think you'll be happy with it.
Check out what graphics card you'll be getting, and google "graphics_card_name drivers ubuntu" or "xxx compatibility with ubuntu" to see what others' experience with it has been.
 
I am once again thankful to you for your continue and valuable reply.  I had two experiences i.e. in 10.04 mobile internet worked like a charm i.e. i just plugged in my mobile device through USB cable, after 5-6 second there was a connection to connect, but I tried almost all efforts for the same in 11.04 but no luck, so I am much concern that is 12.04 64 bit Ubutuntu supports mobile internet connection or not.
 
Apart from mobile internet, my other concerns are will I be easy and smooth of using dotnet 10 in win 7 VM, will VM will support Oracle enterprise linux etc.
 
At the moment, I don't have yet purchased the PC, just discussing here proactively that will I be able to use all my main requirements or not please.  So, till now one answer has been finalized i.e. go for 64 bit Ubuntu... its now time to think for 10.04 or 12.04.
 
Regards
Girish Sharma

---

### Post by cortman on 2012-05-24
> **GirishSharma said:**
> I am once again thankful to you for your continue and valuable reply.  I had two experiences i.e. in 10.04 mobile internet worked like a charm i.e. i just plugged in my mobile device through USB cable, after 5-6 second there was a connection to connect, but I tried almost all efforts for the same in 11.04 but no luck, so I am much concern that is 12.04 64 bit Ubutuntu supports mobile internet connection or not.
 
Apart from mobile internet, my other concerns are will I be easy and smooth of using dotnet 10 in win 7 VM, will VM will support Oracle enterprise linux etc.
 
At the moment, I don't have yet purchased the PC, just discussing here proactively that will I be able to use all my main requirements or not please.  So, till now one answer has been finalized i.e. go for 64 bit Ubuntu... its now time to think for 10.04 or 12.04.
 
Regards
Girish Sharma

1) Win7/.NET should work just fine in a VM
2) No experience with OEL, but I imagine it'd work just fine (you could try googling "OEL in vbox" or something similar, for more info)
3) 10.04 will be supported for another year, so if it suits your needs, it is probably the best option. By the time it's EOL 12.04 will have most current bugs ironed out and should be rock solid.

---

