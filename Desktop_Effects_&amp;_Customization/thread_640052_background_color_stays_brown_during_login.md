---
title: "background color stays brown during login"
date: 2007-12-13
forum: Desktop Effects &amp; Customization
---

### Post by travm on 2007-12-13
I'm using Ubuntu gutsy installed on my dell laptop.  Everything is in order except i picked a couple custom themes with different background colors (brown might be cool in africa:) ), and it works when the login window comes up, but when i put my name and password in and click to log in the screen goes default ubuntu brown and stays that way for a few seconds before changing to my more pleasant chosen color.  I have selected the background color for login within gdmsetup, and also changed my background color in my desktop settings.  yet it still shows this color for a few seconds during login.  What gives?  Have I done something wrong?  I found some threads on the net but nothing really helpful.  I'm not about to tear into some config files that tell me in the intro not to modify this by hand.
Please help.  down with brown   :guitar:

---

### Post by Takster on 2007-12-13
Open:

```
sudo gedit /etc/gdm/PreSession/Default
```

Then here:

```
if [ "x$BACKCOLOR" = "x" ]; then
BACKCOLOR="#dab082"
```

Make it:

```

if [ "x$BACKCOLOR" = "x" ]; then
BACKCOLOR="#000000"
```

#000000 (black) or whatever colour you like. :)

---

### Post by phansiizwe on 2007-12-16
Thanks Takster, that works perfectly!

Can this be changed through any GUI setting, else I think this good be a good addition somewhere in the Login Screen settings for instance.

---

### Post by evil_cat on 2007-12-23
Thx although I actually live in Africa i'm actually bored with the brown theme

---

