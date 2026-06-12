---
title: "No pulldown arrows?"
date: 2012-09-10
forum: Forum Feedback &amp; Help
---

### Post by GeForce 9500GT on 2012-09-10
Hello everyone!  Just something i noticed: under Windows Explorer i see these arrows next to Search, Quick Links. But under Firefox i don't see them. Why is that?  screenshot FF: [http://img577.imageshack.us/img577/4306/selectie00110092012.png](http://img577.imageshack.us/img577/4306/selectie00110092012.png)

---

### Post by coldcritter64 on 2012-09-10
Just reproduced the symptom here, that is I made the down arrows disappear, by blocking scripting, in particular I blocked yahooapis.com.

If you are using script blocking or ad blocking allow yahooapis.com for the site and you should get them back. Cheers, coldcritter64.

---

### Post by GeForce 9500GT on 2012-09-11
> **coldcritter64 said:**
> Just reproduced the symptom here, that is I made the down arrows disappear, by blocking scripting, in particular I blocked yahooapis.com.
 
If you are using script blocking or ad blocking allow yahooapis.com for the site and you should get them back. Cheers, coldcritter64.
 
I'm not using any kind of script blocking under FF. The only thing i use is Adblock Plus. But i don't think that is causing the issue here, right?

---

### Post by zombifier25 on 2012-09-11
I can see them fine here, and I'm using a truckload of blocking-related addons. OP, you can try Shirt+F5-ing the page to clear the cache.

---

### Post by coldcritter64 on 2012-09-11
> **GeForce 9500GT said:**
> I'm not using any kind of script blocking under FF. The only thing i use is Adblock Plus. But i don't think that is causing the issue here, right?
Check all your adblock settings. I vaguely remember someone else here a long while back using it having trouble with the yahooapis scripting on this site. IIRC Adblock also uses script blocking as part of the blocking of ads. Hopefully someone using adblock can point you to the right settings for it to use here.

---

### Post by GeForce 9500GT on 2012-09-11
> **coldcritter64 said:**
> Check all your adblock settings. I vaguely remember someone else here a long while back using it having trouble with the yahooapis scripting on this site. IIRC Adblock also uses script blocking as part of the blocking of ads. Hopefully someone using adblock can point you to the right settings for it to use here.

 Tried everything, nothing helped. I kinda was hoping you could remember that topic.... Well, i'll search for it too.

---

### Post by GeForce 9500GT on 2012-09-15
Just did a fresh install of Lubuntu 12.04. Installed Firefox 15.0.1 and get the same.... no pulldown menu's. Whats going on?

---

### Post by GeForce 9500GT on 2012-09-17
*bump*

---

### Post by catlover2 on 2012-09-17
I'll just make the probably unhelpful comment that I'm not seeing any issues here. I have Adblock Plus and NoScript installed; if I block scripts from either yahooapis or ubuntuforums.org in NoScript, then the drop-down menus don't work.

---

### Post by Elfy on 2012-09-17
Try running firefox from a terminal in safe mode - do you get the arrows then?

```
firefox -safe-mode
```

---

### Post by vasa1 on 2012-09-17
> **GeForce 9500GT said:**
> I'm not using any kind of script blocking under FF. The only thing i use is Adblock Plus. But i don't think that is causing the issue here, right?
Could be! Disable Adblock Plus and try.

---

### Post by vasa1 on 2012-09-17
If it is indeed caused by Adblock Plus, you'll have to make an exception rule.

