---
title: "Best Graphics card for $100"
date: 2011-04-14
forum: Gaming &amp; Leisure
---

### Post by catlover2 on 2011-04-14
Hello, 

Recently i completed my first computer build and of course put Ubuntu on it, 
but it is obvious that the intergrated graphics that came with the mobo are not enough.

Currently I am looking at:
Radeon HD 5750:[http://www.newegg.com/Product/Product.aspx?Item=N82E16814102865&cm_re=5750-_-14-102-865-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16814102865&cm_re=5750-_-14-102-865-_-Product)
GeForce GTS 450:[http://www.newegg.com/Product/Product.aspx?Item=N82E16814162062&cm_re=GeForce_GTS_450-_-14-162-062-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16814162062&cm_re=GeForce_GTS_450-_-14-162-062-_-Product)
and this: [Newegg.com - Newegg Eggs Model# 3gg0v3r3a5y - Newegg Gear:lolflag:]("http://www.newegg.com/Product/Product.aspx?Item=00-000-033&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Keywords=%28keywords%29&Page=1#scrollFullInfo")
So, basically I'm looking for the most powerful GPU for about $100 that is compatible with Ubuntu of course!

Thanks, Catlover

---

### Post by DonjQuix on 2011-04-14
Hey there. I just wanted to say that I have only had Ubuntu installed for maybe six hours, but my card was compatible when I downloaded the drivers. So as far as I could tell you, the 450 is pretty compatible.
Hope this helps!

---

### Post by catlover2 on 2011-04-14
Thanks for the info, as I had seen some compatibility questions with the 450.

---

### Post by papibe on 2011-04-14
The nvidia driver has much better support than ATI in Linux. I would recommend getting an nvidia card (although I don't have any relevant info on the 450).

Regards.

---

### Post by Irritant on 2011-04-14
I can vouch for the Nvidia GTS 450 - that is a damn fine card.

---

### Post by HolgerB on 2011-04-15
I would vote for an NVidia card also.
May be in a few month this will change but currently both NVidia and ATI open source drivers are not very performant. They also lack certain OpenGL / GS features.

Note: I am no NVidia fan boy. It's just that NVidia always worked better for me with better support for older / legacy cards (even my GeForce 4400 Ti is still supported) and NVidia has a better reputation both for Linux native games as well as for WINE.

I run an ATI HD4670 under Ubuntu as well as an GeForce 9800GT. If you are on budget you can try to get a cheap "old" Geforce at the bay. I grabbed mine for 40&#8364; and it runs all recent games up to 1080p fine.

---

### Post by mips on 2011-04-15
NVidia has better drivers than AMD.

---

### Post by HolgerB on 2011-04-15
> **mips said:**
> NVidia has better drivers than AMD.
Not to sound too offensive but on what facts is this statement based ?

---

### Post by Perfect Storm on 2011-04-15
> **HolgerB said:**
> Not to sound too offensive but on what facts is this statement based ?

On performace, features, ease of use contra games and Nvidia supports must of their cards for Linux.
(we're talking of official (restricted) drivers here).

---

### Post by cascade9 on 2011-04-15
Sod the GTS450, you can get a GTX460 for not much more- 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130600](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130600)

If you arent gaming, GTS450 or GTX460 is pointless. Save some cash, get a GT220 or GT430.  Or an AMD/ATI card. 

nVidia used to be 'the best' for linux, but that is changing rapidly. .....Optimus, no support at all. nVidia is footdragging on the GTX590, GTX 550 Ti, GT420, GT440, and GT520 card drivers. 

nVidia is getting under my skin with the way they are realsing multipule cards with the same (or very similar) name, but different features as well. 2 different versions of the GT430, GT440, GTS450 and 3 (yes, three!) different GTX460s. It was bad enough when nvidia was just releasing chips as different series cards (8800GT/GTS, 9800GT/GTX/GTX+, GTS250...).

IMO nVidia is in trouble. Not just in the linux world, though we are wearing the worst of it now, but also in windows world as well.     

Also, the ATI/AMD closed drivers are getting a lot better, nvidia isnt really...

As far as open source goes, ATI/AMD is clearly ahead.  

nVidia wont give out any of the technical specs that would help a lot with open source driver development, and have cut the old .nv driver (you want open source, you'll have to build the drivers yourself is the way nvidia is going). 

ATI/AMD have released spec sheets  on at least some cards, and have engineers actually working on the open source drivers.

---

### Post by mastablasta on 2011-04-15
Why do they mark different chips with same model? OK we do this as well but we are not selling computer hardware here...usualyl we do this because same model is sold in different markets and difference are maybe some special feature for certain market. but in GPU land they shouldn't do this. as users only have models to operate with. 
 
also as i know ATI is issuing new version of restricted drivers so they are in time for new release of Ubuntu.

---

### Post by mips on 2011-04-15
> **HolgerB said:**
> Not to sound too offensive but on what facts is this statement based ?

You only have to look at the forums & other sites to realise this.

---

### Post by mips on 2011-04-15
> **mastablasta said:**
> Why do they mark different chips with same model?

What do you mean by this? Examples?

---

### Post by cascade9 on 2011-04-16
> **mips said:**
> You only have to look at the forums & other sites to realise this.

You'll find that *EVERY* GPU/video chip has reported problems.  

ATI/AMD might still be slightly in front of nVidia for problems, but its not like there is any 'hard' data on that. 

From what I've seen of the 11.XX drivers they are far superiour to the 10.XX drives that most people are using (due to things like ubuntu not updating the drivers in the repos when newer drivers are released) So the reports are always a fair way behind what you can expect from the current drivers.  

Give it a few months to 2 years and then have a check again.  ;) 

> **mips said:**
> What do you mean by this? Examples?

The best example of this is the GT440. Theres a 'normal' GT440, and a GT440 'OEM'.  

Different chips, different core speeds, different shader/texture/render output units, different bus width, different RAM speeds and capacity. Totally different cards. 

GT440- GF108, 128bit, 810MHz core, 1620MHz shader (96 Unified Shaders, 16 Texture Mapping Units, 4 Render Outputs) 1800Mhz/3200Mhz RAM (GDDR3/GDDR5),  512/1024/2048MB RAM.  

GT440 'OEM'-  GF106, 192bit, 594MHz core, 1189MHz shader (144 Unified Shaders, 24 Texture Mapping Units, 24 Render Outputs) 1800Mhz RAM (GDDR3),  1536/3072MB RAM. 

Where things are less obvious is things like the GTX460 variants....same basic chip (GF104) with different core/shader/RAM speeds (SE and 'OEM' are 650MHz core, 1300MHz shader, 3400MHz RAM,  the 'normal' version is  675MHz core, 1350MHz shader, 3600MHz RAM). 

Even with the 'normal' GTX460s there  are differences- 768MB variants are 192bit bus width, 24 render output units, 1024/2048MB variants are 256bit bus width, 32 render output units). 

Then there is the different in shaders/render output units... GTX460 1024/2048MB and GTX460 OEM are 336 Unified Shaders, 56 Texture Mapping Units, 32 Render Outputs. GTX460 768MB is 336 Unified Shaders, 56 Texture Mapping Units, 24 Render Outputs. GTX460 SE is 288 Unified Shaders, 48 Texture Mapping Units, 32 Render Outputs. 

Its all down to different RAM amounts (192bit/256bit split) speeds (3600/3400 split) and different numbers of the internal 'cores' in the GPU being used or disabled.  

Right #%&@#$&^#$ mess. It would have been easier, and less confusing to have given the different variants of the GTX460 different model numbers.....

---

### Post by Irritant on 2011-04-16
Honestly what is the big deal about the different Nvidia cards?  To the end user, all it really means is price vs speed, so maybe it's actually good that there is a good variety to pick from.  They use the same driver and they support the same OpenGL/DirectX versions.

---

### Post by catlover2 on 2011-04-16
Hello, 

I don't really have much to say in this discussion, but from what i have gathered, it seems that nVidia might be a better buy then ATI at the moment.

I'm not ready to buy yet though, so i have plenty of time to change my mind. ;)

Catlover

---

### Post by Tweak42 on 2011-04-25
> **catlover2 said:**
> Hello, 

I don't really have much to say in this discussion, but from what i have gathered, it seems that nVidia might be a better buy then ATI at the moment.

I'm not ready to buy yet though, so i have plenty of time to change my mind. ;)

Catlover

There are pros and cons for both, whither you go AMD/ATI or Nvidia.  Really all you can do is search out whither the most crucial apps you want to run will work well (and hopefully continue to improve) on whichever chip at the time you plan to buy.  

[http://www.phoronix.com/](http://www.phoronix.com/) tends to be a good source of latest developments in the linux video hardware.  Just beware some fanatical posters on their forums can get snippy at times.

---

### Post by devguy on 2011-04-26
To be honest, I don't think you'll be able to beat the HD 5830 combo from Newegg right now (comes with a USB tv tuner you can either use or sell).  The catalyst drivers have been rock solid for me for quite some time, and perform excellent.  I get great video acceleration with VAAPI, and Eyefinity support as well.  Supports OpenGl 4.1 and runs the Unigine Heaven demo great (although the Evergreen series have weak tesselation compared to Fermi and Northern Island GPUs).

Go for nVidia if you have to have Adobe Flash GPU acceleration, which only works on the 32bit OS (and is buggy as hell).  Also, nVidia is much better at supporting newer kernel/Xorg versions before they're released (AMD usually waits until they're released to put out new drivers).  VDPAU is better supported than VAAPI right now, but it isn't a huge deal anymore (thank Intel more than AMD for that, IMHO).

[Here's]("http://www.phoronix.com/scan.php?page=article&item=sapphire_hd5830&num=1") how you can expect it to perform.

---

### Post by rajeev1204 on 2011-04-26
I have the 5750 card myself .It runs fine.Dont believe all the anti ATI comments , its mostly not true.Both cards though you mentioned are a royal waste of money on ubuntu if you want to run any games, cos there arent any that take advantage of these cards.Unless doom 4 releases next year on linux.

I hope you have windows too.

---

### Post by catlover2 on 2011-04-27
Hey, thanks for th ATI feedback, I was a bit suspicious about all this nVidia drivers are so much better then ATI/AMD on linux. And yes i do have Windows.

Catlover

---

### Post by baccilus on 2011-04-27
I have an ATI HD4670. It works great on ubuntu without any problem. If you plan on using the card for a long time, i recommend you go with ATI because the way things are looking, ATI drivers are improving with a furious pace.

---

### Post by rajeev1204 on 2011-04-27
Also like to add :


If you plan to use wine for playing games, nvidia seems to work a little better for some newer games which run on wine .

---

### Post by baccilus on 2011-04-27
> **rajeev1204 said:**
> Also like to add :


If you plan to use wine for playing games, nvidia seems to work a little better for some newer games which run on wine .

Well, I didn't know that. Wine sucks on my ATI HD4670. Could never even play TF2 with it.

---

### Post by rajeev1204 on 2011-04-27
> **baccilus said:**
> Well, I didn't know that. Wine sucks on my ATI HD4670. Could never even play TF2 with it.

TF2 receives so many updates that it frequently keeps breaking under wine.I have been trying for the last one year but performance is horrendous.It mostly freezes the machine in a few minutes.

Nvidia also aint any good for wine frankly.Wine itself is a poor way of playing games.If it runs then you are lucky.

I just use wine to run my old half life games.And frankly with the latest games i have no hope of them ever running under wine.

---

### Post by catlover2 on 2011-04-28
Really, I don't care about fiddling for (possibly) hours trying to get a game to work under wine, when i could just boot windows and forget about it.

---

### Post by PCLinuxGuy on 2011-06-21
at one point tigerdirect had the AMD Radeon HD 5670 for under $100 with a rebate. not bad for a 1GB of GDDR5.  not going to take sides of ati vs nvidia  I have found that both have worked great for me. the main thing is to look at the cards in your price range and then compare the spec sheet.

---

### Post by oldrocker99 on 2011-06-22
I bought a nVidia 520, which has 1 GB RAM and, while it is the lowest-end DX11 nVidia card, it's MUCH faster than the lowest-end ATI DX11 5450 card it replaced. Just remember that nVidia's proprietary drivers require a non-GUI console (with X not running) to install, and it's around $50 from NewEgg.

It does run just fine.

---

### Post by holastickboy on 2011-06-22
I actually have a radeon 5750, and it is great. Works with multiple monitors no problems, and I can play any game maxed out with no issues (and my monitor runs on a 2560x1440 res).  That being said, I would agree with the others in terms of driver support for Linux, Nvidia is just better at that.

If you dual boot, either will be fine.  I like the Radeon cards (im a fan of underdogs).  That being said, either way you go, they will both be good choices, and the gaming performance between them is barely noticeable (particularly in real life situations). If you can find a Radeon 5770, however, they will blast both cards away in terms of performance, and may only cost $10-$20 more depending where you get them.

---

### Post by R33D3M33R on 2011-06-23
GTS 450 has around 5-10% better performance in Windows games, but it's also more expensive on those links.

---

### Post by catlover2 on 2011-06-23
In case any one was wondering, I ended up getting an ATI Radeon 5670 from Newegg for ~$80, All works fine except Compiz...

---

### Post by holastickboy on 2011-06-23
> **catlover2 said:**
> In case any one was wondering, I ended up getting an ATI Radeon 5670 from Newegg for ~$80, All works fine except Compiz...
I have done a little bit of searching and found this link that shows you how to install the ATI catalyst drivers that might help you with Compiz (I hope anyways).

[http://www.ubuntuvibes.com/2011/04/quick-tip-how-to-enable-ati-catalyst.html](http://www.ubuntuvibes.com/2011/04/quick-tip-how-to-enable-ati-catalyst.html)

---

### Post by catlover2 on 2011-06-23
Hmmm, I'll try it out:roll: Kwin does almost everything compiz does anyhow...

---

### Post by ELD on 2011-06-23
I have the 5770 so two up from you basically with no compiz problems, what "problems"? Also what Ubuntu version are you using?
 
If you are on Ubuntu 10.10 you need the proprietary drivers. The open source drivers on 11.04 will run compiz.

---

### Post by catlover2 on 2011-06-23
11.04, I use the proprietary drivers, and the "problem(s)" are
1. CCSM will not respond to _any_changes I make whatsoever.
2. Compiz is quite choppy, and I can't change anything in CCSM to fix it.

---

### Post by catlover2 on 2011-06-23
OK, now disabling sync to vblank fixed the choppiness(an exception to CCSM not responding), but no window borders now...

---

### Post by mips on 2011-06-23
nVidia would have been a better option, good luck sorting your issues out.

---

### Post by R33D3M33R on 2011-06-24
You should try the drivers from the ATI website, the ones in the repository are older and may contain more bugs.

---

### Post by catlover2 on 2011-06-24
AWWW YEAH!

I really don't know if this is due to upgrading to the latest drivers, or my figuring a bit more about CCSM, or a combination of both, but it WORKS!!! :guitar:

---

### Post by catlover2 on 2011-06-24
Hey, it fixed my flash fullscreen issues too!

---

### Post by mips on 2011-06-24
Cool, glad you came right.

---

