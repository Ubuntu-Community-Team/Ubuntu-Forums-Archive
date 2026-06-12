---
title: "Will Beryl work?"
date: 2007-04-25
forum: Desktop Effects &amp; Customization
---

### Post by dannyboy2k on 2007-04-25
Hi,

Can anybody tell me if Beryl will work with my Acer Aspire 5000 laptop, it's about a year old and has an AMD Turion processor with, I presume, an integrated graphics card. I can't find anything that says it has any other graphics card and it didn't cost much so I presume it doesn't have an expensive graphics card.

I'm running Feisty Fawn (very good it is to)

So I'm figuring that this means it won't.

But can anybody tell me for sure because it looks really cool?

Cheers

---

### Post by carlossl on 2007-06-29
I have an Aspire 5000 too, your graphics card is a Sis M760GX and it is the crappiest graphics card I've ever known. I've tried to use Desktop Effects but I only get a white screen (I have to press Esc to get rid of it), so I'm guessing I won't be able to use any other type of cool effect or window manager (just like Aero of Windows Vista, I was never able to use it). I've been looking for some help a long time but unfortunately very few people bought this notebook model, but I still have hope that someone will help us :).

Good Luck!

---

### Post by carlossl on 2007-06-29
Look what I just found! 

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29)

I found a thread of some guy that said that he has an Acer Aspire (didn't say the model) but he said that Beryl works in his computer, so I'll try to follow these instructions, hope you can too.

Good Luck!

---

### Post by digital_exhaust on 2007-06-29
Enter the following in a terminal 

 ```
glxinfo | grep direct
```

If you get "direct rendering:yes" then it should work just fine.

---

