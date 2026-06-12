---
title: "how to remove unwanted fonts in Ubuntu 9.04"
date: 2009-04-25
forum: General Help
---

### Post by Cenydd on 2009-04-25
How do I get rid of all the unnecessary Arabic fonts in Open Office 3, on 9.04?

---

### Post by GCoffee on 2009-04-25
Not booted into ubuntu right now (about to do some gaming) but i think there is a folder like /usr/shared/fonts

you will need to be root to create and delete fonts though,

do:

sudo nautilus

then put in your password, then navigate to /usr/shared/fonts

I will check the directory later, but i think thats right.

GC

---

### Post by HermanAB on 2009-04-25
Basically, all you need to do is delete the font files and restart the font server xfs.

---

### Post by fallendarling on 2009-06-08
I made a post earlier today after my similar problem was solved. I do not know, which of the fonts listed in my post are Arabic. All I know, is that SOME of them definitely were, and I no longer have Arabic fonts showing up in my font-pickers.

So Part 1 of this post, may be of help to you. Note that it does remove some other non-English type fonts too, so don't use it verbatim, unless you wish to remove more than just Arabic. Hope it helps though.

[http://ubuntuforums.org/showthread.php?t=912030](http://ubuntuforums.org/showthread.php?t=912030)

The problem was so frustating to me too. All my best to you.

FD

---

### Post by Ichido on 2009-08-06
I have Many TTFs that I cannot remove because I cannot find them?!
They are: akeem, adriana, adrain, abigail, abracadabra, adonis, bria, brinkley, braddon, brody, and about 25 more.

Can anyone help, please?

---

### Post by kerry_s on 2009-08-06
it's better to just uninstall the fonts you don't want through synaptic, just click status> installed, then click on the right & type ttf, it will go straight to them.

---

### Post by Ichido on 2009-08-07
> **kerry_s said:**
> it's better to just uninstall the fonts you don't want through synaptic, just click status> installed, then click on the right & type ttf, it will go straight to them.

Thank You Kerry_s.
I forgot about that.

---

### Post by SeanBlader on 2009-08-11
Here's all the non-english ones I found:

```
sudo apt-get remove ttf-arphic-uming ttf-indic-fonts-core ttf-thai-tlwg ttf-arabeyes ttf-bengali-fonts ttf-kannada-fonts ttf-lao ttf-oriya-fonts ttf-sazanami-gothic ttf-sazanami-mincho ttf-telugu-fonts ttf-unfonts-core ttf-wqy-zenhei
```

---

