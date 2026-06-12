---
title: "CPU &amp; GPU Temp upto 85C!!"
date: 2008-04-02
forum: Dell  Ubuntu Support
---

### Post by Kiri on 2008-04-02
I have a dell xps m1210 and have installed ubuntu hardy herron (8.04) on it. The temperature of the CPU and GPU is very high:
65+ Celsius in an idle state (CPU usage at less than 5% or negligible)
The GPU is also mid - high 60s.

I used lm-sensors to give me this information, and it is also reflected when I run a temperature monitor software in a windows XP guest on the ubuntu host machine. 

But if I dual boot into windows XP , the temperatures seem much lower (40s for CPU, although the GPU is still quite high)

In ubuntu, if I'm actually using the CPU a bit, the temperature can rise up into the 80s, even close to 90!!

Does anyone know what I can do about this??
I do not think it is a hardware problem, since the temperature in windows is much lower...
I suspect somehow ubuntu is not regulating the temperature correctly (?)

Anyway, please give me some advice if you know about this issue. I don't want to fry my cpu. 
Thanks


Edit: When I ran lm-sensors it detected my cpu, but did not detect fans... could it be that my fans are not running?

---

### Post by viciouslime on 2008-04-02
You should probably report this as a bug on launchpad. Whilst GPU temperatures in the mid 60s are perfectly normal, the difference of 20degrees in your CPU temps is not.

That said, 60deg for a laptop CPU isn't too high... 90 is pushing it a little though. Many laptops will get into the 80s under full load, I'm using a macbook and even running mac os x which is highly customised and optimised for mac hardware, it will hit about 83deg under full load.

Another possibility is that windows is reporting the temperature incorrectly... can you feel a physical difference if you put your hand underneath the laptop around the area where the CPU is located?

---

### Post by Kiri on 2008-04-02
Hey vicious, thanks for the advice. I'll have a look at launchpad and see if anyone has posted anything yet. 
60 degrees would be ok, but if I watch a video it gets close to 80, and anything CPU intensive puts it up to 90 pretty quickly.

I haven't done the 'hand' test yet, but I haven't noticed a substantial difference in the heat. Although it is quite hot I have to say. I'll see how hot it feels in windows later. 

Hmm, I just looked at the bottom of the laptop and the windows license key sticker is stlightly blackened from heat. Not that that really bothers me, but it does seem like it is very hot

---

### Post by viciouslime on 2008-04-02
Yeh it definitely shouldn't blacken any stickers on the bottom! There can be irregularities in temperature reporting, especially with linux, one of my machines reports in linux that it runs at 260-275 degrees celcius... i doubt that somewhat.

However, I think we can rule out the temperature being reported incorrectly in either OS, because the laptop is clearly getting above what it should be at if it is blackening stickers.

It is rare that this kind of thing is actually caused by an operating system though (in my experience at least) so it could well be that it is hitting roughly equal temperatures (both of them higher than they should be) in windows and ubuntu but a reporting error is making it look like it is purely a fault of ubuntu's. If this were the case, then there is probably a hardware problem, a failed fan, some dust that's stuck, something like that.

Have you noticed any difference in fan utilisation between the two operating systems? It could be that ubuntu is somehow preventing the fans from turning on, most laptops do allow for software control of fans. Again, this is unlikely though.

---

### Post by viciouslime on 2008-04-02
I've just found this: [http://forum.notebookreview.com/showthread.php?t=149633]("http://forum.notebookreview.com/showthread.php?t=149633")
The guy replying to that thread recommends sending it back, but if you're not the only one, maybe the thing is just supposed to run at that temperature... the burnt sticker is a little concerning though, and I must admit, I would usually say anything over 85 is edging towards unacceptable, but then we don't necessarily know that you are going over 85 in ubuntu as it could well be that the temperature is reported incorrectly and it's actually just as hot as in windows...

---

### Post by Kiri on 2008-04-03
Thanks again viciouslime. I have not realyl noticed a difference with the fans or what not. And Yesterday I installed gtkellm and used it to force my fans to stay on at high speed for about an hour. They did seem to be blowing a lot of hot air out (and were quite noisy) but the temperature of the machine was reported as being only a few (maybe 5) degrees cooler. 

Is there any way I can get a more accurate temperature report if the OS is reporting it incorrectly?

Perhaps it is just a hot laptop. I really haven't pushed it very far in ubuntu yet, and am reluctant to do so if the temperature is going so high... 

I might try and get some compressed air and blow around, and also I read something about someone replacing the heat pad with thermal grease on this laptop and it had a significant impact. Though I don't know if I really trust myself to go messing around with the heat sink. 

Anyway, thanks again, and if you think of anything else please let me know

---

