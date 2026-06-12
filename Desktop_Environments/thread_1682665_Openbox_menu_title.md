---
title: "Openbox menu title"
date: 2011-02-06
forum: Desktop Environments
---

### Post by Typhon on 2011-02-06
Greetings,
Nowadays I use Openbox as a window manager of choice and yesterday I was browsing though Google Images for Openbox screenshots. I saw that some users have a title on their Openbox menu. (see [_this image_]("http://lewk.org/img/securityspin.png"): "Fedora Security Spin").

[_This_]("http://tinypic.com/view.php?pic=6rn9k6&s=7") is my current Openbox menu. As you can see it doesn't have any title. I wonder how can edit menu.xml file to include a title of my choice.

---

### Post by mcduck on 2011-02-06
Use the separator-item with a label on it:

```
<separator label="Ubuntu" />
```

---

### Post by Typhon on 2011-02-06
Excellent, it worked! Thank you very much!

---

### Post by Gaygerbil on 2011-10-17
Thanks for helping me out man.

---

### Post by Sector11 on 2012-01-21
[SIZE="4"][CENTER]**[COLOR="DarkRed"]_A Word of Caution_[/COLOR]**[/CENTER][/SIZE]

If you use the GUI OpenBox menu editor: **obmenu**

It sees:
```
<separator label="SR11 Ops Centre"/>
```
and
```
<separator label="SR11 Cockpit"/>
```
as simple separators!

Do not use **obmenu** to edit separators if you have a few like I do. When I started using them, I found out the hard way.

---

