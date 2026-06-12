---
title: "Opera fonts: mostly okay, but still...."
date: 2006-09-01
forum: Desktop Environments
---

### Post by robenroute on 2006-09-01
Most web sites show well-rendered fonts in Opera (using 9.00 build 344), but [The Register]("http://www.theregister.co.uk/") and [Dvorak's Blog]("http://www.dvorak.org/blog/") (the italic print here) leave a lot to be desired (jagged edges, mainly).

Someone out there who knows how to tackle this problem? Thanks a bunch.


Rob

---

### Post by robenroute on 2006-09-03
Hmmm, nobody struggling with the font problems?

---

### Post by gpierce on 2006-09-03
I don't use Opera, but in my experience it's nearly every web page. The most easy to describe and conspicuous difference is the shape of the upslanting stroke in the letter k. In Windows with cleartype turned on, the whole letter is well-shaped and clear, but in every GNU/Linux distro and on both CRT's and LCD's, I have tried (not just Ubuntu) that upslanting stroke is thinned and, narrowed and less distinct. Why this is I don't know. There are other subtle differences. This was just easiest for me to describe. I have not found a solution for this. I have tried adjusting the antialiasing in the gnome font preferences, but this doesn't work either. So while I understand your frustration, I don't know what to do about it. When people say Linux requires polish, this is one feature--the fonts and rendering--I always think about. It may seem like a trivial thing but it is one aspect that makes using a Linux computer painful. The display is how we interact with our computers and if the screen is crummy then our overall impression of the computer is that it is poor even though it may sport the greatest and fastest chips. 

I think commercial companies really understand the importance of appearance better than free software developers and invest great efforts in improving their user interface. Apple understands this and so does MSFT. I hope that future Linuxes have better fonts and more importantly better rendering.

Enough ranting. Hope you find a solution. I'll be watching this thread. 

_greg

---

### Post by mssever on 2006-09-03
This seems to be an Opera problem. I'm getting pixellated fonts on those sites in Opera but not in Firefox--Firefox looks great. However, I did notice a number of websites--those that didn't specify a font--appeared very badly kerned in FF. For example, in the combination "at", the two letters would be touching. Other combinations would have too much space in between. Changing FF's default font fixed it. I use Deja Vu Sans, Deja Vu Serif, and Deja Vu Mono with great success.

Note: I've set those same font to be defaut in Opera, but it doesn't make any difference. Of course, I don't know what fonts those site are using. I don't feel like combing through the source to find out.

---

### Post by gpierce on 2006-09-03
Wish I had a solution for you. I tried the Edgy Eft release today and  noticed that the fonts in Edgy Eft look significantly better in the console. It might be that easier reading and happier browsing are in the future for Ubuntu.

---

### Post by robenroute on 2006-09-04
Good news (at least it solved my problems):

[http://my.opera.com/community/forums/topic.dml?id=128290](http://my.opera.com/community/forums/topic.dml?id=128290)

Hope this helps

---

### Post by gkiller on 2006-09-04
Hey thanks for that link... that worked for me too.

For others who also want better fonts in Opera, go here:

[opera:config#UserPrefs|EnableCoreXFonts]("opera:config#UserPrefs|EnableCoreXFonts")

and disable it. Then restart Opera.

---

### Post by Bree on 2006-09-04
thanks a lot :D  this font thing had been bugging me for a while, was just gonna make a thread about it actually.

---

### Post by Junx on 2008-02-02
I almost hate to bump an old thread, but this issue still exists in Opera 9.50 beta 1, so the solution (which works by the way) still works.  You can put it in /etc/opera6rc or your own ~/.opera/opera6.ini config.

---

### Post by tobodestroyer on 2008-06-24
> **Junx said:**
> I almost hate to bump an old thread, but this issue still exists in Opera 9.50 beta 1, so the solution (which works by the way) still works.  You can put it in /etc/opera6rc or your own ~/.opera/opera6.ini config.

Hi,

I'm running Opera 9.5 on Ubuntu and I can't turn off smooth or clearfonts. How can I do it. I find the slightly pixelated look much clearer. Is there a way I can turn it off in Opera? I have in Ubuntu itself and all other applications fo it must be a setting within Opera.

---

### Post by durand on 2008-06-24
> **gkiller said:**
> Hey thanks for that link... that worked for me too.

For others who also want better fonts in Opera, go here:

[opera:config#UserPrefs|EnableCoreXFonts]("opera:config#UserPrefs|EnableCoreXFonts")

and disable it. Then restart Opera.

That works nicely here. Thanks!

This is in 9.5 btw.

---

