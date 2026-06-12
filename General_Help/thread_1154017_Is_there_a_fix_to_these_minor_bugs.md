---
title: "Is there a fix to these minor bugs?"
date: 2009-05-09
forum: General Help
---

### Post by gymophett on 2009-05-09
I just installed Ubunutu 9.04 on my shiny new laptop. :) 
Here is my laptop: [http://www.bestbuy.com/site/olspage.jsp?skuId=9163772&type=product&id=1218040476935](http://www.bestbuy.com/site/olspage.jsp?skuId=9163772&type=product&id=1218040476935)

I noticed some bugs. I have an ATI Radeon 3100 and I can't activate Compiz :(. Which is my main problem, I HAVE to have Compiz!

Then my second bug is when I'm turning it off and on it says 'device not ready' on two seperate drive thingys. I have a dual-boot with Vista Premium.

How can I fix this? Especially Compiz?!

---

### Post by stwschool on 2009-05-09
Not sure if your card is included but ATI recently dropped support for a whole bunch of cards, some not that old, and 9.04 upgraded to a new version of Xorg. The problem here is that the ATI proprietary drivers made for this version of Xorg have dropped the older cards. This means that you're left with the open source ones, which really aren't of the same quality, and won't handle Compiz. In fact, in my experience they won't even handle not flickering like mad. I've not got the link for the list of dropped cards but maybe someone else has or you can google it?

---

### Post by dragos240 on 2009-05-09
did you install video drivers and do sudo apt-get update?

---

### Post by gymophett on 2009-05-09
> **dragos240 said:**
> did you install video drivers and do sudo apt-get update?

I haven't installed the video drivers but have done the update, how do I install my video drivers?

---

### Post by stwschool on 2009-05-09
You might want to run jockey-gtk as that'll look to see if there are any proprietary drivers for your card. If not, you might be better going back to 8.10 and using launchpad to update the more interesting apps.

---

### Post by bapoumba on 2009-05-09
Moved to General Help.

---

