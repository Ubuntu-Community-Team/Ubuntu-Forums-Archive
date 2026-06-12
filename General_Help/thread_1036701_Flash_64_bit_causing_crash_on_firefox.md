---
title: "Flash 64 bit causing crash on firefox"
date: 2009-01-11
forum: General Help
---

### Post by SpinningAround on 2009-01-11
I downloaded flash player for linux 64 bit from here [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

When I visit this site [http://newsmill.se/artikel/2009/01/09/bloggarna-kan-aldrig-ersatta-en-riktig-varldsreporter](http://newsmill.se/artikel/2009/01/09/bloggarna-kan-aldrig-ersatta-en-riktig-varldsreporter) and activate flash (using NoScript) will firefox crash, this is the only site so far that is causing firefox to crash so far since I started using flash 64 bit.

I guess that firefox isn't the problem but flash so how should I try to research why firefox crash?

---

### Post by mikewhatever on 2009-01-11
You probably shouldn't. I here flash 64 is still an alpha, so problems are expected. Reporting the problem to Adobe devs is the best you can do.

---

### Post by victoro on 2009-01-19
> **SpinningAround said:**
> I downloaded flash player for linux 64 bit from here [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

When I visit this site [http://newsmill.se/artikel/2009/01/09/bloggarna-kan-aldrig-ersatta-en-riktig-varldsreporter](http://newsmill.se/artikel/2009/01/09/bloggarna-kan-aldrig-ersatta-en-riktig-varldsreporter) and activate flash (using NoScript) will firefox crash, this is the only site so far that is causing firefox to crash so far since I started using flash 64 bit.

I guess that firefox isn't the problem but flash so how should I try to research why firefox crash?


I experienced the same issues with some websites like Yahoo email. I was able to get around the problem by installing the flashblock plugin. Now I can have Yahoo email open and enable any flash movie from YouTube manually when ever I want without crashing firefox.

---

### Post by hyper_ch on 2009-01-19
I haven't had any issues with flash 64 bit this far. I've been using it now for over a month. It's weird it doesn't work for you :(

---

### Post by ju2wheels on 2009-01-19
I just visited that link and have no problems, Im running the 64bit flash w/ FF 3.0.5.

Are you sure you properly uninstalled flash from synaptic as well as the nspluginwrapper before manually installing the 64bit plugin?

---

### Post by Cope57 on 2009-01-19
Me: Hey Doc, it hurts when I do this...

Doc: Then don't do that...

---

### Post by Shii on 2009-01-31
I'm having the same problem, Firefox segfaults when I go to Google Video, but not to YouTube.

---

### Post by ju2wheels on 2009-01-31
Just out of curiousity... what version does your 64bit flash plugin list when you visit about:plugins in Firefox?

Mines currently says Shockwave Flash 10.0 d21. I know there were at least two releases of the alpha 64bit flash plugin so far. If your version isnt that one you may want to consider getting the new one.

---

### Post by Shii on 2009-01-31
> **ju2wheels said:**
> Just out of curiousity... what version does your 64bit flash plugin list when you visit about:plugins in Firefox?

Mines currently says Shockwave Flash 10.0 d21. I know there were at least two releases of the alpha 64bit flash plugin so far. If your version isnt that one you may want to consider getting the new one.

Mine says Shockwave Flash 10.0 d21.

What makes this uniquely irritating is that this bug only appeared after I installed the most recent system updates... and I only discovered it when I invited a friend to watch a movie with me.

---

### Post by DeMus on 2009-01-31
> **ju2wheels said:**
> Just out of curiousity... what version does your 64bit flash plugin list when you visit about:plugins in Firefox?

Mines currently says Shockwave Flash 10.0 d21. I know there were at least two releases of the alpha 64bit flash plugin so far. If your version isnt that one you may want to consider getting the new one.

My version of Shockwave Flash is 10.0 r15 so it must a whole lot newer than yours.
I got it from:

[http://www.howtoforge.com/installing-adobe-flash-10-on-a-64bit-ubuntu-8.04]()

which has a nice explanation on how to install it.
Until now it just works, no problems whatsoever.

---

### Post by ju2wheels on 2009-01-31
[Removed Line see edit below]

Also, my version is definitely the latest one, unless they put out a new one this week which I doubt based on looking at the link below, because I updated it last week. I dont know what version you have but its possible you still have the 32 bit plugin in there and thats whats getting loaded by nspluginwrapper.

The latest 64bit plugin: [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz) 

The page where that plugin is: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Ive gotten both versions (10.0.d20 and 10.0.d21) from there and never had any problems.

Edit: The script on that website *does not* install 64bit flash although it claims to. I just checked what it downloaded and its actually the 32bit Flash, which explains why the script needed to add nspluginwrapper back in. You can prove this for yourself by opening the script and seeing that it downloads this file: [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz) which you download from this page: [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) and is the 32bit flash download for Linux.

Case and point, check any scripts you run on your computer and understand what they are doing or dont use them.

---

