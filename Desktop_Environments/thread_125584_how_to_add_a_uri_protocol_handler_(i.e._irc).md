---
title: "how to add a uri protocol handler? (i.e. irc://)"
date: 2006-02-04
forum: Desktop Environments
---

### Post by quonsar on 2006-02-04
is it possible to add your own protocol and specify the program that handles it, for example the way gAIM makes aim:// links work and some irc clients make irc:// links work? can it be done by hand? what gets edited?

---

### Post by quonsar on 2006-02-04
*thud* *bonk*

---

### Post by quonsar on 2006-02-04
*bonk*

---

### Post by ardchoille on 2006-02-04
This is a very good question. I'd like to learn how to do this also.

---

### Post by quonsar on 2006-02-06
*bump*

---

### Post by twisted_steel on 2006-02-06
Here's an example for IRC:
```
$ gconftool-2 --set --type=string /desktop/gnome/url-handlers/irc/command 'xchat "%s"'
$ gconftool-2 --set --type=bool /desktop/gnome/url-handlers/irc/enabled true
$ gconftool-2 --set --type=bool /desktop/gnome/url-handlers/irc/need-terminal false
``` There are a few more available on this site (not in english, but self-explanatory): [http://bolgo.cent.uji.es/node/9]("http://bolgo.cent.uji.es/node/9")

---

### Post by mcduck on 2006-02-06
If you want to do it for Firefox, type about:config in the address bar, and then right-click on the page, select 'new' and 'string'  to create a new key.  Set Preference Name to 'network.protocol-handler.app.irc' and Value to 'xchat'. You might need full path to xchat, I'm not sure abot that as I have only done this for lastfm://

---

### Post by quonsar on 2006-02-06
very cool! thanks for the replies!

with xchat 2.6.0 i found the configuration string needs to be
```
gconftool-2 --set --type=string /desktop/gnome/url-handlers/irc/command 'xchat --url="%s"'
```

---

### Post by uberushaximus on 2007-11-02
> **quonsar said:**
> very cool! thanks for the replies!

with xchat 2.6.0 i found the configuration string needs to be
```
gconftool-2 --set --type=string /desktop/gnome/url-handlers/irc/command 'xchat --url="%s"'
```

add the --existing flag to prevent messy window opening

---

