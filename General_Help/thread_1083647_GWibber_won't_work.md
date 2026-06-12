---
title: "GWibber won't work"
date: 2009-03-01
forum: General Help
---

### Post by joey-elijah on 2009-03-01
I installed GWibber - an awesome sounding piece of software that'll save me loading up Adobe Air - yet even though my facebook and twitter account info is entered (and correct) GWibber fetches nothing. 

It does launch but all i get is this window: - 

[IMG]http://img24.imageshack.us/img24/5750/screenshot6png.jpg[/IMG]

If i run if from the terminal i get: -

```

joey@ibex:~$ gwibber
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/gwibber/gwui.py", line 81, in on_click_link
    if not self.link_handler(uri, self) and self.load_externally:
TypeError: link_handler() takes exactly 2 arguments (3 given)
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/gwibber/gwui.py", line 81, in on_click_link
    if not self.link_handler(uri, self) and self.load_externally:
TypeError: link_handler() takes exactly 2 arguments (3 given)
console message: undefined @1046: ReferenceError: Can't find variable: addMessages
console message: undefined @22: ReferenceError: Can't find variable: setGtkConfig
console message: undefined @22: ReferenceError: Can't find variable: setAccountConfig
console message: undefined @838: ReferenceError: Can't find variable: addMessages
console message: undefined @22: ReferenceError: Can't find variable: setGtkConfig
console message: undefined @22: ReferenceError: Can't find variable: setAccountConfig

```

:-k any ideas on how to fix this/what the problem is?

---

### Post by joey-elijah on 2009-03-01
EDIT: oops.

---

### Post by irfan9727 on 2009-03-01
where you downloaded it? I downloaded it from [https://launchpad.net/~gwibber-team/+archive/ppa]("https://launchpad.net/~gwibber-team/+archive/ppa") and it's just work fine. Download the .deb file from there and install it by *just* double-clicking on it.
Note: Don't forget to refresh!

---

### Post by joey-elijah on 2009-03-02
> **irfan9727 said:**
> where you downloaded it? I downloaded it from [https://launchpad.net/~gwibber-team/+archive/ppa]("https://launchpad.net/%7Egwibber-team/+archive/ppa") and it's just work fine. Download the .deb file from there and install it by *just* double-clicking on it.
Note: Don't forget to refresh!

Okay i'll try that. I had gotten it from the repo's. I'd really love this to work!

---

### Post by joey-elijah on 2009-03-02
Sadly that doesn't fix it. I installed all of the deb's available after purging my previous gwibber install. but i still get: -

> Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/gwibber/gwui.py", line 81, in on_click_link
    if not self.link_handler(uri, self) and self.load_externally:
TypeError: link_handler() takes exactly 2 arguments (3 given)
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/gwibber/gwui.py", line 81, in on_click_link
    if not self.link_handler(uri, self) and self.load_externally:
TypeError: link_handler() takes exactly 2 arguments (3 given)
console message: undefined @682: ReferenceError: Can't find variable: addMessages
console message: undefined @22: ReferenceError: Can't find variable: setGtkConfig
console message: undefined @12: ReferenceError: Can't find variable: setAccountConfig
console message: undefined @838: ReferenceError: Can't find variable: addMessages
console message: undefined @22: ReferenceError: Can't find variable: setGtkConfig
console message: undefined @12: ReferenceError: Can't find variable: setAccountConfig


---

### Post by dkruythoff on 2009-03-03
Second that.


Edit:
Ok, downgrading libwebkit to 1.0.1-2ubuntu0.1 did the trick.

---

### Post by joey-elijah on 2009-03-06
Tried all of the suggestions, downgraded my webkit, purged gwibber, installed webkit, installed gwibber, removed gwibber installed hardy version of gwibber... all still nothing!

I get the same errors time and time again. I hope when i upgrade to Juanty it works for me!

---

