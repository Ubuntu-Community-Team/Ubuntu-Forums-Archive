---
title: "Forum member count vs time?"
date: 2008-06-11
forum: Forum Feedback &amp; Help
---

### Post by kanem on 2008-06-11
Hi,

I was wondering if records still exist for how many forum members there were here on a given date all the way back to the beginning. And if so, if it would be easy to compile the data and show a "forum # vs time" graph. 

Just thought it would be interesting to see.

---

### Post by p_quarles on 2008-06-11
The greatest number of simultaneous users was 24125, on 4/25/2008. The "active users" count (the number of distinct accounts with activity in the past 30 days) was only added with the newest version of vBulletin, so probably isn't all that useful for overall records.

---

### Post by kanem on 2008-06-11
It occurs to me now that what I want should actually be quite simple, and that I explained it badly in my first post.

I would just like to see total number of members vs time. Everyone has an ID# tagged to their account and a join date. So if I just could see who joined on September 30 2006, for example, I could just look at their ID# and see how many forum members there were on that date.

For instance, on Jan 28, 2008 the forums got its 487459th member. I got that by just randomly picking a name from the active users list at the bottom of the main page. This info for each day (or week, or month) is what I want.

Edit: I realize many people signed up and then left forever, but I'm willing to put that in the error analysis (i.e. ignore).

---

### Post by bapoumba on 2008-06-11
I did this for myself when hardy was released and we hit new top users numbers and online record. But I did not keep it, nor did I keep the data or the posts where I found them.
We were not half way to an exponential curve, so there is room for increase. I should have kept the data..

---

### Post by kanem on 2008-06-11
> **bapoumba said:**
> I did this for myself when hardy was released and we hit new top users numbers and online record. But I did not keep it, nor did I keep the data or the posts where I found them.
We were not half way to an exponential curve, so there is room for increase. I should have kept the data..

I've already started collecting the data. Just by month for now though. I'll post the results when I finish.

---

### Post by DirtDawg on 2008-06-11
> **kanem said:**
> I've already started collecting the data. Just by month for now though. I'll post the results when I finish.

Great idea! Should be interesting.

---

### Post by kanem on 2008-06-12
Here are two graphs. The upper is forum # vs month. I had planned to do by week (or even day) but that would take way too long. I suppose that if the backend of this forum is some kind of SQL it would be trivial for someone with access to extract this info.

Anyway, it's clearly exponential for now. The line is a fit. Using higher order polynomials didn't improve the fit for some reason, so the equation is pretty simple and is included in the graph. There should be over 1 million members in about a year if this continues.

The lower graph is the increase in members in a month vs time. The peaks indicate approximate release dates. It's at 25,000 new members per month now. Wow.

I've included a spreadsheet with the data.

---

### Post by DirtDawg on 2008-06-12
> **kanem said:**
> Here are two graphs. The upper is forum # vs month. I had planned to do by week (or even day) but that would take way too long. I suppose that if the backend of this forum is some kind of SQL it would be trivial for someone with access to extract this info.

Anyway, it's clearly exponential for now. The line is a fit. Using higher order polynomials didn't improve the fit for some reason, so the equation is pretty simple and is included in the graph. There should be over 1 million members in about a year if this continues.

The lower graph is the increase in members in a month vs time. The peaks indicate approximate release dates. It's at 25,000 new members per month now. Wow.

I've included a spreadsheet with the data.

Great work! Amazing stats.

Do you happen to know the month and year the forum started?

---

### Post by LaRoza on 2008-06-12
> **DirtDawg said:**
> 
Do you happen to know the month and year the forum started?

[http://ubuntuforums.org/index.php?page=about](http://ubuntuforums.org/index.php?page=about)

---

### Post by bapoumba on 2008-06-13
Thanks kanem, really nicely done.
May be it can be fitted with a saturation curve (a S-shaped curve for ex.).

---

### Post by matthew on 2008-06-13
kanem: great stuff! Thanks.

---

### Post by kanem on 2008-06-13
You're welcome.

> **bapoumba said:**
> May be it can be fitted with a saturation curve (a S-shaped curve for ex.).
Yeah, that makes sense. I guess it has to turn into that eventually. And with that in mind, I can see how the bottom graph could start looking like a normal distribution soon, which it should if the top one is a saturation curve.

Here's hoping the saturation doesn't start for a few more years.

---

### Post by bhavin.marvadi on 2008-06-15
Great work kanem!! Its people like you who make the Ubuntu Community so special.

Again, great work, bravo. :)

---

