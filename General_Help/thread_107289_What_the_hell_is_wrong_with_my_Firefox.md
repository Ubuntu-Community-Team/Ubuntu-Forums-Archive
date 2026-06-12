---
title: "What the hell is wrong with my Firefox?"
date: 2005-12-22
forum: General Help
---

### Post by XtremeGamer99 on 2005-12-22
[http://xgamer.insder.com/bleh/Screenshot-1.png](http://xgamer.insder.com/bleh/Screenshot-1.png)

0_o

I don't knw what I did. I downloaded FF 1.5, installed that into my /usr , installed it, and ran it. Then I tried to use my 1.0.7 version, and this is what happened. I did a complete removal of firefox through the Synaptic Package Manager, and installed it again.

What's wrong? v_v

EDIT: Nevermind. I just have to run 1.5 now (it works).

How do I change my firefox icon down there to run /usr/firefox/firefox.sh?  (I didn't know where else to put it, so I put it in my /usr dir. >_>)

---

### Post by shakin on 2005-12-22
I believe the problem is that you installed 1.5 partially over 1.0.7. I installed 1.5 in /opt/firefox to keep it separate and both work fine.

You can edit /usr/bin/firefox and change the variable values on lines 41 and 42 to point to the new locations. This will make all references to 'firefox' load 1.5.

---

### Post by rcerreto on 2005-12-23
Likely, you're using a theme which is not compatible with 1.5
Try drilling down $HOME/.mozilla/firefox/..
up to finding prefs.js
then edit the file removing any reference to theme(s)
At the next start, Firefox will load the default theme which should run fine.
Afterward you'll be able to change theme looking for something compatible.

---

### Post by REBELinBLUE on 2005-12-23
I had this problem and I've just solved it.

It only happened to me when clicking on links in external applications, for example one someone sent me in Gaim. I found out that the reason for this is that it was loading Firefox 1.0.7 and my theme wasn't compatible with 1.0.7. This is because the preferred browser was "mozilla-firefox" and /usr/bin/mozilla-firefox still pointed to 1.0.7 but /usr/bin/firefox pointed to 1.5 so I simply changed the preferred browser to "firefox" and it works perfectly. Been having this problem since 1.5 was released and it just suddenly came to me today whilst doing something else.

---

