---
title: "Why are buttons ugly in firefox?"
date: 2006-09-29
forum: Desktop Environments
---

### Post by fatsheep on 2006-09-29
Compare these two screenshots.  The first is [www.google.com](www.google.com) being rendered by the konqueror brower.  The second is [www.google.com](www.google.com) being rendered by firefox.  Both screenshots were taken on the same machine under the GNOME desktop environment. 

**Konqueror**
[img]http://img242.imageshack.us/img242/8503/konquerorvc6.png[/img]

**Firefox**
[img]http://img501.imageshack.us/img501/967/firefoxnq6.png[/img]

As you can see buttons look much much nicer in konqueror then firefox.  The same applies to radio buttons and checkboxes.  What I want to know is why this is happening.  On windows buttons looked great on firefox, now they look terrible...

---

### Post by BitTorrentBuddha on 2006-09-29
Give [this](http://ubuntuforums.org/showpost.php?p=520822&postcount=2) a read, it looks really nice. I've attached a screenshot. 
[img]http://img528.imageshack.us/img528/7875/screenshot1gf1.png[/img]

---

### Post by lwr on 2006-09-29
You might find you get a 404 not found error on the method in the previous post. An alternative can be found [here]("http://www.ubuntuforums.org/showpost.php?p=1552206&postcount=4"). As to why this happens, I've no idea. Someone should really get it sorted, so it's nice after a fresh install. You'll need to restart Firefox for the changes to be applied, and I've found you need to fun the script every time Firefox upgrades.

---

### Post by fatsheep on 2006-09-29
> **lwr said:**
> You might find you get a 404 not found error on the method in the previous post. An alternative can be found [here]("http://www.ubuntuforums.org/showpost.php?p=1552206&postcount=4"). As to why this happens, I've no idea. Someone should really get it sorted, so it's nice after a fresh install. You'll need to restart Firefox for the changes to be applied, and I've found you need to fun the script every time Firefox upgrades.

Here are my results:

> 
fatsheep@fatsheep:~$ **wget [http://users.tkk.fi/~otsaloma/art/firefox-form-widgets](http://users.tkk.fi/~otsaloma/art/firefox-form-widgets) .tar.gz**
--17:03:06--  [http://users.tkk.fi/~otsaloma/art/firefox-form-widgets.tar.gz](http://users.tkk.fi/~otsaloma/art/firefox-form-widgets.tar.gz)
           => `firefox-form-widgets.tar.gz'
Resolving users.tkk.fi... 130.233.240.8
Connecting to users.tkk.fi|130.233.240.8|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,132 (3.1K) [application/x-tar]

100%[====================================>] 3,132         --.--K/s

17:03:07 (1.63 MB/s) - `firefox-form-widgets.tar.gz' saved [3132/3132]

fatsheep@fatsheep:~$ **tar -xvzf firefox-form-widgets.tar.gz**
firefox-form-widgets/res/form-widgets/checkbox-checked.png
firefox-form-widgets/res/form-widgets/button.png
firefox-form-widgets/res/form-widgets/checkbox.png
firefox-form-widgets/res/form-widgets/radio-checked.png
firefox-form-widgets/res/form-widgets/droparrow.png
firefox-form-widgets/res/form-widgets/radio.png
firefox-form-widgets/res/forms-extra.css
firefox-form-widgets/AUTHORS
firefox-form-widgets/INSTALL
fatsheep@fatsheep:~$ **sudo cp /usr/lib/mozilla-firefox/res/forms.css /usr/lib/moz illa-firefox/res/forms.css.bak**
Password:
cp: cannot stat `/usr/lib/mozilla-firefox/res/forms.css': No such file or direct ory
fatsheep@fatsheep:~$ **cat firefox-form-widgets/res/forms-extra.css | sudo tee --append /usr/lib/mozilla-firefox/res/forms.css > /dev/null**
Password:
tee: /usr/lib/mozilla-firefox/res/forms.css: No such file or directory
fatsheep@fatsheep:~$ **sudo cp -r firefox-form-widgets/res/form-widgets /usr/lib/mozilla-firefox/res**
fatsheep@fatsheep:~$ **rm -rf firefox-form-widgets**
fatsheep@fatsheep:~$


Unfortunately buttons still look the same.

---

### Post by BitTorrentBuddha on 2006-10-01
You have a different firefox directory, try doing a search for 'firefox' without quotes, it's the folder that's not /usr/bin. For me it's /usr/lib/firefox. That could be a place to look before trying the search.

---

### Post by Josh1 on 2006-10-01
Hi,
I prefer the second one, only because I am use to it. I love simplicity (spelling?), and love the way firefox looks by default.
- Josh

---

### Post by fatsheep on 2006-10-01
> **BitTorrentBuddha said:**
> You have a different firefox directory, try doing a search for 'firefox' without quotes, it's the folder that's not /usr/bin. For me it's /usr/lib/firefox. That could be a place to look before trying the search.

My firefox is located in /usr/local/firefox32 so for me the commands would be like this correct?

> 
wget [http://users.tkk.fi/~otsaloma/art/firefox-form-widgets.tar.gz](http://users.tkk.fi/~otsaloma/art/firefox-form-widgets.tar.gz)
tar -xvzf firefox-form-widgets.tar.gz
sudo cp /usr/local/firefox32/res/forms.css /usr/local/firefox32/res/forms.css.bak
cat firefox-form-widgets/res/forms-extra.css | sudo tee --append /usr/local/firefox32/res/forms.css > /dev/null
sudo cp -r firefox-form-widgets/res/form-widgets /usr/local/firefox32/res
rm -rf firefox-form-widgets


EDIT: Yep worked.  Firefox looks beatiful now. :D

---

