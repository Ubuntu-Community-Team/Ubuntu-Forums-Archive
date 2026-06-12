---
title: "How do you change the Ubuntu logo on Gnome"
date: 2007-01-26
forum: Desktop Environments
---

### Post by JoshuaH1 on 2007-01-26
Hello,

I was wondering how to change the logo on the menu bar(On Gnome) from the orange Ubuntu logo to something else.  I have searched, and found many tutorials on older versions of Ubuntu, which do not work on 6.10.  The reason I'm switching it is because the orange doesn't go well with my desktop theme.  So I'm trying to change the logo to this

[http://img265.imageshack.us/img265/9789/distributorlogoec6.png](http://img265.imageshack.us/img265/9789/distributorlogoec6.png)


Any help would be appreciated,

Thanks.

---

### Post by Stemp on 2007-01-26
> I have searched, and found many tutorials on older versions of Ubuntu, which do not work on 6.10.

What tutorials ? 

Do you mean changing /usr/share/pixmaps/gnome-logo-icon-transparent.png and killall gnome-panel doesn't work ?

---

### Post by LarsKongo on 2007-01-26
It depends on what icon theme you are using. I for example use the etiquette icons. I had to place a distributor-logo.svg in /home/user/.icons/etiquette/scalable/apps/ and then killall gnome-panel to get it working. If you're using the standard Tango icon theme I belive you should replace the distributor-logo.svg in /usr/share/icons/Tango/scalable/places/.

---

### Post by paparucino on 2007-01-26
> **JoshuaH1 said:**
> Hello,

I was wondering how to change the logo on the menu bar(On Gnome) from the orange Ubuntu logo to something else.  I have searched, and found many tutorials on older versions of Ubuntu, which do not work on 6.10.  The reason I'm switching it is because the orange doesn't go well with my desktop theme.  
Thanks.

Run gconf-editor then apps->panel ->objects. You have a lot of object_x folders. Look inside at everyone until you find
```

**object_type   menu-object**

```
Now in **[COLOR="Red"]custom_icon[/COLOR]** right-click under the column **Value** and add/modify the path to your image (a 48x48 .png)
Then check the box **use_custom_icon** and you are ready.

I'm not really sure, but I think it's no necessary to restart gdm.

---

### Post by JoshuaH1 on 2007-01-26
Yeah, No matter what I did. the distributor-logo replace (Yes, I replaced the one for my theme) method wasn't working...

But thanks you paparucino, that worked perfectly, many thanks :D

---

### Post by paparucino on 2007-01-27
> **JoshuaH1 said:**
> 
But thanks you paparucino, that worked perfectly, many thanks :D

Someone told me about this :-)

---

