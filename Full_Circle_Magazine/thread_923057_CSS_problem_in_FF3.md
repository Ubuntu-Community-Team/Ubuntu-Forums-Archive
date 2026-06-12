---
title: "CSS problem in FF3"
date: 2008-09-18
forum: Full Circle Magazine
---

### Post by stevesmith on 2008-09-18
Hi wonderful Full Circle People :)

You've got a div covering up most of your menu in Firefox 3 on Windows.  Most of the menu isn't clickable.  In IE it's fine, haha, turn up for the books :)

Screenshot attached.

---

### Post by sillyxone on 2008-09-18
nice spotting!

I've been clicking there a few times before and never spot the problem. Perhaps I always move the mouse from below to the top menu and click as soon as the link change its color.

---

### Post by stevesmith on 2008-09-18
lol :) I spent ages going up down, up down, trying to work out how to download the darn thing!

---

### Post by ronniet on 2008-09-18
yeah it's something our web guy is working on. The links do work but usually you need to have your pointer just below the words to get the link...  :(

---

### Post by Steve Smith on 2008-09-18
:) I just had a look at it and this made me smile - I guess you got the theme from a movie website, or you've been hacked, one or the other.  I hope it's the first!  Delete the following from near the top and you'll be sorted.

[HTML]<div style="overflow: hidden; width: 530px; height: 21px; left: 30px; top: 12px; position: absolute; z-index: 1; font-family: Arial; font-size: 12px;">
<br><br>Header information: <a href="http://my-movie-download.com/" title="movies download">download movies</a> online. Find the best movie online deals. Buy membership and enjoy, you own what you download. Online movie rental service.
</div>[/HTML]

---

### Post by ronniet on 2008-09-18
> **Steve Smith said:**
> :) I just had a look at it and this made me smile - I guess you got the theme from a movie website, or you've been hacked, one or the other.  I hope it's the first!  Delete the following from near the top and you'll be sorted.


**Good spotting! Thanks for that.**
We use the 5thirtyOne theme, I can only assume we got it from a 3rd Party website with dubious links  :(

Thanks again for spotting that, admin is on the case...  :KS

---

