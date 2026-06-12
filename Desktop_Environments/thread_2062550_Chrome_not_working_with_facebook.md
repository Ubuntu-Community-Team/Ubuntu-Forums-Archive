---
title: "Chrome not working with facebook"
date: 2012-09-25
forum: Desktop Environments
---

### Post by pmla on 2012-09-25
Anyone with this issue?
Using chrome in ubuntu 12.04 64x and trying to access facebook pages it extremely slow, times out and or:
No data received
Unable to load the webpage because the server sent no data.
Here are some suggestions:
Reload this webpage later.
Error 324 (net::ERR_EMPTY_RESPONSE): The server closed the connection without sending any data.

Already cleaned ubuntu chrome cache.
Firefox seems to work, chrome for windows seems to work also, seems to be affecting chrome just ubuntu version. Other pages seem to work fine.

---

### Post by drmrgd on 2012-09-25
This seems to have been like this for some time now, and there's no real fix that I could find.  I usually have to click on a link in Facebook, and then when the empty page loads, click refresh and it'll load.  It's quite a pain as I have to do that procedure for every single page that I go to.  

The only solution that I found, which was from a Google-Chrome developers forum (or something similar - I don't quite remember), is to make sure that the address is prefixed with HTTPS:// and not [HTTP://.](HTTP://.)  For me that didn't really work as it automatically used HTTP for every page when I clicked on it and I couldn't figure out how to permanently force it to use the HTTPS protocol.  Since I don't really use Facebook all that much, I didn't really pursue it much further.  That might be a good starting point for you, though.

---

### Post by pmla on 2012-09-25
> **drmrgd said:**
> force it to use the HTTPS protocol

Funny enough, mine is actually forced to use https, it always loads pages or links in https. You can for it in your facebook security settings, option to always use secure connection.

---

### Post by drmrgd on 2012-09-25
Hmmm...thanks for the tip.  I'll have another look at that.  I thought I had already set this as part of the fix, but I might not have.  It sounds, though, like this is not part of your specific problem.  Sorry I don't have any more suggestions:confused:

---

### Post by Peetra on 2012-09-26
When it lags, it lags with reqonq, chrome and firefox, Ubuntu 10.04, Kubuntu 12.04 and Ubuntu 12.04. Doesn't seem to lag with win7 clean install, but I can't get it not to lag from within winXP in virtualbox on my Kubuntu. It although seems to wake up if I simultaneously first log in at win7 and then continue at my Kubuntu.

Here is something that bothers me a great deal, as i am used to fix windows computer issues with linux and not the other way around. 

I mostly use FB  to play (bubble witch saga FTW!!!!), and I have no problem accessing the app-pages that have the games in frames. 

I have tried with and without https, but really, there is no usage for FB these days if you don't use https.

I am now using a plugin that masks my user agent to lure FB  to believe that I am in with anything else that I am, juggling around changing user agent actually makes it fewel like it would work better, or trying to access FB at [https://beta.facebook.com/](https://beta.facebook.com/) But really, it might just be tht juggling around keeps me busy and when I am busy I am happy and when I am happy lag doesn't bother me that much. :lolflag:

---

### Post by pmla on 2012-09-27
Wow... firefox also affected.

Facebook is unusable in ubuntu 12.04 64x :)

Windows versions of firefox and chrome, everything runs fine, win7 64x virtualbox guest also works fine with chrome. Well just to show this as nothing to do with network/router/firewall.

---

### Post by SpeedySparrow on 2012-10-12
I might not have the exact same issue but similar. On my 64bit 12.04 system I can open Facebook, scroll through the pages but if I try to enter anything in a form, ie. comment on something, it is so so so slow if responsive at all. However, this is not just a Facebook issue I experience it with almost all web forms. No problems with Firefox.

---

### Post by SpeedySparrow on 2012-10-23
I have updated to 12.10, problem still exist. Did a reinstall of Chrome and it seemed to remedy the issue but just for one day. Now the issue is back. hmmm.

> **SpeedySparrow said:**
> I might not have the exact same issue but similar. On my 64bit 12.04 system I can open Facebook, scroll through the pages but if I try to enter anything in a form, ie. comment on something, it is so so so slow if responsive at all. However, this is not just a Facebook issue I experience it with almost all web forms. No problems with Firefox.

---

### Post by riramar on 2013-05-04
Same problem here but with Ubuntu LTS 12.04 32bit. I can not load facebook.com on Chrome or Firefox but in my Windows 7 in another machine works normaly.
Any news about this problem?

---

### Post by midnightramen on 2013-05-06
...could be the browser version. Haven't noticed as much of a problem with Firefox 20. Doesn't quite explain the issue affecting Chrome though. I usually notice this happening intermittently at night, so I had figured it has something to do with bandwidth management while some night deployments.

---

### Post by riramar on 2013-05-07
It could be the browser specific for linux. I don't think this is a bandwidth problem because I did a test using my Ubuntu box and another Windows laptop at the same time and I could access by Windows and had some problems with Ubuntu. In my case is intermittently as well.

> **midnightramen said:**
> ...could be the browser version. Haven't noticed as much of a problem with Firefox 20. Doesn't quite explain the issue affecting Chrome though. I usually notice this happening intermittently at night, so I had figured it has something to do with bandwidth management while some night deployments.

---

