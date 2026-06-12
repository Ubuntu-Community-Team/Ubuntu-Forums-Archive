---
title: "[Req] Ubuntu Spatial Patch/Hack for other distros"
date: 2005-07-09
forum: Desktop Environments
---

### Post by joekr on 2005-07-09
Hey all,

to any users out there well-versed in coding & programming: I'm requesting the patch/hack which allows Ubuntu's gnome to activate "Ubuntu Spatial".  I'd like to apply this patch to my Gentoo installation as I have grown fond of this feaure whilst using Ubuntu.

Thanks in advance,

joe

---

### Post by joekr on 2005-07-12
Can someone point me in the right direction at least?

---

### Post by poptones on 2005-07-12
Having never used gentoo I am curious: what is the difference between "gnome spatial" and "ubuntu sptial?"

I personally hate what they did with hoary. All I can tell is they swapped the two buttons around, it makes it a giant pain in the butt to go back and forth between my 9warty) laptop and my hoary desktop. I wish they would just give an option in the configuration editor so WE could tell nautilus what to do on middle click and left click.

---

### Post by psychicdragon on 2005-07-12
In ubuntu spatial mode nautilus closes the parent window whenever you open a new directory. I find this behaviour incredibly annoying but I guess some people like it.

---

### Post by poptones on 2005-07-12
[QUOTE=psychicdragon]In ubuntu spatial mode nautilus closes the parent window whenever you open a new directory. I find this behaviour incredibly annoying but I guess some people like it.[/QUOTE]
 I agree. I think that must be the change I noticed on hoary. Very, very annoying.

I want a left click that opens a new window without closing parent, and a middle click that opens a file browser. Of course many probably don't want that at all... if I knew how to add such a switch myself I'd do it and post a deb for it.

---

### Post by hondje on 2005-07-12
[QUOTE=joekr]Hey all,

to any users out there well-versed in coding & programming: I'm requesting the patch/hack which allows Ubuntu's gnome to activate "Ubuntu Spatial".  I'd like to apply this patch to my Gentoo installation as I have grown fond of this feaure whilst using Ubuntu.

Thanks in advance,

joe[/QUOTE]

No well versed required!  \\:D/ 

Just press alt-f2, and in the run dialog enter 
```

gconftool-2 --type bool --set /apps/nautilus/preferences/no_ubuntu_spatial true

``` 

Voila! If that doesn't work, you can do it the clicky way by opening up Applications->System Tools -> Configuration Editor, and go under apps -> nautilus -> preferences and click the little check box next to no_ubuntu_spatial :)

Dogg

---

### Post by poptones on 2005-07-12
[QUOTE=hondje]No well versed required!  \\:D/ 

Just press alt-f2, and in the run dialog enter 
```

gconftool-2 --type bool --set /apps/nautilus/preferences/no_ubuntu_spatial true

``` 

Voila! If that doesn't work, you can do it the clicky way by opening up Applications->System Tools -> Configuration Editor, and go under apps -> nautilus -> preferences and click the little check box next to no_ubuntu_spatial :)

Dogg[/QUOTE]
 Except.. joekr was asking for a way to **enable** this feature in another distribution, not **disable** it in ubuntu.

But we are half way there. I sure appreciate the reminder. :)

---

### Post by hondje on 2005-07-13
[QUOTE=poptones]Except.. joekr was asking for a way to **enable** this feature in another distribution, not **disable** it in ubuntu.

But we are half way there. I sure appreciate the reminder. :)[/QUOTE]

My reading comprehension skills aren't that great :)  Closest I can figure out without having gentoo availiable is this, but it's not very good and doesn't get rid of those annoying browser buttons.

```

gconftool-2 --type bool --set /apps/nautilus/preferences/always_use_browser true
gconftool-2 --type bool --set /apps/nautilus/preferences/start_with_location_bar false
gconftool-2 --type bool --set /apps/nautilus/preferences/start_with_side_bar false
gconftool-2 --type bool --set /apps/nautilus/preferences/start_with_status_bar true

```

Outside that, the best I could find between phonecalls was

[http://www.amedias.org/~koke/patches/ubuntu-nautilus-02_ubuntuspatial.patch](http://www.amedias.org/~koke/patches/ubuntu-nautilus-02_ubuntuspatial.patch)
[http://www.amedias.org/~koke/debian/hoary/nautilus_2.10.0-0ubuntu8.diff.gz](http://www.amedias.org/~koke/debian/hoary/nautilus_2.10.0-0ubuntu8.diff.gz)

Sebastien Bacher is the guy who maintains and made those, maybe digging around his site or something would be more productive.

Dogg

---

