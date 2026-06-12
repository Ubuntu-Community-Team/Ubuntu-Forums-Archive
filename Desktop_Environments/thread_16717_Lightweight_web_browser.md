---
title: "Lightweight web browser?"
date: 2005-02-23
forum: Desktop Environments
---

### Post by Biffy on 2005-02-23
Im on a slow machine. It's an AMD-K6 350 mhz with 192mb ram. I am looking for a lightweight web browser. 

Mozilla, firefox and konqueror is slow. Very slow even. I've tried Dillo and links2. They are very fast but they seem to have problems showing pages the way they are suppose to look.

So, im looking for a lightweight web browser that is capable of showing pages right. Im not saying everything should be perfect but the pages can't look like a warzone either.

Im using Epiphany now, and it seems to run slightly better then mozilla, firefox and konqueror.

---

### Post by wulf on 2005-02-23
Erm... use lynx and visit sites that are designed to degrade gracefully? That's probably not very useful advice. However, I've just installed Ubuntu on my old desktop machine so I'll have to compare Firefox performance on that (AMD K-6 400, 192MB RAM) with the laptop that has been Ubuntu'd since December (er.... Celeron 2.6GHz and 220MB RAM after the video driver has taken it's slice).

Wulf

---

### Post by Daniel G. Taylor on 2005-02-23
I was going to recommend Epiphany, but you are already using it.

I know Rodney Dawes has been hacking on [Encompass](http://encompass.sourceforge.net) recently, but it's not nearly ready for general use yet. It would be better for you, because it uses the lighter GtkHTML renderer instead of Mozilla's Gecko.

KHTML is also lighter than Gecko. I wonder if there are any lightweight KHTML-based browsers out there (I'm not a KDE guy, sorry!)...

[Edit] Also, you might want to use XFCE instead of GNOME or KDE. I actually like Fluxbox for slower machines, too. The less memory your desktop environment / window manager take, the more you'll have for other apps like your browser.

---

### Post by wulf on 2005-02-23
I've done some experiments - my 400MHz system (Firefox 0.9.3 on XFCE4.2) is marginally slower at rendering pages than my 2.6GHz laptop (Firefox 1.0 on Gnome 2.8). There's not a lot in it though - the older system is still very usable.

Out of interest, what's your frame of reference for "fast" and "slow"?

Wulf

---

### Post by Biffy on 2005-02-24
[QUOTE=wulf]Out of interest, what's your frame of reference for "fast" and "slow"?

Wulf[/QUOTE]

1. How long time the browser takes to start. For example, Dillo starts in one second, while firefox takes like 10.

2. This one is hard to explain, but when scrolling sites, how fast the site is being "rendered". For example take this site. It is slow to scroll up and down in this forum in firefox, when it works very good in Dillo. Shame that most pages i like to visit is unusable in Dillo. Same in Links2.

But as i said, Epiphany works slightly better then firefox.

---

### Post by barbarian on 2005-02-24
Opera?

btw, there was some interesting thred..
[http://www.howtocreate.co.uk/browserSpeed.html#testresults](http://www.howtocreate.co.uk/browserSpeed.html#testresults)

---

### Post by Biffy on 2005-02-24
[QUOTE=barbarian]Opera?

btw, there was some interesting thred..
[http://www.howtocreate.co.uk/browserSpeed.html#testresults](http://www.howtocreate.co.uk/browserSpeed.html#testresults)[/QUOTE]

Thank you! Opera feels way faster. :D

---

### Post by wulf on 2005-02-24
Interesting. On my systems, Firefox isn't really much slower on the older system and is quite usable on both (although, to be fair, I haven't used it for extended surfing and I didn't have any other programs running when I tested it). I'm sure those extra 50MHz I've got can't be that significant. Hmmnn...

Wulf

---

### Post by barbarian on 2005-02-24
>Firefox isn't really much slower on the older system

Maybe you've made significant tunning:-]

---

### Post by Biffy on 2005-02-24
[QUOTE=wulf]Interesting. On my systems, Firefox isn't really much slower on the older system and is quite usable on both (although, to be fair, I haven't used it for extended surfing and I didn't have any other programs running when I tested it). I'm sure those extra 50MHz I've got can't be that significant. Hmmnn...

Wulf[/QUOTE]

That's weird. Maybe you have more RAM? Firefox was slow in Slackware too. Well, Opera feels much better. Do i have to pay for Opera after a period of time? Cause that would suck.

---

### Post by az on 2005-02-24
"Do i have to pay for Opera after a period of time? Cause that would suck"

It is proprietairy.  Regardless of whether you have to pay, it is not open source, free software.  Say bye bye to your privacy.


You can disable smooth scrolling in firefox ad gain a lot of performance.  I have also found packages for mozilla-1.4 as well as galeon compiled with gtk1.2.  You lose some functionality (copy and paste and so forth) and the fonts are not antialiased, but galeon under gtk1.2 is quite fast.

---

### Post by barbarian on 2005-02-24
**IMHO**: If some product has better quallity then another product, why not. I don't care if it's proprietarity or not. 

Examples:
Skype
Photoshop
Mstcorefonts

---

### Post by wulf on 2005-02-24
[QUOTE=Biffy]That's weird. Maybe you have more RAM?[/QUOTE]
192MB... although that's running it under XFCE and with nothing else running. How about posting one or two pages where they take a consistently long time to render? That would allow for some comparisons.

Wulf

---

### Post by WW on 2005-02-24
[QUOTE=azz]Regardless of whether you have to pay, it is not open source, free software.  Say bye bye to your privacy.[/QUOTE]azz, I'm very curious about what that means.  Could you elaborate?

---

### Post by landotter on 2005-02-24
[QUOTE=Biffy]Im on a slow machine. It's an AMD-K6 350 mhz with 192mb ram. I am looking for a lightweight web browser. 

Mozilla, firefox and konqueror is slow. Very slow even. I've tried Dillo and links2. They are very fast but they seem to have problems showing pages the way they are suppose to look.

So, im looking for a lightweight web browser that is capable of showing pages right. Im not saying everything should be perfect but the pages can't look like a warzone either.

Im using Epiphany now, and it seems to run slightly better then mozilla, firefox and konqueror.[/QUOTE]
 I just installed Ubuntu to an identical system: 300mhz K6/192mb.

Firefox crashed and died--and I didn't have time to mess with it.

Mozilla surfed like a champ with one small tweaK:

reduce the "cache" settings under advanced settings to something reasonable like 5 or 10 mb instead of 50.

Gnome ran just fine on this box too, we just didn't load up a bunch of applets--they tend to be a bit hungry. :P

---

### Post by az on 2005-02-24
[QUOTE=WW]azz, I'm very curious about what that means.  Could you elaborate?[/QUOTE]

It is not open source.  It is proprietairy.  Unless the source code is available, how do you know that it is not spyware?

It comes down to your beliefs.  If you do not care about your privacy and your rights to know what a program is doing, then you shall be happy.  If you chose to only use open source apps, then you chose to do without some functionality.

Although the gap is getting smaller all the time, you still need to be careful.  In many ways, you cannot "have it both ways" and get the advantages of free-open software while running proprietairy apps.

The danger is that once people are happy with one solution - let's say any free desktop operating system that is competing with microsoft, they stop caring about freedom and would continue to use it even if it becomes proprietairy (the company stops distributing their software under a free licence)

This would just be a vicious circle where free and open software is just a transition phase - a marketing tool to beat the competition.  This would be a waste.






Hey, man.  You asked.

---

### Post by barbarian on 2005-02-24
>Unless the source code is available, how do you know that it is not spyware?

It's a right way of thinking.
I just wanted to say, that some linux apps not always so good for desktop then proprietary competitors. I also hope that situation will changed:-]

---

### Post by WW on 2005-02-24
azz, thanks for the response.  I was just wondering whether your comment about privacy was based on an actual instance of spyware being discovered in Opera.

---

### Post by kelean on 2005-02-24
[QUOTE=Biffy]That's weird. Maybe you have more RAM? Firefox was slow in Slackware too. Well, Opera feels much better. Do i have to pay for Opera after a period of time? Cause that would suck.[/QUOTE]
 Im using firefox on a P-3 450 machine and it is faster than the ones you stated.  I have not used opera with linux but it worked very well with windows.  As far as paying for opera its free for 2 weeks then you get banner adds or you have to pay.

---

### Post by Quest-Master on 2005-02-24
> Unless the source code is available, how do you know that it is not spyware?

Though I must agree and like open-source more than proprietary, who really sifts through all of the source code in a GPL-ed program to make sure there is no spyware in it?

As said before, I prefer open source applications anyday, but when it comes done to it, I will use anything that does the job best (of course, without spyware/viruses).

---

### Post by Biffy on 2005-02-24
[QUOTE=landotter]I just installed Ubuntu to an identical system: 300mhz K6/192mb.

Firefox crashed and died--and I didn't have time to mess with it.

Mozilla surfed like a champ with one small tweaK:

reduce the "cache" settings under advanced settings to something reasonable like 5 or 10 mb instead of 50.

Gnome ran just fine on this box too, we just didn't load up a bunch of applets--they tend to be a bit hungry. :P[/QUOTE]

I shall try it, but the whole app is slow. If i click "edit", it takes like 2 seconds for the menu to show. That, plus the rendering is slow as i said before. This is both in Mozilla and Firefox. Epiphany seems to work slightly better. For example, this forum is slow. If i scroll up and down, the whole site "lags" and it's extremely disturbing. But hey, Opera works way better so im sticking to it. But i need to know (cause i didnt get my question answered so i understood) if i can use Opera for how long i want now or will it just stop functioning one day and say that it needs money to work? :)

I know that Opera is prop, but i agreed on seeing a banner on top of it.

---

### Post by landotter on 2005-02-24
[QUOTE=Biffy]I shall try it, but the whole app is slow. If i click "edit", it takes like 2 seconds for the menu to show. That, plus the rendering is slow as i said before. This is both in Mozilla and Firefox. Epiphany seems to work slightly better. For example, this forum is slow. If i scroll up and down, the whole site "lags" and it's extremely disturbing. But hey, Opera works way better so im sticking to it. But i need to know (cause i didnt get my question answered so i understood) if i can use Opera for how long i want now or will it just stop functioning one day and say that it needs money to work? :)

I know that Opera is prop, but i agreed on seeing a banner on top of it.[/QUOTE]
 Mozilla's still going to be a bit "slow" feeling even if you speed it up by reducing the cache--still worth a shot though. A lot of the UI lag can be your video card performance--are you certain that it's fully supported and you have the drivers/modules loaded?

I really like the newest Opera too--compared to previous versions it's really super stable and renders very nicely. You might even consider utilizing the built in mail/news/and IRC to save resources--those components aren't loaded into memory unless you're using them afaik. Disabling java can make for more efficient browsing--it's pretty rare to absolutely need it and also reduce your disc cache to something tiny like 5 megs as recommended for Mozilla/Firefox.

Yeah, Opera's proprietary and so's the strawberry jam in your fridge--LOL--Opera's a niche company selling a niche product, they aren't abusing a monopoly and you have other browsers to choose from. They're nice responsible Norwegians AND they make sure that the latest and greatest Opera is always available for a variety of platforms, including Linux. Good folks, so if you like the browser and have the cash--buy a license and support proprietary software done right. BTW, you can use Opera forever with the banner on top and a lot of folks do use a cracked version--Opera doesn't lock their software down too tight--seems they're confident that those who like it will pay.

I think XFCE + Opera would be an excellent modern, pretty, and speedy choice. :D

---

### Post by Davepet on 2005-02-25
>>who really sifts through all of the source code in a GPL-ed program to make sure there is no spyware in it?<<

You may not do it, but you can be sure that quite a few hackers *have* done the sifting & if there were spyware, it would be loudly called out online. Since many folks work on most open source projects, it'd be pretty tough to sneak some spyware in unnoticed.

Personally, I wouldn't get paranoid about Opera yet, but any program that serves ads is worth keeping an eye on, it's all too easy to use that to track you.

Dave

---

### Post by Biffy on 2005-02-25
Hehe, long post. Thanks for explaining! Nice to hear i can use Opera as long as i want with that banner.

About my graphic card, it's a "S3 Virge" (never heard of it before, got the card from my school) and i think it got 2mb 's of memory. It was auto-detected by Ubuntu and the name "S3 Virge" is in xorg so i guess the right driver is loaded.

---

### Post by wulf on 2005-02-25
[QUOTE=Biffy]About my graphic card, it's a "S3 Virge" (never heard of it before, got the card from my school) and i think it got 2mb 's of memory. It was auto-detected by Ubuntu and the name "S3 Virge" is in xorg so i guess the right driver is loaded.[/QUOTE]
Xorg? Are you using Hoary? All my machines (the two mentioned above plus the one at work) are running Warty and using XFree86. I've not used Xorg, so all bets are off!

Wulf

---

### Post by Biffy on 2005-02-25
But would that have an effect on how fast mozilla render pages? Well, maybe you are right.

---

### Post by wulf on 2005-02-25
[QUOTE=Biffy]But would that have an effect on how fast mozilla render pages? Well, maybe you are right.[/QUOTE]
I don't know but you're getting significantly different results from what I'm experiencing with a similarly old machine and a large part of the work is rendering the page onscreen. The video system used *may* be having an impact. Any comments from other users of Firefox on Xorg?

Wulf

---

### Post by Daniel G. Taylor on 2005-02-25
I don't have a slow machine but I would say it has more to do with the drivers you are using than with the X11 implementation (i.e. it may not matter if you use XFree86 or Xorg, if one of you is using accelerated drivers and the other isn't there can be a huge impact).

That said, I get scrolling issues every now and then with Xorg + Compositing (garbage in the Firefox window). A bit off topic but I thought I'd mention it.

---