### Post by XRayA4T on 2008-04-03
My Inspiron 6000 used to run very hot until I undervolted it : [https://wiki.ubuntu.com/UndervoltingHowto](https://wiki.ubuntu.com/UndervoltingHowto)

Undervolting is just dropping the voltage the CPU runs at as the defaults tend to be higher than needed to run the CPU with no errors, drop iot too much and it starts to have calculation errors. It does not affect the processing speed in any way and the extra voltage is just converted to heat. At the default setting at 1.8GHz it runs at 1.39v but I can drop that to 0.97v. When idling at 800MHz I can run at 0.7v instead of 1.1v. I can now run most of the time with the fans off and the temperature slowly rises to 50 deg whan the fan comes on and drops to 35-40 deg. I used to hit over 80 deg at 100% CPU but now I hardly go over 60 deg.

---

### Post by viciouslime on 2008-04-03
XRayA4T's idea might be worth a try. As for replacing the thermal pad, in my experience that does make a massive difference in almost every case. Thermal pads, in comparison to thermal paste/grease seem to be pretty rubbish.

Even just stripping it down until you can get to the heat sink and removing any built up dust could well make a difference. I have a nvidia 7800GT in my main desktop machine that was idling around 60deg, this was fine, but the fan was a bit noisy, so i decided to remove the heatsink clean it all up and reattach, just to try and make it  little bit quieter. When i took the heatsink off I was pleasently surprised to find that they had already used thermal paste on the main GPU so I didn't need to change that, but there were some other chips that the heatsink also covered that only had thermal pads, I was going to change those when I realised i've left my thermal paste at Uni, so instead I just removed all the dust that had somehow got under the heatsink, and the masses of dust from inside the heatsink and fan and now it idles 27degrees cooler!

---

### Post by Kiri on 2008-04-03
Thanks XRayA4T for the advice. I looked at the link, but the information seemed outdated and for pentium M class processors... I will try to research more for my case, because to be honest I did not really understand how to do it properly :-k

viciouslime: You mean that I should maybe try to remove the thermal pad and put thermal grease on? I have never done this... Is it difficult?

---

### Post by Kiri on 2008-04-03
And as for dust, yes I agree, for such a small thing it can make a big difference. 

So anyway, I decided to open my laptop and blow some air around inside. 

I have done this with a desktop before, but I was not really prepared for how it would be opening a laptop. Needless to say it was quite complex and detailed!


But finally I reached the fan, and after removing it, I found a big chunk of dust (see pic).
So I got rid of it, managed to put everything back without leaving anything out ;-)
And started up with no errors. 

Now in ubuntu, the temperature is maybe 5-10 degrees cooler. Not a huge change, but an improvement. But the big change is when the fans kick in.
Before the fan seemed quite ineffectual, but now when it kicks in, it actually pulls the temp below 50 on the CPUs and even the GPU is down to 50. Once it gets down, the fans turn off and the temp rises up to 60ish again, and the fans kick in. So basically the heat is still bad, but now the fans actually work.

I do notice a huge difference in the physical temperature though. Under the laptop is only slightly warm now, instead of very hot. And the air blowing out from the fan is almost cool.

Amazing what those little dusts can do!


I would still like to do something about the heat sink (putting on the thermal grease?) so that the fans do not have to come on all the time.But at least for now, I don't have to worry too much about my computer burning.

---

### Post by viciouslime on 2008-04-03
That's great news! You really went to town on taking the thing apart too! Just a little advice for the future, putting a vacuum cleaner on the vents (while the computer is turned off) will usually remove most dust without having to take it apart, however, looking at those pics I'm not sure that would've helped much and since you want to change the pad for thermal paste you now know what taking it apart is going to involve.

As for how best to do this, it should be fairly easy. The hardest part, especially in laptops, is removing the heatsink from the chip, there are a million possible different designs and whilst most are simple enough, sometimes in laptops it can be very hard to reach the right screw/catch to get the thing off. Once you have however, it is important to get rid of ALL of the thermal pad, else the heatsink won't sit in an optimal position once the paste is applied.

The best way to get rid of it, in my experience, is to use nail varnish remover. It is safe to apply this both to the heatsink AND to the die of the CPU. That's to say I have done so many times in the past and had no problem what-so-ever. Soak a piece of cloth/cotton-wool/something of that nature, you should probably use a lint-free cloth ideally, in the nail varnish remover, then rub on the thermal pad until it has completely dissolved.

Then apply a little thermal paste. Do so directly to the die if possible, you should be able to see where abouts on the die the actuall processor is, or if it has a metal casing, there will usually be a mark on the casing somewhere indicating exactly where the circuit is. Apply the paste to that point, just a small dab, then reattach the heatsink and see how the temps are.

---

### Post by Kiri on 2008-04-04
Well I found this:
[http://support2.jp.dell.com/docs/systems/xpsM1210/en/SM/coolass.htm#wp1000001]("http://support2.jp.dell.com/docs/systems/xpsM1210/en/SM/coolass.htm#wp1000001")

Which seems to show the cooling is all part of one big copper rod. lol

In this case should I apply the paste to the underside of that copper thing (where the pads are now), or directly to the processor that it comes in contact with?

thanks

---

### Post by viciouslime on 2008-04-04
Basically wherever there are/were pads, you'll want to put some paste, I was trying to explain that on the processor itself, you'll want to put the paste in a small dab on the part of the processor where the circuit actually is.

I've attached two images with these points marked so it's maybe a bit clearer what I mean.

For some type of processor however, it is impossible to know this and for these you'll just want to put a very thin spread of paste over the whole thing.

---

### Post by Kiri on 2008-04-04
Thanks vicious. I'll try and get some of the paste and have a go at applying it when I have some free time. Thanks again! :)

---

### Post by peteguhl on 2008-06-17
Are you sure the fan even turns on?  On my e1505 i8k would turn it on, but dellfand works *much* better - not sure if it'll work on yours, but is worth a shot

---

