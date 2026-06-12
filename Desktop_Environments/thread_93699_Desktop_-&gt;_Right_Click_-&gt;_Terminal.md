---
title: "Desktop -&gt; Right Click -&gt; Terminal?"
date: 2005-11-22
forum: Desktop Environments
---

### Post by lasermike026 on 2005-11-22
Where did you it go and I want it back.  How do I get the terminal back to my Desktop -> Right Click menu?

Thanks in advance,
Mike

---

### Post by kperkins on 2005-11-22
install nautilus-open-terminal using Synaptic or apt-get

---

### Post by lasermike026 on 2005-11-22
Shouldn't I just have to update a XML file or something?  That seems alittle extreme just to add Terminal to my desktop right click.

---

### Post by lasermike026 on 2005-11-22
Geewiz, look at all this stuff.

$ dpkg -L nautilus-open-terminal
/.
/usr
/usr/share
/usr/share/locale
/usr/share/locale/bg
/usr/share/locale/bg/LC_MESSAGES
/usr/share/locale/bg/LC_MESSAGES/nautilus-open-terminal.mo
/usr/share/locale/ca
/usr/share/locale/ca/LC_MESSAGES
/usr/share/locale/ca/LC_MESSAGES/nautilus-open-terminal.mo
/usr/share/locale/cs
/usr/share/locale/cs/LC_MESSAGES
/usr/share/locale/cs/LC_MESSAGES/nautilus-open-terminal.mo
/usr/share/locale/da
/usr/share/locale/da/LC_MESSAGES
/usr/share/locale/da/LC_MESSAGES/nautilus-open-terminal.mo
/usr/share/locale/de
/usr/share/locale/de/LC_MESSAGES
/usr/share/locale/de/LC_MESSAGES/nautilus-open-terminal.mo
/usr/share/locale/en_CA
/usr/share/locale/en_CA/LC_MESSAGES
/usr/share/locale/en_CA/LC_MESSAGES/nautilus-open-terminal.mo
/usr/share/locale/en_GB
/usr/share/locale/en_GB/LC_MESSAGES
/usr/share/locale/en_GB/LC_MESSAGES/nautilus-open-terminal.mo
/usr/share/locale/es
/usr/share/locale/es/LC_MESSAGES
/usr/share/locale/es/LC_MESSAGES/nautilus-open-terminal.mo
/usr/share/locale/fi
/usr/share/locale/fi/LC_MESSAGES
/usr/share/locale/fi/LC_MESSAGES/nautilus-open-terminal.mo
/usr/share/locale/fr
/usr/share/locale/fr/LC_MESSAGES
/usr/share/locale/fr/LC_MESSAGES/nautilus-open-terminal.mo
/usr/share/locale/gl
/usr/share/locale/gl/LC_MESSAGES
/usr/share/locale/gl/LC_MESSAGES/nautilus-open-terminal.mo
/usr/share/locale/hu
/usr/share/locale/hu/LC_MESSAGES
/usr/share/locale/hu/LC_MESSAGES/nautilus-open-terminal.mo
/usr/share/locale/it
/usr/share/locale/it/LC_MESSAGES
/usr/share/locale/it/LC_MESSAGES/nautilus-open-terminal.mo
/usr/share/locale/ja
/usr/share/locale/ja/LC_MESSAGES
/usr/share/locale/ja/LC_MESSAGES/nautilus-open-terminal.mo
/usr/share/locale/nl
/usr/share/locale/nl/LC_MESSAGES
/usr/share/locale/nl/LC_MESSAGES/nautilus-open-terminal.mo
/usr/share/locale/pa
/usr/share/locale/pa/LC_MESSAGES
/usr/share/locale/pa/LC_MESSAGES/nautilus-open-terminal.mo
/usr/share/locale/pt_BR
/usr/share/locale/pt_BR/LC_MESSAGES
/usr/share/locale/pt_BR/LC_MESSAGES/nautilus-open-terminal.mo
/usr/share/locale/rw
/usr/share/locale/rw/LC_MESSAGES
/usr/share/locale/rw/LC_MESSAGES/nautilus-open-terminal.mo
/usr/share/locale/sk
/usr/share/locale/sk/LC_MESSAGES
/usr/share/locale/sk/LC_MESSAGES/nautilus-open-terminal.mo
/usr/share/locale/sr
/usr/share/locale/sr/LC_MESSAGES
/usr/share/locale/sr/LC_MESSAGES/nautilus-open-terminal.mo
/usr/share/locale/sr@Latn
/usr/share/locale/sr@Latn/LC_MESSAGES
/usr/share/locale/sr@Latn/LC_MESSAGES/nautilus-open-terminal.mo
/usr/share/locale/sv
/usr/share/locale/sv/LC_MESSAGES
/usr/share/locale/sv/LC_MESSAGES/nautilus-open-terminal.mo
/usr/share/locale/zh_CN
/usr/share/locale/zh_CN/LC_MESSAGES
/usr/share/locale/zh_CN/LC_MESSAGES/nautilus-open-terminal.mo
/usr/share/locale/zh_TW
/usr/share/locale/zh_TW/LC_MESSAGES
/usr/share/locale/zh_TW/LC_MESSAGES/nautilus-open-terminal.mo
/usr/share/doc
/usr/share/doc/nautilus-open-terminal
/usr/share/doc/nautilus-open-terminal/README
/usr/share/doc/nautilus-open-terminal/TODO
/usr/share/doc/nautilus-open-terminal/AUTHORS
/usr/share/doc/nautilus-open-terminal/copyright
/usr/share/doc/nautilus-open-terminal/changelog.gz
/usr/share/doc/nautilus-open-terminal/NEWS.gz
/usr/share/doc/nautilus-open-terminal/changelog.Debian.gz
/usr/lib
/usr/lib/nautilus
/usr/lib/nautilus/extensions-1.0
/usr/lib/nautilus/extensions-1.0/libnautilus-open-terminal.so

---

### Post by kperkins on 2005-11-22
The whole thing takes up ~370KB when installed. That's how to do it, if you don't like the answer, don't bitch about it, find another one.

---

### Post by canadianwriterman on 2005-11-22
While he may not have positioned his comment very nicely, kperkins is right. The nautilus-open-terminal package is quite small, despite having a number of components. I installed it some time ago and it works great.

---

### Post by kperkins on 2005-11-22
[QUOTE=canadianwriterman]While he may not have positioned his comment very nicely, kperkins is right. The nautilus-open-terminal package is quite small, despite having a number of components. I installed it some time ago and it works great.[/QUOTE]
You're absolutely right that I didn't position my answer very well (that's a great phrase, by the way, is it a Canadian colluquillism?), but neither did the OP, when he  took my simple, very workable answer, and made 2 posts, basically, trying to prove how bad my answer was, in the time it would have taken him to instal it, and get using it.
If he has a problem with the solution, maybe asking the devs about why it isn't implemented by default would be in order.

---

