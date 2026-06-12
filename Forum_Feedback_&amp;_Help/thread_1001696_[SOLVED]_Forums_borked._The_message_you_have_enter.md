---
title: "[SOLVED] Forums borked. The message you have entered is too short"
date: 2008-12-04
forum: Forum Feedback &amp; Help
---

### Post by philinux on 2008-12-04
The message you have entered is too short. Please lengthen your message to at least 1 characters.

Had to change to a "Basic Editor" to get this thread posted.


Found the workaround here.
[http://www.vbulletin.com/forum/archive/index.php/t-143403.html](http://www.vbulletin.com/forum/archive/index.php/t-143403.html)

---

### Post by philinux on 2008-12-04
test reply, Cant use code or any other wraps etc. 


Changing from wysiwyg to basic then back to standard gets me able to reply. But non of the function work like wraps smileys etc.

Vbulletin must have a problem.

No drop down appears in thread tools either.

Also have to adblock *yahooapis* just to get the forum page to load

---

### Post by pp. on 2008-12-04
It's just conceivable that it is a problem on your end. Try and refresh the forum pages.

---

### Post by philinux on 2008-12-04
Refresh the pages.
I've used safe mode in firefox deleted cookies closed FF restarted etc etc etc.


Nothing changed this end at all. Was working fine then not.

It's defo a vbulletin thing. There are lots of posts on vbulletin forum when i google this error.

They probably need to reload the database or something.

I can post now by using the basic editor. But code wraps etc don't work or pull downs.

---

### Post by bapoumba on 2008-12-04
Have you tried clearing the cache ?

---

### Post by philinux on 2008-12-04
> **bapoumba said:**
> Have you tried clearing the cache ?

Yep, I even renamed .mozilla and let it create a default profile. Same thing.

---

### Post by bapoumba on 2008-12-04
Okay, here we go, an advice directly from u-g :)

- Make sure to allow javascript and specifically connections from the yahoo API's.

- Try to disable the adblock plugin. That would explain why the basic editor works because it's not using any of the special javascript in the yahoo api.

---

### Post by yabbadabbadont on 2008-12-04
Given that all yahoo websites pretty much cratered yesterday (my ATT pop3 server was down too, and is hosted by yahoo...) perhaps there were issues with yahooapis earlier today?  (another reason not to use a third party website to host essential javascript...  :roll:)

---

### Post by bapoumba on 2008-12-04
> **yabbadabbadont said:**
> Given that all yahoo websites pretty much cratered yesterday (my ATT pop3 server was down too, and is hosted by yahoo...) perhaps there were issues with yahooapis earlier today?  
Maybe. 

> **yabbadabbadont said:**
> 
(another reason not to use a third party website to host essential javascript...  :roll:)
(forums servers loads.. but it's currently been discussed).

---

### Post by philinux on 2008-12-04
> **bapoumba said:**
> Okay, here we go, an advice directly from u-g :)

- Make sure to allow javascript and specifically connections from the yahoo API's.

- Try to disable the adblock plugin. That would explain why the basic editor works because it's not using any of the special javascript in the yahoo api.

Ok I had to adblock *yahooapis* to even get the forums to load at all.

But it seems all is back to **normal **now so what caused the glitch?
Hey I got stuff back now BOLD etc.

Now I deleted the  *yahooapis* filter all is ok.

---

### Post by shirishagarwal on 2008-12-05
I had the same issue with my old username ShirishAg75. Had to get a new one to function. I also used to get the same issue,

```
The message you have entered is too short. Please lengthen your message to at least 1 characters.
```

Would be trying again my old username, let's see if it works better this time around, otherwise going to create a new thread on the same with this username.

---

### Post by ShirishAg75 on 2008-12-05
Finally got my old username. Had the same issue for last 4 days, now finally fixed.

---

### Post by shirishagarwal on 2008-12-06
had to get back to using the new username again. The old one stopped working (**again**). Getting the same message, can somebody look into it?

---

### Post by CooksWithFire on 2009-05-11
Has anyone been able to fix this problem?

---

### Post by VgnStirfry on 2009-05-17
> **CooksWithFire said:**
> Has anyone been able to fix this problem?

I am having this problem as well!  Can anyone assist?

---

### Post by CooksWithFire on 2009-05-21
I just reinstalled and it worked after, sorry.

---

### Post by cariboo on 2009-05-21
There really is no need to reinstall to solve the problem. Open nautilus (Places-->Home Folder) and press Ctrl-h this will reveal the hidden files and directories. Next back up your bookmarks they are located in ~/.mozilla/firefox/xxxxxxx-default, where xxxxxxx is a random string of letters and numbers, rename ~/.mozilla to ~/.mozilla.bak. When you start Firefox the ~/.mozilla directory will be recreated and problem should be solved. Remember to restore your bookmarks.

---

### Post by virtual reality on 2009-12-23
same problem here too!

vr.

---

### Post by Prostokvashino on 2010-01-30
test ...if posted -need to allow yahoo api  ..if not posted - you don't want to know what I think in this case

---

### Post by awd01 on 2010-10-22
> **bapoumba said:**
> Okay, here we go, an advice directly from u-g :)

- Make sure to allow javascript and specifically connections from the yahoo API's.

- Try to disable the adblock plugin. That would explain why the basic editor works because it's not using any of the special javascript in the yahoo api.

yes this is the solution to my problem!!! But i allowed also all the ubuntuforums.org...
thank you vert much!

---

