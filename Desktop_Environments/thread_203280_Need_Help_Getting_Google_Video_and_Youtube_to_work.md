---
title: "Need Help Getting Google Video and Youtube to work"
date: 2006-06-25
forum: Desktop Environments
---

### Post by lastexyle on 2006-06-25
Youtube works in Konqueror but in FireFox I get 
> Hello, you either have JavaScript turned off or an old version of Macromedia's Flash Player. Click here to get the latest flash play

And Google Video doesn't work in either, I have javascript and flash installed, what gives?

---

### Post by K.Mandla on 2006-06-25
I'm not 100 percent sure, but I thought that Google Video relied on Flash 8, which Linux doesn't have (I think we have 7). Perhaps someone can verify that.

---

### Post by hippy4life on 2006-06-25
[QUOTE=K.Mandla]I'm not 100 percent sure, but I thought that Google Video relied on Flash 8, which Linux doesn't have (I think we have 7). Perhaps someone can verify that.[/QUOTE]

i have no problems using google video under ubuntu so i dont think its flash 8 dependant

---

### Post by chalex on 2006-06-25
AFAIK both depend on just Flash.  I have the Flash Mozilla plug-in installed in Dapper and I can see movies on both sites without a problem.  I used EasyUbuntu to install the Flash plugin.

---

### Post by lastexyle on 2006-06-25
I found a tutorial for video playback, now it works great (in firefox, flash is really laggy and skips in Konqueror for some reason). Not sure exactly what changed though since I could already view flash on other web sites.

---

### Post by dgermann on 2006-06-26
lastexyle--

Mind sharing where that tutorial on video playback can be found? Thanks!

---

### Post by lastexyle on 2006-06-26
Unfortunatly I can't remember exactly where I found it and my history doesn't seem to have been saved. I found it on a digg.com page that I found through google. That's somewhere to start, I'll post again if I can find the page again.

---

### Post by scxtt on 2006-06-26
sounds like a flash problem - since both google video and youtube use flash ... do and "about:plugins" in firefox and see what you have.```
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r25

MIME Type 	                Description 	        Suffixes  Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf       Yes
application/futuresplash 	FutureSplash Player 	spl       Yes
```

---

### Post by dgermann on 2006-06-27
Thanks, lastexyle!

No rush. Let us know if you find it.

---

### Post by lastexyle on 2006-06-30
I found it, but unfortunatly it doesn't work anymore (The repository it gives is dead). But I figured out how to get flash working without going through their tutorial. Make sure you have the package ALSA-OSS then follow these steps: Get the linux flash plugin from adobe.com and install it, then open /etc/firefox/firefoxrc and change FIREFOX_DSP="none" to "aoss." It should work.

Here's the link incase it gets updated or the links start working again: [http://www.ehomeupgrade.com/entry/2663/how-to_get_full](http://www.ehomeupgrade.com/entry/2663/how-to_get_full)

---

### Post by dgermann on 2006-06-30
Thanks, lastexyle!

---

### Post by Sabrage on 2006-07-08
> **chalex said:**
> AFAIK both depend on just Flash.  I have the Flash Mozilla plug-in installed in Dapper and I can see movies on both sites without a problem.  I used EasyUbuntu to install the Flash plugin.

what is the name of the plug-in? I searched for a flash extension for firefox  but could not find it.... And will I need to install flash or just the plug-in? I'm trying to get Google Video and Youtube working....

---