To do that, click on the dropdown arrow next to the ABP icon and then click on Open Blockable items.
You'll get a panel listing items that are blocked (red) or unblocked (green or black).
I have
[http://yui.yahooapis.com/2.9.0/build/connection/connection-min.js?v=387](http://yui.yahooapis.com/2.9.0/build/connection/connection-min.js?v=387)
and
[http://yui.yahooapis.com/2.9.0/build/yahoo-dom-event/yahoo-dom-event.js?v=387](http://yui.yahooapis.com/2.9.0/build/yahoo-dom-event/yahoo-dom-event.js?v=387)
as allowed or unblocked.

To allow any blocked item, double-click on it, and then choose exception rule (which will be the default when you double-click on a blocked item).


A simpler way is to just disable ABP on ubuntuforms.org!
But then you'll get that to see that irritating guitar player ;)

---

### Post by GeForce 9500GT on 2012-09-17
**_@ catlover2 & vasa1:_**
in [this post ]("http://ubuntuforums.org/showpost.php?p=12240726&postcount=7")i mentioned that i did a fresh/new install of Lubuntu. Maybe i wasn't really clear with what i ment, but i did a totally new and fresh install of Lubuntu. First i removed all partitions with the live-cd of Gparted and then i installed Lubuntu using a live-cd. After that i only removed Google Chromium (terrible browser IMHO) installed Firefox => no add-on's!! And still the button's for the pulldown menu aren't visible.
 
**_@ vasa1:_**
I'll check those 2 links. Maybe they help but looking at my comment above it has nothing to do with Adblock Plus or other add-on.
 
**_@ elfy:_**
I'lll try that and see if that makes any difference.

---

### Post by coffeecat on 2012-09-17
> **GeForce 9500GT said:**
> Just did a fresh install of Lubuntu 12.04. Installed Firefox 15.0.1 and get the same.... no pulldown menu's. Whats going on?

Out of interest, I've just installed Lubuntu 12.04 to a spare partition to see what I get, in case this was a Lubuntu quirk. See my screenshot of Firefox - the pulldowns are there for me.

This is a system freshly installed and not updated yet - only firefox 15.0.1 installed through Synaptic. I'll update the system and install my selection of firefox addons, which include Adblock+ and noscript, and see if any of that makes any difference.

Off-topic comment: I have to say that Lubuntu runs well on this quad-core 8GB RAM system! :)

---

### Post by vasa1 on 2012-09-17
Okay, if it's a totally clean install of Firefox, then AdBlock Plus isn't to blame and whatever I suggested related to that possibility.

---

### Post by coffeecat on 2012-09-17
> **coffeecat said:**
>  I'll update the system and install my selection of firefox addons, which include Adblock+ and noscript, and see if any of that makes any difference.

Lubuntu now fully updated, etc, and I can still see the dropdowns. Adblock+ with Easylist hasn't affected it and the only thing that makes the dropdowns disappear for me is as coldcritter64 mentioned, blocking yahooapis.com in noscript. @GeForce 9500GT, since you aren't using a script blocker, then that wonlt be relevant for you. The one thing I haven't tried is removing Chrome.

---

### Post by GeForce 9500GT on 2012-09-17
> **coffeecat said:**
> Out of interest, I've just installed Lubuntu 12.04 to a spare partition to see what I get, in case this was a Lubuntu quirk. See my screenshot of Firefox - the pulldowns are there for me.
:confused: This is weird.... Why don't have i the pulldowns??
 
> This is a system freshly installed and not updated yet - only firefox 15.0.1 installed through Synaptic. I'll update the system and install my selection of firefox addons, which include Adblock+ and noscript, and see if any of that makes any difference.
I did a fresh/new/clean install, just removed Chromium (Firefox will be installed as replacement), didn't add any add-on's to exclude them out. My system was updated with the latest updates. No pulldown's.... 
 
> Off-topic comment: I have to say that Lubuntu runs well on this quad-core 8GB RAM system! :)
[See my spec's in my signature]("http://ubuntuforums.org/member.php?u=1694960").

---

### Post by Elfy on 2012-09-17
so I assume that safe mode made no difference

---

### Post by GeForce 9500GT on 2012-09-17
> **Elfy said:**
> so I assume that safe mode made no difference
 
I didn't tried that yet. That will be done this evening. Remember the time difference between u and me ;)

---

### Post by Elfy on 2012-09-17
as far as I can tell you are constantly at home when online :D

---

### Post by GeForce 9500GT on 2012-09-17
> **Elfy said:**
> as far as I can tell you are constantly at home when online :D
 
So it seems :lolflag: 
 
Right now i'm not at home and working on a Windows computer. But i keep you guys updated about the safe-mode option.

---

### Post by vasa1 on 2012-09-17
> **coffeecat said:**
> Out of interest, I've just installed Lubuntu 12.04 ...
Off-topic comment: I have to say that Lubuntu runs well on this quad-core 8GB RAM system! :)
I just did a **sudo apt-get install --no-install-recommends lubuntu-desktop** and now have "Lubuntu" as a log-in option. All drop-down arrows present and functional in Firefox 1_6_. And this is just a dual-core 4GB RAM laptop.

OT edit: There's not just Lubuntu, but Lubuntu Notebook, and Openbox and Gnome Openbox ...

---

### Post by vasa1 on 2012-09-17
> **GeForce 9500GT said:**
> ...
 
**_@ vasa1:_**
I'll check those 2 links...
**They're not links for reading.** They're just the two yahooapis connections that my settings of Adblock Plus allow.

---

### Post by vasa1 on 2012-09-17
BTW, do you have a separate /home partition?

---

### Post by GeForce 9500GT on 2012-09-18
> **vasa1 said:**
> BTW, do you have a separate /home partition?

 No, i don't.

