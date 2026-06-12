---
title: "Website Viewing - Same Browser, OS &amp; Version, different results"
date: 2009-02-03
forum: General Help
---

### Post by JFire on 2009-02-03
Hello,
I realise that this is probably not the best place to post this, but I'm at a loss. Any suggestions you have would definately help.

I have two laptops:
 - Toshiba Satellite J40 (Work)
 - HP Compaq nx7100 (Home)

Both are running the same version of Ubuntu (Intrepid) and same browser versions (Opera 9.62 & Firefox 3.0.5). The only things that differ are the actual hardware and different network environments.

Here's the problem:
I made some changes to my website layout and themes but the pages only display correctly on my home laptop. Not on my work laptop. The laptop at work shows the pages as they were before the change, and I am at a loss as to why.

_Logically eliminating the sources of the problem:_

 **Browers** - I don't think it's the browsers, because both Opera and Firefox work fine at home, but show exactly the same differences at work.

 **Cache** - At first this seemed like it was the problem, but having checked the source code of the pages fetched from work, I have verified that they are up to date. So its not a problem with the Network Cache or the Webserver-side cache.

**Old Hardware** - It might be that my work computer's hardware just doesn't play well with the website changes, but that's a long shot because .. it's hardware ... and I haven't noticed any differences (apart from resolution) with any other website. I have no problem playing with Compiz on the work laptop, so my reasoning is that the hardware should definately be able to handle simple webpage rendering. 

 **Ubuntu?** - This is the main reason why I'm posting here. Does anyone know if there is any random setting in Ubuntu that might cause this problem? Maybe something I need to install or uninstall? I have no clue where or what it might be or where to start looking.

My diagnosis points to the problem being either Hardware related or Ubuntu related. In both cases I don't know how to continue. I'm seriously stumped. Any help is truly appreciated. 

~ J

---

### Post by dcstar on 2009-02-03
> **JFire said:**
> Hello,
I realise that this is probably not the best place to post this, but I'm at a loss. Any suggestions you have would definately help.

I have two laptops:
 - Toshiba Satellite J40 (Work)
 - HP Compaq nx7100 (Home)

Both are running the same version of Ubuntu (Intrepid) and same browser versions (Opera 9.62 & Firefox 3.0.5). The only things that differ are the actual hardware and different network environments.

Here's the problem:
I made some changes to my website layout and themes but the pages only display correctly on my home laptop. Not on my work laptop. The laptop at work shows the pages as they were before the change, and I am at a loss as to why.

_Logically eliminating the sources of the problem:_

 **Browers** - I don't think it's the browsers, because both Opera and Firefox work fine at home, but show exactly the same differences at work.

 **Cache** - At first this seemed like it was the problem, but having checked the source code of the pages fetched from work, I have verified that they are up to date. So its not a problem with the Network Cache or the Webserver-side cache.
.........
My diagnosis points to the problem being either Hardware related or Ubuntu related. In both cases I don't know how to continue. I'm seriously stumped. Any help is truly appreciated. 


Possible answer: Your work network uses a transparent proxy.

---

### Post by Xamiga on 2009-02-03
'having checked the source code of the pages fetched from work, I have verified that they are up to date'

Are you saying that the page source/content is identical but the display is different?

---

### Post by caro on 2009-02-03
> **Xamiga said:**
> 'having checked the source code of the pages fetched from work, I have verified that they are up to date'

Are you saying that the page source/content is identical but the display is different?

That was my question too because it seems like the most likely problem is the cache on the computer browser.  

Another option, and I've done this :redface: is that I hadn't published the website and was looking at the updated version as a local file on the computer.  It doesn't sound like this is the problem though.

---

### Post by Xamiga on 2009-02-03
Can you post the URL?

---

### Post by JFire on 2009-02-04
**dcstar:** Thanks, but I don't understand how a transparent proxy can be the cause of my problem.

**Xamiga and caro:** Yep, exactly the same page is fetched. I even saved the source code as a html file and opened it on both computers locally, the results are the same. Attached are screenshots - the resolution at work is (800x600) and (1680x1050) from home.

The page I've been testing on can be found here: 
[http://ajet.net/modules/articles/article.php?id=12](http://ajet.net/modules/articles/article.php?id=12)

Its looking more and more like a rendering issue caused by Ubuntu and the Laptop Hardware not getting along, although I haven't ruled out the network-cache at work still. It can't be the computer browser cache because I cleared those and tested different pages with two different browsers.

I'll try to eliminate the network-cache possibility by bypassing the network through SSH, and bounce the traffic through my home laptop.

In the meantime... I'm still clueless.

~ J

---

### Post by Xamiga on 2009-02-04
Your 'fromhome.png' I can't tell what browser your using, the second 'fromwork.png' is OPERA!  Are you trying to compare Firefox output and Opera output?  I can't see 'differences' from your pics.  Could you post images of the complete browser windows, with both browsers set to the same size and default font?

---

### Post by redilyn on 2009-02-04
I would definitly try bypassing any proxies using ssh before looking into this further.

---

### Post by JFire on 2009-03-09
It was the work proxies/network cache that was the problem. Thanks everyone for your help.

---

