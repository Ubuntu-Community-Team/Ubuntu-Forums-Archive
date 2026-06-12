---
title: "Custom GTK"
date: 2009-04-04
forum: Desktop Environments
---

### Post by LIB53 on 2009-04-04
I've been working on a personal mod of the Dust GTK under Jaunty Jackalope. When i use the original Dust, root apps use Dust too. When i use my mod, root apps use the ugly basic gtk. I understand this is for some failsafe purpose, so could i make my mod fall back onto the original dust gtk for root apps?

And just for the hell of it, i attached a screenshot of my mod.

---

### Post by ad_267 on 2009-04-04
> **LIB53 said:**
> I've been working on a personal mod of the Dust GTK under Jaunty Jackalope. When i use the original Dust, root apps use Dust too. When i use my mod, root apps use the ugly basic gtk. I understand this is for some failsafe purpose, so could i make my mod fall back onto the original dust gtk for root apps?

And just for the hell of it, i attached a screenshot of my mod.

This doesn't really answer your question, but another solution would be:

sudo ln -s $HOME/.themes /root/.themes
sudo ln -s $HOME/.icons /root/.icons

That way, root always has the same themes available that you do.

---

### Post by LIB53 on 2009-04-04
> **ad_267 said:**
> This doesn't really answer your question, but another solution would be:

sudo ln -s $HOME/.themes /root/.themes
sudo ln -s $HOME/.icons /root/.icons

That way, root always has the same themes available that you do.

Yeah, i know that trick. That's better than nothing, but i still want a distinction between root windows and other windows. :(

---

### Post by ad_267 on 2009-04-04
Well you could create a directory in /root/.themes with the same name as your new theme, but link it to another theme like the original dust theme.

---