---

### Post by Elfy on 2012-09-18
> **GeForce 9500GT said:**
> No, i don't.

Something tugged at my memory, disabled javascript - no arrows.

Re-enabled it - arrows ...

Possibly affects your other issue as well.

---

### Post by GeForce 9500GT on 2012-09-18
> **Elfy said:**
> Something tugged at my memory, disabled javascript - no arrows.

Re-enabled it - arrows ...

Possibly affects your other issue as well.

Didn't helped. Even Chromium doesn't show the pulldown menu's

---

### Post by vasa1 on 2012-09-18
Try a totally new browser like Midori. It's a small download.

---

### Post by GeForce 9500GT on 2012-09-18
> **vasa1 said:**
> Try a totally new browser like Midori. It's a small download.

I'll try that too.  Just installed Xubuntu and guess what..... same issue with the pulldown menu's. I don't think it's a Lubuntu or Xubuntu issue, i start to believe now it's a Firefox 15.x issue.... Isn't this weird or what???

---

### Post by GeForce 9500GT on 2012-09-18
> **Elfy said:**
> so I assume that safe mode made no difference

Correct, no difference at all...

---

### Post by thatguruguy on 2012-09-18
> **GeForce 9500GT said:**
> I'll try that too.  Just installed Xubuntu and guess what..... same issue with the pulldown menu's. I don't think it's a Lubuntu or Xubuntu issue, i start to believe now it's a Firefox 15.x issue.... Isn't this weird or what???

How could it be a firefox issue when you stated [here]("http://ubuntuforums.org/showpost.php?p=12245736&postcount=27") that you don't have the pulldown menus in Chromium, either?

---

### Post by GeForce 9500GT on 2012-09-18
> **thatguruguy said:**
> How could it be a firefox issue when you stated [here]("http://ubuntuforums.org/showpost.php?p=12245736&postcount=27") that you don't have the pulldown menus in Chromium, either?

Yes, you're right about that. But now it's a Firefox/Chrome/Midori issue then... 3 web browsers showing the same problem, no pulldown menu....

---

### Post by GeForce 9500GT on 2012-09-18
The situation now:
 
Lubuntu (64-bit):
Firefox => no pulldown menu's
Chrome => no pulldown menu's
 
Xubuntu (64-bit)
Firefox => no pulldown menu's
Chrome => no pulldown menu's
Midori => no pulldown menu's
 
**edit**
** 18 sep 2012 @ 18:29 **
Just installed Ubuntu 12.04.1 64bit and guess what....... Yep..... no pulldown menu's.
Am i the only one suffering from this????
 
***edit***
** 18 sep 2012 @ 18:56 **
Keep Ubuntu 12.04 for now but with the Cinnamon desktop environment since this desktop environment suits my needs the best even i ditched Lubuntu for some curious drawbacks.

---

### Post by catlover2 on 2012-09-19
Are scripts working on other sites? (Newegg.com has a lot of scripts, to name one) How about other vBulletin forums? (if you happen to be registered with one)

---

### Post by GeForce 9500GT on 2012-09-19
> **catlover2 said:**
> Are scripts working on other sites? (Newegg.com has a lot of scripts, to name one) How about other vBulletin forums? (if you happen to be registered with one)
 
I'll try neweg.com. But it's really, really, really, really, really, really, really, really, really, really strange that this forum shows no pulldown menu on at least 3 operating systems and 3 different webbrowsers.
 
Hmmm......Just a wild thought....2 of the 3 operating systems are Ubuntu-based (Xubuntu/Lubuntu) and 1 is the original Ubuntu 12.04.1 version....Has it something to do with (U/X/L)buntu itself?????

---

### Post by Elfy on 2012-09-19
The only issue I have ever had with the forum was when it started using the yahooapi thing and I had it blacklisted. 

I've used it in kubuntu/ubuntu/xubuntu and lubuntu, I've used it in respins. 

I don't think it's the forum - I think it is something going on where you are. 

But I'm an electrician ...

---

### Post by GeForce 9500GT on 2012-09-19
> **Elfy said:**
> The only issue I have ever had with the forum was when it started using the yahooapi thing and I had it blacklisted. 
Like in [this link]("http://ubuntuforums.org/showpost.php?p=12243643&postcount=12")? How do i add these rules in Adblock Plus btw??
 
 
> I don't think it's the forum 
I'm pretty sure about that too. Thats the reason of my thought.
 
> I think it is something going on where you are. 
Probably yes. But what?
 
