---
title: "Need Ps3 Flash player youtube help"
date: 2009-02-06
forum: General Help
---

### Post by kdarkentity on 2009-02-06
I am probably like 40 thousandth person on here asking about this but maybe now someone has a little more resolve.

I am trying to watch videos on youtube in firefox on my ps3, i have installed gnash and that did nothing, and obviously since adobe has not made a flash plugin for the power pc architecture i can not use flash, is there any other alternative to be able to watch youtube vids on ps3?

---

### Post by kdarkentity on 2009-02-06
Well i just installed ubuntu ppc 8.10 on my ps3 and installed gnash and youtubevids will play reasonably well now, but i am still looking for a better solution if there is one.

---

### Post by Tomatz on 2009-02-06
As far as i know adobe doesn't make flash for the ppc arch :(

---

### Post by kdarkentity on 2009-02-07
> **Tomatz said:**
> As far as i know adobe doesn't make flash for the ppc arch :(

No they unfortunately do not, well gnash is a decent alternative, but it's nothing special, at least not yet.

---

### Post by Yashiro on 2009-02-07
You'd really be better off using the default PS3 browser for youtube. They recently updated it and it runs very well.

---

### Post by vageta on 2009-02-08
Hi!
I'm new to this ubuntu, I'm facing the same problem, I can't watch videos on youtube, so i downloaded Gnash but when the download completes i doubled clicked on it but it asks for some program to open the file, but I'm not able to do so..
could anybody throw light on how to fix  this....
I' srry if this is a really stupid question but i'm getting used to this ubuntu.... and this is really confusing:(  and i really don't know whether the version which i'm using is 32 or 64 bit....lol

there are a lot of other problem and i'm looking fr solutions and hope that they would also be fixed

thanks in advance....

---

### Post by kdarkentity on 2009-02-19
> **vageta said:**
> Hi!
I'm new to this ubuntu, I'm facing the same problem, I can't watch videos on youtube, so i downloaded Gnash but when the download completes i doubled clicked on it but it asks for some program to open the file, but I'm not able to do so..
could anybody throw light on how to fix  this....
I' srry if this is a really stupid question but i'm getting used to this ubuntu.... and this is really confusing:(  and i really don't know whether the version which i'm using is 32 or 64 bit....lol

there are a lot of other problem and i'm looking fr solutions and hope that they would also be fixed

thanks in advance....

Are you running ubuntu on a ps3?

---

### Post by Tomatz on 2009-02-21
> **vageta said:**
> Hi!
I'm new to this ubuntu, I'm facing the same problem, I can't watch videos on youtube, so i downloaded Gnash but when the download completes i doubled clicked on it but it asks for some program to open the file, but I'm not able to do so..
could anybody throw light on how to fix  this....
I' srry if this is a really stupid question but i'm getting used to this ubuntu.... and this is really confusing:(  and i really don't know whether the version which i'm using is 32 or 64 bit....lol

there are a lot of other problem and i'm looking fr solutions and hope that they would also be fixed

thanks in advance....


Open a terminal and copy and paste the following:

```
sudo apt-get remove --purge gnash && sudo apt-get install flashplugin-nonfree
```

Press return, enter password and **restart firefox**.

Now you can view flash content :). This will not work on the ppc arch though (ps3).

---

