---
title: "Want better fonts? There you go!"
date: 2007-08-25
forum: Desktop Environments
---

### Post by tekkenlord on 2007-08-25
Hi all,

I run into an amazing tutorial on how to make your ubuntu desktop look like an OS X desktop. There was a great advice on how to make your fonts look clearer and it's very simple. Just download this file (select save link as)

[http://www.taimila.com/files/fonts.conf]("http://www.taimila.com/files/fonts.conf")

and save it in your home directory as  .fonts.conf 

Restart your X and enjoy!!!

This howto was taken by 

[http://www.taimila.com/?q=node/11](http://www.taimila.com/?q=node/11)

---

### Post by happy-and-lost on 2007-08-25
They look fuzzy to me.

Font rendering looks near perfect in Gutsy ;)

---

### Post by Laterix on 2007-08-25
> **happy-and-lost said:**
> They look fuzzy to me.

Font rendering looks near perfect in Gutsy ;)
If you're referring to the fonts-dialog screenshot then I have to advise that it's scaled screenshot. So it doesn show how they actually look. I like my fonts better with this little "patch" in Feisty. But font-look seems to be a personal preference.

---

### Post by Massive Brain on 2007-08-25
This just enables the auto hinter. Nothing new.

---

### Post by RedSquirrel on 2007-08-27
> **happy-and-lost said:**
> They look fuzzy to me.

Indeed, some people feel that native fonts look more crisp.

In any case, rather than use the file above, one can do:

```
sudo dpkg-reconfigure fontconfig-config
```and choose "Autohinter" for the first question.

---