> But I'm an electrician ...
I'm a Piping Engineer and there's nothing strange to be found in my pipeline :lolflag:
I just have a weird challenge for you guys.

---

### Post by vasa1 on 2012-09-19
> **GeForce 9500GT said:**
> ...
Hmmm......Just a wild thought....2 of the 3 operating systems are Ubuntu-based (Xubuntu/Lubuntu) and 1 is the original Ubuntu 12.04.1 version....Has it something to do with (U/X/L)buntu itself?????
Why?
No one else who has read this thread has the same problem (unless they deliberately block certain scripts from running). I'm assuming they've checked, as I have, while running some flavor of Ubuntu.

(I don't have a problem with Xfce 4.10 on Ubuntu 12.04 or [s]with[/s] after installing lubuntu desktop since that was what you were using initially. BTW, I'm quite liking it.)

---

### Post by GeForce 9500GT on 2012-09-19
> **vasa1 said:**
> Why?
No one else who has read this thread has the same problem (unless they deliberately block certain scripts from running). I'm assuming they've checked, as I have, while running some flavor of Ubuntu.
 
Like i said, it's a wild thought of me. And like i said over and over again, after every fresh/new/clean install of (U/Xu/Lu)buntu **not** installing any add-on in Firefox i encounter the same problem with Google Chrome/Chromium and Midori, Netsurf, Empathy browser as with Firefox: no pulldown menu's. 
 
So, basically, I am more convinced now that it has nothing to do with the browser or Adblock or Noscript or any Flash or Java blocking script. Even if hundreds of people here telling me that they haven't this problem. 
 
Believe me when i'm telling you that i fully understand your message. But it's getting a bit weird now. Maybe i'll try Linux Mint, see if that does make any difference. 
 
Just one thing: can it be my ISP blocking stuff???

---

### Post by vasa1 on 2012-09-19
> **GeForce 9500GT said:**
> ... Maybe i'll try Linux Mint, see if that does make any difference. 
 
Just one thing: can it be my ISP blocking stuff???
I think trying Mint is a fantastic idea. We read about how Mint has solved so many problems for so many people.

Wouldn't Ubuntu and Windows have the same ISP? In your first post you mentioned not having problems with "Windows Explorer".

---

### Post by GeForce 9500GT on 2012-09-19
> **vasa1 said:**
> Wouldn't Ubuntu and Windows have the same ISP? In your first post you mentioned not having problems with "Windows Explorer".
 
True, but that's at my work. Just to see if it occured there as well.
hmmmm...really a stupid Linux problem then??

---

### Post by vasa1 on 2012-09-19
> **GeForce 9500GT said:**
> True, but that's at my work. Just to see if it occured there as well.
hmmmm...really a stupid Linux problem then??
You really are providing information in a misleading way.

---

### Post by GeForce 9500GT on 2012-09-19
> **vasa1 said:**
> You really are providing information in a misleading way.

Sorry for that.

Just opened this forum on my Samsung Galaxy S2 with Dolphin browser and guess what???? No pulldown menu!!! 

Could it be my ISP who is blocking some stuff or could it be some setting on my router which is blocking stuff?

---

### Post by Elfy on 2012-09-19
Possibly - yahoo*anything* perhaps ...

---

### Post by coffeecat on 2012-09-19
> **GeForce 9500GT said:**
> or could it be some setting on my router which is blocking stuff?


I was beginning to wonder that. You can block certain domains in some routers, so check that. Also - I had a weird problem with a Netgear router  once, although I'm not criticising Netgear specifically - they seem to have a good reputation. I guess mine was faulty. It would randomly suddenly start blocking some websites, or some parts of some websites for no particular reason. Nothing was set in the content filtering page, and a reboot of the router would fix it. Until a few days or weeks later when it would start playing up again.

---

### Post by lisati on 2012-09-20
> **coffeecat said:**
> I was beginning to wonder that. You can block certain domains in some routers, so check that. Also - I had a weird problem with a Netgear router  once, although I'm not criticising Netgear specifically - they seem to have a good reputation. I guess mine was faulty. It would randomly suddenly start blocking some websites, or some parts of some websites for no particular reason. Nothing was set in the content filtering page, and a reboot of the router would fix it. Until a few days or weeks later when it would start playing up again.

Even OpenDNS, if you're using it, can be set to block certain pages.

---

### Post by GeForce 9500GT on 2012-09-24
Ok, just checked my router firwall settings and there was an option under the security settings to block pop-up menu's which was checked. I unchecked this option and now i have the puilldown menu's! this topic is solved!

---

### Post by Elfy on 2012-09-24
Excellent :)

---

