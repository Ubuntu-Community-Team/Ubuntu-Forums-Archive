---
title: "Google Earth and Firefox"
date: 2007-06-01
forum: Gaming &amp; Leisure
---

### Post by tim71 on 2007-06-01
I am having kind of a stupid problem with Google Earth and I am pretty sure that I am not alone with this.

Google Earth itself works without problems, but when I try to access those pictures, which are linked to the map, then things get a bit complicated. Pictures can be seen fine from Google Earth - nice window opens etc., but when I try to access the original picture, then Google Earth will open the original gallery page in Firefox. These pictures are all from panoramio.com gallery (which Google is/has acquired btw) and most of them cannot be seen in Firefox. All other stuff is visible, but not the picture itself. When I click on link "original size", then text appears stating "image 'something.jpg' cannot be displayed, because it contains errors". 

Little bit of a research showed, that this is possibly related with pretty old problem (Firefox inability to show CMYK encoded images). Opera shows all these images without any problem, but Google Earth is always opening these pages in Firefox despite all settings I have changed to use Opera as default web browser.

So the question is - has anyone found some kind of workaround for this issue or found the way to get Google Earth to open these pages on other browser than Firefox?

P.S. And if anyone is interested, whether I'm using GNOME or KDE - nope... I use Xfce as main desktop environment, but have GNOME and KDE also installed.

---

### Post by p110011 on 2007-06-03
I just came here to search this because that's what is happening with mine also.
If I click a Google Earth picture link, I get a message that the image is corrupted. 
Oh well, I was hoping to find a fix.

---

### Post by tim71 on 2007-06-04
The most interesting thing is, that it seems to be some kind of glitch in Panoramio's website, because sometimes all browsers show pictures without problems , sometimes Firefox cannot show any pictures on this site. However Opera and IE (yes... I have to use Windows at work) work without problems.

So problem stays at least in the "default browser" issue - how Google Earth always  opens Firefox...

---

### Post by tim71 on 2007-06-08
Liittle update to this issue...

Afrer some testing it seems, that the problem is Linux-specific. Even when I open these pages in Firefox under wine, there is no problems whatsoever - if I try to open the same page in Firefox on Linux environment, then most of the time almost all of the images on panoramio.com site are missing.

However if Firefox has been previously opened with -P option, then all works fine. When Firefox is opened manually without this switch, then the problem is present again.

And all this is happening, whatever profile of Firefox I am using - is it my default profile with many extensions or is it a brand new, clean profile without any extensions...

---

### Post by p110011 on 2007-06-08
I hope I'm not repeating what you just said, but if I go to Paoramio.com I can view their images. This is without  any Google Earth running.
For me if I click a link in Google Earth is the problem.

---

### Post by tim71 on 2007-06-09
> **p110011 said:**
> I hope I'm not repeating what you just said, but if I go to Paoramio.com I can view their images. This is without  any Google Earth running.
For me if I click a link in Google Earth is the problem.

Something like that - if Firefox gets started from the link in Google Earth, then there is a problem. Also same problem is present, if Firefox is opened with command "firefox".

When I open Firefox with command "firefox -P" then all works - i even modified my launcher button to do this.
Not making much sense, but resolves the problem...

---

### Post by p110011 on 2007-06-09
Oh, I get you now. I'm pretty stuck on GUI stuff thanks to winderz.:)
I'm just happy Google Earth is working now that I am using Feisty. It would not get past the splash when I had 6.10 running.

I wonder if this is a Google Earth for Linux problem, or an Ubuntu bug? 
I'm thinking the first, since I installed it with AutoMatix.

---

### Post by tim71 on 2007-06-11
> **p110011 said:**
> 
I'm just happy Google Earth is working now that I am using Feisty. It would not get past the splash when I had 6.10 running.
It's possible that newer version of Google Earth has something to do with this.
> I wonder if this is a Google Earth for Linux problem, or an Ubuntu bug? 
I'm thinking the first, since I installed it with AutoMatix.
This is probably some strange problem with Firefox on Linux and panoramio.com, because same things happen even when trying to browse panoramio's gallery with Firefox without using Google Earth.

Of course other thing remains unresolved - is there any way to change the browser Google Earth uses...

---

