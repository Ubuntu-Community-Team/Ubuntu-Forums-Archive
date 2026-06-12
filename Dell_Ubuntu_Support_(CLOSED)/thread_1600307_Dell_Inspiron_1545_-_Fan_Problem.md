---
title: "Dell Inspiron 1545 - Fan Problem"
date: 2010-10-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Kevin147 on 2010-10-18
Hi there. I have a Dell Inspiron 1545 laptop, and I'm having major fan problems. The thing heats up like its on FIRE! I turn it on, and it stays at about 40C. But then, when I open any application,(It can even be gedit) it heats up to 55C. When I let it just sit there at like 1% CPU, it sits at 50C. I can even get on Facebook, and it will heat up to like 60C. I've tried everything I can possibly find surfing the internet. I've tried i8k, gkrellm, but none of those worked. I tried going in the BIOS and looking there, but I found nothing. Then I uninstalled Compiz config settings manager, it went down for a little while, stayed at about 45C. But, now its back to doing what it was doing..I wish I knew how to fix it, but I don't...

Can someone please give me some options or something on how to fix this please?

Thank you

---

### Post by Jimtheplanner on 2010-10-19
Ah your not the only one......


I did a back to back check with fresh installs of both 10.10 and Mandriva 2010.1 as a test to prove my hardware.

I found most heat is generated from the hard drive just under the left hand "wrist rest" part of the keyboard. Ubuntu averaging 50-52 Deg C and Mandriva averaging 40-42 Deg C. My hard drive is a WD and their spec has a maximum temp of 60 Deg C....

So like you I'm not sure how to reduce the temp.

Regards

Jim

---

