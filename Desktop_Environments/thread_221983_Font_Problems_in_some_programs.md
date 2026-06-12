---
title: "Font Problems in some programs"
date: 2006-07-24
forum: Desktop Environments
---

### Post by noumaan on 2006-07-24
Since I installed Dapper I am having trouble with fonts. I have installed fonts like I did in Breezy but these fonts are not appearing in firefox, epiphany and many other programs. I can use these fonts on text editors like leafpad and gedit.

---

### Post by noumaan on 2006-07-25
I have filed a bug report on launchpad. I thought it would be nice to copy paste it here. 

I read plenty of Urdu web pages each day. When I was using Breezy I had no trouble viewing Urdu web pages or editing my files in Urdu. But in Dapper I am having many problems:

[LIST=1]All web browsers totally ignore the Urdu fonts. I have added fonts in .fonts, /usr/share/fonts and fonts:/// folders. Used fc-cache and followed instructions ubuntu-desktop guide many times. but still No browser not even thunderbird would display them.
[*]When I installed microsoft fonts including Tahoma these browsers display Urdu web pages in msfonts because Tahoma is what urdu webmasters use on their pages as the last font option.
[*]I can write in urdu using gEdit which recognizes the Urdu fonts but it is unable to render them properly.
[/LIST]

I have installed
[LIST]
[*]language-support-ur
[*]language-pack-ur
[*]language-pack-ur-base
[*]language-pack-gnome-ur
[*]language-pack-gnome-ur-base
[/LIST]

But I am still unable to read urdu webpages. I tried forcing firefox by adding Urdu fonts in Preferences > Content > fonts & colors > Advanced. I even unchecked the box "allow pages to chose their own fonts". But still firefox wouldn't display these pages in urdu fonts.

Urdu fonts that I am using are:
[LIST][*]Nafees Web Naskh
[http://www.crulp.org/nafeesWebNaskh.html](http://www.crulp.org/nafeesWebNaskh.html)
[*]Urdu Naskh Asiatype
[http://www.bbc.co.uk/urdu/fontinstall/popupwin.shtml](http://www.bbc.co.uk/urdu/fontinstall/popupwin.shtml) to install this font I install it on windows and copy paste it in ubuntu.
[*]Tahoma and msttcorefonts.
[/LIST]

---

### Post by noumaan on 2006-08-20
Made great progress. See [This bug report]("https://launchpad.net/distros/ubuntu/+bug/54091")

---

