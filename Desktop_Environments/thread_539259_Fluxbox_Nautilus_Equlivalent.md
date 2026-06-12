---
title: "Fluxbox Nautilus Equlivalent"
date: 2007-08-31
forum: Desktop Environments
---

### Post by blithen on 2007-08-31
Okay refining this post.

I am a complete FluxBox noob.
So what is a good Fluxbox Nautilus Equlivalent
and also how do I install themes?
Thanks in advance!

---

### Post by fnx.lv on 2007-08-31
Hello.  

As far as I know you can use Nautilus in Fluxbox.  Try this:

Open the .menu file in your ~/.fluxbox directory.  And add the following line somewhere :

```
[exec] (nautilus) {nautilus --no-desktop --browser} </usr/share/pixmaps/nautilus.xpm>
```

This will add an entry to your menu file allowing you to open the Nautilus browser without crashing Fluxbox.  If you like Nautilus this is a perfect way of integrating it into Fluxbox. However if you feel like trying something new then by all means Thunar is a great alternative.  Again, after installing (use the repositories) simply type 'thunar' in a terminal or add it to your menus as before. 

As for themes, that's easy.  Download the theme/themes/ you want ([www.deviantart.com](www.deviantart.com)) is a great place for all sorts of themes and simply put them in your '~/.fluxbox/styles/' folder.  If it doesn't exist make one.  

Hope this helps!

---

### Post by blithen on 2007-08-31
Wow!! Thanks a lot!

---

### Post by kerry_s on 2007-08-31
> **blithen said:**
> Okay refining this post.

I am a complete FluxBox noob.
So what is a good Fluxbox Nautilus Equlivalent
and also how do I install themes?
Thanks in advance!

rox-filer, can do all things nautilus can but faster. make sure to set up compatibility so you have your fluxbox right click. rox also does desktop icons and can set your background.
**sudo apt-get install rox-filer**

[http://fluxbox.sourceforge.net/docbook/en/html/faq.html](http://fluxbox.sourceforge.net/docbook/en/html/faq.html)

---

