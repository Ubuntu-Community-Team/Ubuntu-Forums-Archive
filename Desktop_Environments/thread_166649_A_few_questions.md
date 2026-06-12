---
title: "A few questions"
date: 2006-04-26
forum: Desktop Environments
---

### Post by Ewzzy on 2006-04-26
I have been using Ubuntu since August.  I really like it and I am currently using it on my laptop here at college.  I have hit a few snags that keep me using windows on my desktop box.

Startup hangs on Configuring Network Interfaces.(pressing PrtSC/SysRq forces it continue)
I can't get WPA wireless to work.
I can't get dial-up through AOL to work.
I need to be able to use an equivalent to DVD Shrink.
Battery life is listed as plugged in at all times/battery drains faster than windows.

Here at college I can use there Hi-Speed internet but when I'm at home I have to use my mom's dial-up.(can't change until Thanksgiving due to contract with AOL that got me the laptop)  Wireless on campus is WPA so I have to keep a windows partition to use it.  I also have to use DVD shrink on windows to copy movies for my film class.(all of the films at my school are copies so I won't even begin to get into the morals of it)  If I could solve these problems I wouldn't need to use windows.

Also if I could at least solve the AOL dial-up problem, I can get my mom to swith her old WinME pc over.

Thanks for everything,
Andrew 'Ewzzy' Rayburn

---

### Post by utUtu on 2006-04-26
We can't help you unless you tell us
-- laptop make, model
-- wireless card type, builtin, or pcmcia, make, model

For me I have Compaq Turion that uses Broadcom builtin wireless gear.  The new Dapper tries to install a native driver that does not work, so I use ndiswrapper.  Sorry I don't know the link but you can find it in the WIKI- findpages for Ndiswrapper.

I tried to blacklist the bcm43xxx but seems not to work, so I just renamed the driver by prepending/appending BAD to it's name so it won't load.  Otherwise, it will clobber the ndiswrapper.

---

### Post by Ewzzy on 2006-04-27
My apologies, I am using a Toshiba Satelite L25-S1193. And just to clarify, wireless works to a degree. Un-encrypted and WEP(though I haven't tested it much) both function. WPA encryption isn't listed under System/Administration/Networking. So far I haven't had to use NdisWrapper.

[EDIT: for spelling]

---

### Post by Ewzzy on 2006-04-30
I upgraded to flight 6 dapper and that solved most the problems.  I still need help with AOL Dial-Up.  I downloaded the Penggy package, but I don't know how to use it.

---

