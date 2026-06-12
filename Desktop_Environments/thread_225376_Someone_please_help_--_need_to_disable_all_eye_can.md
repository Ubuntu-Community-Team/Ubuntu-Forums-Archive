---
title: "Someone please help -- need to disable *all* eye candy in Gnome"
date: 2006-07-29
forum: Desktop Environments
---

### Post by harisund on 2006-07-29
So ... here's my scenario. 

I have a Ubuntu default installation and I want to disable all eye candy, for speed. 

I know, your first response is probably going to be install XFCE. But no, the problem with XFCE is I am getting a smaller resolution when I try to access it using FreeNX, and since these are all headless machines that I am talking about, I need FreeNX desperately. 

What are your suggestions and ways to disable eye candy in Gnome/Metacity?

---

### Post by win_zik on 2006-07-29
There's probably more, but one thing that comes to mind is:
Open gconf-editor, go to apps -> metacity -> general and check reduced resources.

---

### Post by harisund on 2006-07-29
Ok done. Thanks .. as far as I can see, that creates an outline when moving windows. I guess that helps a lot .. thanks again. 

Other suggestions? Perhaps I can change the window manager from Metacity to something else?

---

### Post by win_zik on 2006-07-29
Just had an other idea.
Did you try to change the default depths form 24bit to 16 bit?

You shouldn't see much of a difference, but it should take less resources.

---

### Post by harisund on 2006-07-29
Hmm...I didn't know that would affect. This is a headless node and the output is through FreeNX. Do you think it will still give a performance benefit? (I am willing to try everything :))

---

### Post by win_zik on 2006-07-30
I'm not really sure, but I think it could be worth a try.

Btw., to change it just edit the xorg.conf and change the Default Depth from 24 to 16. After that restart X and see if it has an effect.

---

