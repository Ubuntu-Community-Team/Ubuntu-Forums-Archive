---
title: "Changing Bookmarks toolbar font to light color."
date: 2009-05-04
forum: General Help
---

### Post by EC120 on 2009-05-04
New Ubuntu user here. I'm learning slowly, but I have a question about changing Bookmarks Toolbar font color to light from dark, so it doesn't blend with the background.
I'm using GNOME and Dust theme. My Bookmarks toolbar is dragged to Menu area and that's creating a problem. Would it be best to use custom style for stylish or a modified Firefox theme? Customizing Dust theme in Ubuntu doesn't produce results I'd like. Could someone give me ideas, point me in right direction? Thank you.

[IMG]http://www.picpower.net/images/ftbd9yn8a6pubzs91ao5.jpg[/IMG]

[IMG]http://www.picpower.net/images/qiio9kn1rfhf1tv2ng0.jpg[/IMG]

[IMG]http://www.picpower.net/images/s0zn7o3do53v7xzylr.jpg[/IMG]

---

### Post by uncle_frank on 2009-05-24
does anyone know how to change this because i would like to know too?

---

### Post by Legace on 2009-05-24
Best way is to use another Firefox theme..

- [https://addons.mozilla.org/en-US/firefox/search?q=ubuntu&cat=2%2C0](https://addons.mozilla.org/en-US/firefox/search?q=ubuntu&cat=2%2C0)
- [https://addons.mozilla.org/en-US/firefox/search?q=gnome&cat=2%2C0](https://addons.mozilla.org/en-US/firefox/search?q=gnome&cat=2%2C0)

---

### Post by captainmnb on 2009-06-09
Just fixed this problem for myself.  You need to edit your Firefox profile's userChrome.css.  You may want to create a backup of your profile before doing this, but if you follow the instructions nothing bad should happen.

userChrome.css doesn't exist by default, although there are example files.  Create a file called userChrome.css in ~/.mozilla/firefox/xxxxxxxx.default/chrome (where the xxxxxxxx is whatever random string of characters your profile is named).  Add to that file:
```
@namespace url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);

/* Make Bookmarks Toolbar text light for a dark theme */
toolbarbutton.bookmark-item .toolbarbutton-text {color:#ffffff}
toolbarbutton.bookmark-item:hover .toolbarbutton-text {color:#000000}
```
That'll make the text white and the text color when hovering to black, but you can change #ffffff and #000000 to whatever hex color codes you want.

Then just save the file and restart Firefox.

Edit: Forgot the namespace line.
Edit2: Improved code to make the hover text readable.

---

### Post by teet on 2010-02-05
Wow thanks, this worked great.

I too drag my bookmark toolbar up to the menubar (to save a little vertical screen real estate).  Unfortunately, most themes aren't designed for this and it makes it really hard to read my bookmarks when using a dark theme.

-teet

---

### Post by autonomy on 2010-05-03
thanks

---

### Post by prosist on 2010-08-29
worked great. thanks.

---

