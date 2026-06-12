---
title: "Help with fonts"
date: 2008-02-04
forum: Desktop Effects &amp; Customization
---

### Post by Gom33 on 2008-02-04
Hi guys,

Trying to make my desktop like MAC OS and I am following the mac4lin guide but do not understand what I need to do for the fonts... it says I need to copy andpaste as root and I do not know what that means... here is a screen shot of what I am talking about...  

[IMG]http://i223.photobucket.com/albums/dd232/Gom33/Screenshot-Mac4Lin_Documentation_2p.png[/IMG]

Any help is GREATLY appreciated...

thanks!

---

### Post by Ub1476 on 2008-02-04
To open Nautilus as root, type:

```
sudo nautilus
```

You can also create a font directory in your home directory and put the fonts inside there. The directory should be called ".fonts".

I you want root applications (update manager, software-sources etc) to look like your normal apps (file-manager, appearance) type this into your terminal:

```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts 
```

---

### Post by jordanmthomas on 2008-02-04
> **Ub1476 said:**
> To open Nautilus as root, type:

```
sudo nautilus
```


Just for the record, you should use gksudo when launching graphical applications so you don't mess up your .ICEAuthority's permissions (and others).

Also, to add fonts, I just do this:
1.  add fonts to my ~/.fonts folder (make it if you don't have one)
2.  run 
```
sudo fc-cache -f
```

And your font is installed.  using fonts:/// should work too though.

---

### Post by Gom33 on 2008-02-04
Thanks for your help guys... Will have to try this when I get home...

---

