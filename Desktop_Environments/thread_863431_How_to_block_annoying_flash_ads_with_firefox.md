---
title: "How to block annoying flash ads with firefox"
date: 2008-07-18
forum: Desktop Environments
---

### Post by mohtasham1983 on 2008-07-18
Hi,

I have been having serious problems with firefox 3 and flash contents. I have installed opera to watch videos on youtube, since after watching a video firefox crashes. I even tried to install flash 10, with no luck.

As I mentioned I use opera for watching videos on youtube, but sometimes when I go to websites like digg.com that use flash ads, the page load gets very slow and sometimes causes firefox to crash. I tried to install ad block add ons for firefox, but I dont know how to block flash ads from. whenever I try to block them it just blocks viewing images from some third party websites. Next time I visit digg.com their ad is change. 

Is there any way that I can block the div element of the digg.com page that contains that flash ad?

Thanks

---

### Post by mcduck on 2008-07-18
Sure. Try the Adblock+ or Flashblock extension.

Adblock does complete blocking of all advertisements (if  you use some filter list). And even without any filter list you can use it to block any advertisemetns and flash banners you want.

Flashblock disables all flash movies from loading by default, putting a placeholder in their place instead. So all flash content is only loaded if (or when) you choose to load it by clicking the placeholder.

edit: links:
[https://addons.mozilla.org/en-US/firefox/addon/1865]("https://addons.mozilla.org/en-US/firefox/addon/1865")
[https://addons.mozilla.org/en-US/firefox/addon/433]("https://addons.mozilla.org/en-US/firefox/addon/433")

edit2: I just realised that you have already tried Adblock. Im not sure what's the difference between adblock and adblock+, but at least adblock+ shows a "tag" on all flash movies, you can just click that to block the movie. The tag can be enabled and disabled from adblock+'s settings.

---

### Post by mohtasham1983 on 2008-07-18
> **mcduck said:**
> Sure. Try the Adblock+ or Flashblock extension.



Thanks, flashblock was awesome. Now I can browse the web faster.

---

### Post by ilrudie on 2008-07-18
Looks like your problem is solved but I like noscript.  Might be worth looking into as well.  It blocks javascript and flash and now tries to detect and prevent some XSS attacks.

---

### Post by mohtasham1983 on 2008-07-18
> **ilrudie said:**
> Looks like your problem is solved but I like noscript.  Might be worth looking into as well.  It blocks javascript and flash and now tries to detect and prevent some XSS attacks.

I may not like flash, but I really like Javascript. I don't mind having it enabled for all websites. I will have a look at noscript to see how it can improve my web surfing performance. 

Thanks

---

### Post by ilrudie on 2008-07-18
It might not be for everyone.  It blocks a lot of pop javascript ads.  You can whitelist and blacklist domains as well as just set it up so you click and the single bit of flash or javascript you the script you clicked on runs.  Its certainly worth the investigation.

---

### Post by spupy on 2008-07-18
The advantage of FlashBlock is that you don't need to reload the whole page.
There is some kind of bug with FlashBlock and Firefox 3. I am experiencing it here on Gentoo, if I remember I had it in ubuntu, too:
When you want to watch youtube videos and click the flashblock "block" to see the youtube player, the video sometimes wont appear. You need to refresh the page and click the unblock arrow very quickly. :|

---

