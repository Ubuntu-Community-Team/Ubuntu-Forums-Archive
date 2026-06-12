---
title: "Strange pop up ad.  Not in browser?  From where?"
date: 2016-03-03
forum: Desktop Environments
---

### Post by LazyBoy on 2016-03-03
Running ubuntu 15.04 Unity and chrome with uBlock Origin.  
I've seen this pop up ad a couple of times, outside any browser window.
This was the first time I got a screen shot.
(It's from a dual screen setup with some Mac-like decorations.)
It goes away in a few seconds -- I haven't interacted with it yet.

It doesn't look like a browser window.
Is this an Ubuntu thing?

---

### Post by Frogs Hair on 2016-03-03
Do you have any razer chroma devices ? The popup is for a forum, but they make gaming keyboards mice and and so on.

---

### Post by buzzingrobot on 2016-03-04
Doesn't Chrome allow some components to continue running when Chrome itself is not?

---

### Post by Bucky Ball on 2016-03-04
Just throwing this in. 15.04 is no longer supported. It gets no updates and that includes security updates. Advise you upgrade to 15.10 before it becomes a more difficult task than currently. Good luck.

---

### Post by LazyBoy on 2016-03-05
> **Frogs Hair said:**
> Do you have any razer chroma devices ? The popup is for a forum, but they make gaming keyboards mice and and so on.

I've got a Razor Gaming mouse at home on a Windows box.  (It's never been attached to anything else.)

This popup is at work on an Ubuntu Box.  
But what program is making the popup?  Is that NotifyOSD?  Chrome?

---

### Post by Bucky Ball on 2016-03-06
My last post is even more pertinent in a work environment. You are using EOL operating system in a work/production environment??? Not good as, apart from the fact this is a security concern, we can't give you much help with it, apart from helping you upgrade to a supported release, and the possibilities of any live support will diminish over time. :-k

Hopefully you can get to the bottom of your pop-up ad, though. 

Anyway, sorry, off-topic ... :|

---

### Post by daniii10 on 2016-03-08
I think it's push notification from this website. Go to [https://insider.razerzone.com/](https://insider.razerzone.com/) and right-click then "view page info". Click "permissions" then scroll down, and under "show notification" click block.

---

### Post by LazyBoy on 2016-03-09
> **daniii10 said:**
> I think it's push notification from this website. Go to [https://insider.razerzone.com/](https://insider.razerzone.com/) and right-click then "view page info". Click "permissions" then scroll down, and under "show notification" click block.

Thanks!  There was a Disable button at the bottom of the page.

I do NOT have an account there.
I do not recall visiting the website, although it's possible.
If I did drive by, I would not have ASKED for push updates.
I was definitely not on that site when I was seeing the popup.

I just looked in my cookies.  It showed:
> insider.razerzone.com                      2 Cookies, Local storage, Service Workers

I googled "Service Worker Cookie" and it's scary!  
> A service worker is a script that is run by your browser in the background, separate from a web page, opening the door to features which don't need a web page or user interaction. Today, they already include features like push notifications and in the future it will include other things like, background sync, or geofencing.

How is than anything but a bot infection?  Now I need a way to turn off a class of Cookies.

---

