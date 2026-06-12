---
title: "firefox automatically minimizes"
date: 2006-01-10
forum: Desktop Environments
---

### Post by slrafal on 2006-01-10
I don't know why, but everytime I delete a message or click on a link in gmail for example, firefox becomes a small window. Is there a setting I'm missing somewhere?

---

### Post by orbit on 2006-01-10
I have the same problem.  I'm using Mozilla's official 1.5 build:
    Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8) Gecko/20051111 Firefox/1.5

(that's "1.8" followed by a right parenthesis, not a smily face.)

orbit

---

### Post by slrafal on 2006-01-11
mine is the same version? Anybody have any ideas? Please, this is really starting to piss the hell out of me.

---

### Post by orbit on 2006-01-12
I tried using firefox in safemode to disable any extensions that could be causing a problem (ie greasemonkey).  It still did the same thing while in safemode.  I also tried using Windows at school.  It does the same thing.  So this is a gmail or firefox problem.

---

### Post by Sef on 2006-01-13
I would say that the problem lies with firefox since I use gmail in Opera, and don't have that problem.

---

### Post by Thirsteh on 2006-01-13
I'm using the mozilla-firefox that comes with Ubuntu (1.0.7) and am not having any problems whatsoever.

---

### Post by orbit on 2006-01-14
There is a bug filed in Bugzilla : [https://bugzilla.mozilla.org/show_bug.cgi?id=319819](https://bugzilla.mozilla.org/show_bug.cgi?id=319819)
There is a workaround:
1) *Edit > Preferences > Content*
2) Click the JavaScritp *Advanced *button
3) Uncheck *Move or resize existing windows*

---

### Post by Maelgwyn on 2006-01-14
[quote=orbit]There is a bug filed in Bugzilla : [https://bugzilla.mozilla.org/show_bug.cgi?id=319819]("https://bugzilla.mozilla.org/show_bug.cgi?id=319819")
There is a workaround:
1) *Edit > Preferences > Content*
2) Click the JavaScritp *Advanced *button
3) Uncheck *Move or resize existing windows*[/quote]

Heh I was actually going to say that I did that just to see if it changed anything (I didn't think to check bugzilla), and it appears to work fine!

Although I don't have my browser winder fully maximised anymore, as I kept slipping into other desktops! :-\"

---

