---
title: "Firefox with high CPU load on certain webpages"
date: 2005-10-18
forum: Desktop Environments
---

### Post by johanPO on 2005-10-18
Hi,

I have two PCs one with Breezy and one with Hoary. The first one is a 2.4 GHz Athlon and the second one is an old Toshiba laptop with an 1GHz Pentium processor. 
On both these I get a very high CPU usage (close to 100%) when I look at certain web pages. One example is a [www.chip.de](www.chip.de)

When I try this at work, where we are using Windows, firfox is behaving normally.
Just for fun I installed Mozilla, and it does not show the same behaviour

Has anyone seen this with other webpages? I have tried to search through different forums, but not found any solution...

Thanks

---

### Post by Hairy_Palms on 2005-10-18
that page caused mega high load on mine, but ive never noticed it anywhere else, is that the only site it does it on?

---

### Post by johanPO on 2005-10-18
That is the worst one I have found... so that's my test page. 
I have found others with high loads as well, but none as bad as this one. Right now I am at work, so It will have to wait until I get home again. 

On my XP box, I get a short but high peak.
Thanks for trying this out. 


Johan

---

### Post by rwabel on 2005-10-18
I've noticed the same with chip and other webpages. firefox is sometimes terrible. With opera there is no problem

---

### Post by joshuapurcell on 2005-10-18
I've been using Opera for the last couple of weeks and it has been able to handle any webpage I usually have problems with in Firefox. Firefox has plenty of plugins and extensions, but Opera seems to handle a wider range of websites.

---

### Post by johanPO on 2005-10-19
I tired with a Knoppix CD, and I see the same effect. Must be some feature in the linux version of firefox. Will probably migrate to Opera, that seems to be doing better

---

### Post by SilentCacophony on 2005-10-19
Looks to me like it is the macromedia flash content. I don't know if it's the plugin or the way firefox uses it, but I've noticed it eats my cpu cycles ever since moving to Firefox while I was still using Windows.

I also noticed that if you right-click on any individual flash animation, and reduce the quality from the popup menu, cpu usage goes down accordingly.

What burns me is that I've never been able to find a way to set the quality as a preference for flash content. It always displays highest quality when loading.

I used to use the adblock extension to block the sites that served the most annoying flash ads.

---

### Post by argosreality on 2005-10-19
[QUOTE=johanPO]Hi,

I have two PCs one with Breezy and one with Hoary. The first one is a 2.4 GHz Athlon and the second one is an old Toshiba laptop with an 1GHz Pentium processor. 
On both these I get a very high CPU usage (close to 100%) when I look at certain web pages. One example is a [www.chip.de](www.chip.de)

When I try this at work, where we are using Windows, firfox is behaving normally.
Just for fun I installed Mozilla, and it does not show the same behaviour

Has anyone seen this with other webpages? I have tried to search through different forums, but not found any solution...

Thanks[/QUOTE]I've constantly found that Firefox just about dies on sites that have alot of heavy flash usage. Anandtech.com has gotten really bad lately with its advertising. If you're using Firefox install the flashblock extension. It'll only load flash animations when you specifically request it by clicking on them. Replaces them with a big gray button. Not asthetically pleasing but better than having your system die.

---

### Post by johanPO on 2005-10-20
Thanks, I tried the flashblock but that was not the problem on this web page. It turns our to be the news ticker. This is not a flash, but an iFrame but seems to be a javascript...

---

### Post by jeremy on 2005-10-20
Write and tell them about how their newsticker is causing problems.

---

### Post by johanPO on 2005-10-20
I'have done that, but honestly I don't think they will consider this a problem of their website. 
I assume the will consider this to be a problem of the firefox implementation under linux, and not of the webpage. If it is running under XP with firefox, and with opera under linux why would this be a problem of their webapge. 

My solution was to add the newsticker to my adblock list, and now I have no problem with this webpage.

---

