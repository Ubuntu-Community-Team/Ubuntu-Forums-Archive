---
title: "Beagle and accents"
date: 2006-09-09
forum: Desktop Environments
---

### Post by Amt0571 on 2006-09-09
Hello,

I'm spanish, and in spanish, as you will know there are accents (or tildes, I'm not sure how it's called in english).

Yesterday I installed Beagle, which works fantastic, nevertheless, it gives me an error everytime I try to open a file with an accent on it.

For example, If I search for "Anglès" on the Deskbar, it returns me a document called "Anglès.odt", I click on it, and I get an error that says that a coding error has been detected and the following details:

Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/deskbar/DeskbarApplet.py", line 97, in on_match_selected
    match.action(text)
  File "/usr/lib/deskbar-applet/handlers/beagle-live.py", line 188, in action
    action(self.result)
  File "/usr/lib/deskbar-applet/handlers/beagle-live.py", line 78, in <lambda>
    "action": lambda d: gnome.url_show(d["uri"]),
GError: El lugar o el archivo no se pudo encontrar.


On the other hand, if I search the file directly in Beagle, when I click on the file, Openoffice opens, but tells me the file doesn't exist. If I doubleclick the file in nautilus, it works without problems.

Any help?


Thanks!

---

