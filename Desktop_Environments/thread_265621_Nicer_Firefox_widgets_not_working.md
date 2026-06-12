---
title: "Nicer Firefox widgets not working"
date: 2006-09-26
forum: Desktop Environments
---

### Post by lwr on 2006-09-26
Hi,

I'm trying to make the radio buttons, forms, button etc. look a bit nicer in Firefox. I usually use [this guide]("http://http://www.ubuntuforums.org/showpost.php?p=520822&postcount=2"), but it seems that the package is no longer there or the server is down. Does anyone have the package saved on their computer, or can you point me to something that will do something similar. 

Thanks for your help.

---

### Post by Gotterdammerung on 2006-09-26
try looking for a new one here: [https://addons.mozilla.org/firefox/themes/](https://addons.mozilla.org/firefox/themes/)

---

### Post by wipet on 2006-09-26
> **lwr said:**
> Hi,

I'm trying to make the radio buttons, forms, button etc. look a bit nicer in Firefox. I usually use [this guide]("http://http://www.ubuntuforums.org/showpost.php?p=520822&postcount=2"), but it seems that the package is no longer there or the server is down. Does anyone have the package saved on their computer, or can you point me to something that will do something similar. 

Thanks for your help.
You can find the package here:
[http://users.tkk.fi/~otsaloma/art/firefox-form-widgets.tar.gz](http://users.tkk.fi/~otsaloma/art/firefox-form-widgets.tar.gz)
To install, just follow the same instruction, replacing "firefox-form-widgets-ots" by "firefox-form-widgets".
Worked for me.

---

### Post by lwr on 2006-09-27
Thanks wipet. That works perfectly. For anyone interested, the code to type to use this particular package is as follows (adapted from ow50's guide):

```

wget http://users.tkk.fi/~otsaloma/art/firefox-form-widgets.tar.gz
tar -xvzf firefox-form-widgets.tar.gz
sudo cp /usr/lib/mozilla-firefox/res/forms.css /usr/lib/mozilla-firefox/res/forms.css.bak
cat firefox-form-widgets/res/forms-extra.css | sudo tee --append /usr/lib/mozilla-firefox/res/forms.css > /dev/null
sudo cp -r firefox-form-widgets/res/form-widgets /usr/lib/mozilla-firefox/res
rm -rf firefox-form-widgets

```
Thanks again for your help.

---

### Post by lwr on 2007-01-03
I'm getting increasingly lazy, so here's a nice one liner:
```
wget http://users.tkk.fi/~otsaloma/art/firefox-form-widgets.tar.gz && tar -xvzf firefox-form-widgets.tar.gz && sudo cp /usr/lib/mozilla-firefox/res/forms.css /usr/lib/mozilla-firefox/res/forms.css.bak && cat firefox-form-widgets/res/forms-extra.css | sudo tee --append /usr/lib/mozilla-firefox/res/forms.css > /dev/null && sudo cp -r firefox-form-widgets/res/form-widgets /usr/lib/mozilla-firefox/res && rm -rf firefox-form-widgets

```

---

### Post by Ev.Eli on 2007-01-03
For me the folder has moved to /usr/lib/firefox (no mozilla). Here's the fixed one-liner.
```
wget http://users.tkk.fi/~otsaloma/art/firefox-form-widgets.tar.gz && tar -xvzf firefox-form-widgets.tar.gz && sudo cp /usr/lib/firefox/res/forms.css /usr/lib/firefox/res/forms.css.bak && cat firefox-form-widgets/res/forms-extra.css | sudo tee --append /usr/lib/firefox/res/forms.css > /dev/null && sudo cp -r firefox-form-widgets/res/form-widgets /usr/lib/firefox/res && rm -rf firefox-form-widgets
```
I love these widgets. :)

---

### Post by delfick on 2007-01-10
> **lwr said:**
> I'm getting increasingly lazy, so here's a nice one liner:
```
wget http://users.tkk.fi/~otsaloma/art/firefox-form-widgets.tar.gz && tar -xvzf firefox-form-widgets.tar.gz && sudo cp /usr/lib/mozilla-firefox/res/forms.css /usr/lib/mozilla-firefox/res/forms.css.bak && cat firefox-form-widgets/res/forms-extra.css | sudo tee --append /usr/lib/mozilla-firefox/res/forms.css > /dev/null && sudo cp -r firefox-form-widgets/res/form-widgets /usr/lib/mozilla-firefox/res && rm -rf firefox-form-widgets

```

lol :D

thnx for the one-liner :D

---

### Post by Contrid on 2007-01-22
> **lwr said:**
> I'm getting increasingly lazy, so here's a nice one liner:
```
wget http://users.tkk.fi/~otsaloma/art/firefox-form-widgets.tar.gz && tar -xvzf firefox-form-widgets.tar.gz && sudo cp /usr/lib/mozilla-firefox/res/forms.css /usr/lib/mozilla-firefox/res/forms.css.bak && cat firefox-form-widgets/res/forms-extra.css | sudo tee --append /usr/lib/mozilla-firefox/res/forms.css > /dev/null && sudo cp -r firefox-form-widgets/res/form-widgets /usr/lib/mozilla-firefox/res && rm -rf firefox-form-widgets

```

Awesome!!!
This is the first time that I've managed to get this to work.
Thanks for the code. ;)

---

### Post by mexlinux on 2007-01-22
Great! now firefox looks more like konqueror

---