### Post by TBABill on 2010-10-19
I have the same machine and mine is using the on-chip GPU in the Intel Core i3-330m. On install I automatically install the applet CPU Frequency Scaling Monitor (whatever it's called) to the top panel and I center it so it's right in my face all the time. I make sure it's set to ondemand. I think in 10.04 it sets to ondemand as default. Are you using 10.04?
 
Other steps to remove heat that have worked for me...
 
1. Remove any other flash player and install Adobe Flash. If you are using the 64 bit Ubuntu, install lovinglinux's Flash Aid. It will remove the 32 bit flash and install 64 bit automagically.
2. Remove open java and install Sun Java. It just runs cooler and more sites work well with it.
3. If you have a proprietary video driver available (ATi or nVidia if you have a separate video card), install the driver.
 
Hopefully something from all that can help.

---

### Post by Kevin147 on 2010-10-19
Thank you for the information. I'm going to try Mandriva, and see if that works. Hopefully it will, because I don't need my laptop to burn out before its 2 years old. And I'm running 10.10 (just upgraded) with 64 bit.

---

### Post by Jimtheplanner on 2010-10-19
Hi Guy's,

A good call with the Java I have sun installed with Mandriva Not sure what was in the Ubuntu (64) install. I may give 10.10 another try.

Kevin see what you think of Mandriva as far as temperatures go!!

Regards
Jim

---

### Post by Kevin147 on 2010-10-19
Okay, I'll check it out. I'm downloading it right now. Thanks for telling me.

---

### Post by EvilGnome on 2010-10-19
I was thinking of upgrading to ubuntu 10.10 from Linux Mint 9. I currently use gkrellm i8k to make sure my fans are running but this thread has me worried that the newest release of ubuntu really overheats computers regardless of safeguards. Is this a warranted fear?

---

### Post by TBABill on 2010-10-19
I wonder if it depends on your graphics card? ATi seems to be having a terrible time with 10.10. My 1545 does not have the add on ATi graphics so it was ok with 10.10 as far as temps. But to have other identical models heating up is a bit worrisome to me. I reverted back to 10.04 so all my machines would be the same...my Realtek wireless refuses to work in 10.10 and it's just an open source driver device.

---

### Post by Joe of loath on 2010-10-20
What processors do you guys have?

Mine runs the T3000 Celeron and the integrated intel video, and I've got few heat problems, although the laptop does run hot, as after a few hours uptime the CPU gets to 60C. It's the same after a few hours of gaming though, so maybe it's just what the bios is set to cool the CPU to.

It's been working fine on 9.04-10.04, and now runs perfectly on Arch too, so it's not a recent kernel thing.

---

### Post by TBABill on 2010-10-20
Mine has the Intel Core i3-330m. It has done pretty well with all distros except the initial release of 10.04/Mint9. Once they fixed whatever was wrong it ran nice and cool, but when they first came out my machine was hitting critical and got up to 86C so I switched for a while to PCLinuxOS. Now all is well again.

---

### Post by Jimtheplanner on 2010-10-20
Hi Guys,

This is my baby....

> Processor: Intel Core 2 Duo T5800 (2GHz, 800MHz FSB, 2MB Cache)
RAM/Memory: 3GB DDR2 Memory
Hard Disk: sudo hddtemp /dev/sda
Display: 15.6&#8243; Widescreen Screen
Extras: Integrated Graphics card
CD/DVD Re-Writer Combo drive

Its currently (only switched on for 1/2 Hour or so)


> james@Inspiron:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +45.5°C  (crit = +100.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +46.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +44.0°C  (high = +100.0°C, crit = +100.0°C)  

james@Inspiron:~$ sudo hddtemp /dev/sda
/dev/sda: WDC WD3200BEVT-22ZCT0: [COLOR="Red"]48°C[/COLOR]


Hope this helps - I still have to give the java & flash aid a try. I was just looking at the Dell operating detail which states temp range 0 to 35 Deg C (I guess this is ambient). I know my HD has a max of 60 Deg C.

Regards
Jim

Just as I've typed this I now have....

> james@Inspiron:~$ sudo hddtemp /dev/sda
/dev/sda: WDC WD3200BEVT-22ZCT0: 48°C
james@Inspiron:~$ ^C
james@Inspiron:~$ ^C
james@Inspiron:~$ sudo hddtemp /dev/sda
/dev/sda: WDC WD3200BEVT-22ZCT0: [COLOR="Red"]49°C[/COLOR]

---

### Post by me.translucent on 2010-10-21
Two years back i lost my mother board while running ubuntu :( never the less i am still using using ubuntu :).

---

### Post by gibbylinks on 2010-10-21
> **me.translucent said:**
> Two years back i lost my mother board while running ubuntu :( never the less i am still using using ubuntu :).

Please accept my condolances. It's difficult, but you will come to terms with it. :(

I think a lot of us geeks have suffered losses over the years :)

---

### Post by Jimtheplanner on 2010-10-22
Hi Guy's

Just wondering of the other 1545 Ubuntu users out there what is your temperature experiences? 

Can you please post so we may compare and find out how big or small an issue this is.....

Regards
Jim

---

### Post by Junior_Sampa on 2010-10-22
Hi colleagues,

It seems to be a kernel 2.6.35 related problem. It got a lot of discussion in Brazilian forum (Ubuntu).

According to the experts I'm in contact there, there are some configurations in generic kernel 2.6.35 enabled that causes higher use of CPU even in idle.

Kernel generic with preempt and performance options and also CFS.

I'm just a newbie about kernels, but I also experiment the temperature problem with my Inspiron 1564 I3 M330.:mad: Comparing the CPU behavior between 10.04 (2.6.32) and 10.10 (2.6.35) 

I could notice the average use with the top command or even uptime in terminal. Some guys compiled the kernel 2.6.34 in Ubuntu 10.10 and the system became normal again. This is not with Ubuntu but all distros with kernel 2.6.35 base. With this behavior change, my temperature increases about 10 degrees in constant CPU use if compared with 10.04.

Then post in Brazilian forum could be checked bellow, sorry, in Portuguese.

[http://ubuntuforum-br.org/index.php/topic,73144.0.html](http://ubuntuforum-br.org/index.php/topic,73144.0.html)

Regards from Brazil.
Junior

---

### Post by colin.p on 2010-10-22
I have 7 and 10.04 on a Dell 1545. Using Firefox in 7, my temps run around 55-70 and the fan will come on at 65 or so and run until down to 45 or so and keep cycling after 5 minutes or so when the temps start climbing. 10.04, on the other hand runs around 45-50 and the fan rarely comes on. Occasionally, the temp will go up, usually if I am copying large files, as an example, and the fan kicks on.
When I got this laptop in May, the temps were slightly higher in Ubuntu, but a couple of kernel updates ago and now Ubuntu actually runs cooler.
Now this laptop is a low end model with Intel cpu and graphics, no gaming machine.
However if you do a search on "load balancing tick" or "power top wake ups from [kernel scheduler]", you will find it is a common problem, at least in lucid. I haven't tried maverick, so I don't know if it still is a problem.

Forgot to mention, I have a 320 GB Samsung drive that is usually in the low 30's c. Also, according to the above post, maverick's kernel still has issues with it. Lucid's kernel is 2.6.32-25, still it's much better than lucid's original kernel, which was 32-21?

---

### Post by Kevin147 on 2010-10-25
> **Jimtheplanner said:**
> Hi Guy's

Just wondering of the other 1545 Ubuntu users out there what is your temperature experiences? 

Can you please post so we may compare and find out how big or small an issue this is.....

Regards
Jim

My Inspiron stays around 50C doing NOTHING at all, and when I do something it rises to 65C. My fan turns on at 65C, and when it gets around 60C, the fan turns off. I can just be on firefox, getting on Facebook and the cpu will be at like 12% with the temperature at like 68C. I'm thinking about just giving this laptop to my brother and getting a brand new one, I'm sick of the fan problems in this Dell Inspiron.

---

### Post by TBABill on 2010-10-25
Facebook is full of flash apps, which is a major problem with Ubuntu. It's getting better with each Flash release, but it still uses a lot of CPU because it does not have hardware acceleration in Linux like it does for Windows and Mac. That's why it heats up online a lot and that's why using Gnash and open source java is a bad thing for a laptop. They can't handle the heat well because they are so compact. I always remove open source java and any other flash if they are installed. It's not a fix, but it does help a little. I even sit with it propped a little on the left side (as I am looking at the screen) because that vent on the bottom draws a lot of air and blows it out the side. So I take a lot of caution to keep the left side and left bottom clear of obstruction from cushions, my clothing and my skin. It stays relatively cool most of the time and only heats up during long video playback.

---

### Post by abdusamed on 2010-10-30
Some one should make a proper bug report. My idle is 50degree c and HDD 52 degree with external fan blowing. Its seems like simulating the solar system weather patter for no reason!

---

### Post by bilalsana on 2010-10-30
i am also using inspiron core i3 and since i upgraded to maverick, it keeps on shutting down due to the processor heating up. plus the sensors always show a reading of 27 degrees!!

---

