---
title: "&lt;shift&gt;&lt;backspace&gt; hotkey"
date: 2007-06-02
forum: Desktop Effects &amp; Customization
---

### Post by 213374U on 2007-06-02
I'm running Feisty with Beryl on a Dimension 4600 with ATI Graphics Card. <shift><backspace> hotkey ends the session and exits to the login screen. How do I get rid of this? Can't find it in any of the Hotkey menus.

---

### Post by NilsE on 2007-06-02
All <shift><backspace> does for me is take me to the bottom of any open window.  This is what it is supposed to do.

<ctrl><alt><backspace> does what you described.

Sounds like you may have the wrong keyboard driver installed.  Check into that.

Also, does it do it before you installed Beryl?

---

### Post by 213374U on 2007-06-02
Well I got beryl up and running like three days after I installed Feisty so I'm not sure. I'm gonna try the <alt><ctrl><backspace> command and see what it does though.

---

### Post by 213374U on 2007-06-03
yup, <ctrl><alt><backspace> does the exact same thing as <shift><backspace> for me. So nobody knows how to get rid of this?

---

### Post by 213374U on 2007-06-04
bump

---

### Post by danhm on 2007-06-05
Add
```
xmodmap /usr/share/xmodmap/xmodmap.us
```
to your startup (System->Preferences->Sessions->Startup Programs->New).

You'll have to change it if you don't live in the US/don't use a US keyboard, but that should get the job done. Also, you'll probably have to restart X (or just paste that into a command prompt).

---

