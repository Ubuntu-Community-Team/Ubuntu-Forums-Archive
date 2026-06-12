---
title: "Theming FF Buttons in Gnome?"
date: 2007-12-28
forum: Desktop Environments
---

### Post by shafin on 2007-12-28
Is there any way to theme buttons in web pages in Gnome?When I converted from windows,this was one of the few things that looked ugly to my eyes.I know KDE can do that,but I want a way for Gnome.
For instance,In Gnome,the buttons in a web page are:
[img]http://img2.freeimagehosting.net/uploads/24377fa804.png[/img]
But in other DEs,they can be themes to match the desktop theme:
[img]http://img2.freeimagehosting.net/uploads/8f85bffcdd.png[/img]

Please help.

---

### Post by Forlong on 2007-12-28
You can either use a pre-version of Firefox3 that supports this or try this:

```
wget http://users.tkk.fi/~otsaloma/art/firefox-form-widgets.tar.gz
```
```
tar -xvzf firefox-form-widgets.tar.gz
```
```
sudo cp /usr/lib/firefox/res/forms.css /usr/lib/firefox/res/forms.css.bak
```
```
cat firefox-form-widgets/res/forms-extra.css | sudo tee --append /usr/lib/firefox/res/forms.css >> /dev/null 
```
```
sudo cp -r firefox-form-widgets/res/form-widgets/ /usr/lib/firefox/res
```
```
rm -r firefox-form-widgets
```

---

### Post by shafin on 2007-12-28
Thanks a lot.

BTW,I think there is a procedure to install FF 3 with a different profile folder,but I cant search the thread,can you help?

---

### Post by Forlong on 2007-12-28
I don't have FF3 installed (I use [Swiftweasel](http://swiftweasel.tuxfamily.org/))
Have a look at the startscript for Firefox, though.

For example, in the version that came with Ubuntu:
```
gedit /usr/bin/firefox
```
There's this variable:
```
MOZ_USER_DIR=".mozilla/firefox"
```
You could change that to whatever you want (you need to be root to do that, of course).
I guess there's something similar in FF3.

---

