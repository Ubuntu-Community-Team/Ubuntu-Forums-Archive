---
title: "firefox first click highlights address bar?"
date: 2006-06-08
forum: Desktop Environments
---

### Post by mluu510 on 2006-06-08
how come in linux, when i first click on firefox's address bar, it doesn't highlight my whole url? it gets pretty annoying to have to double click it. most of the time, i click on my address bar to replace the whole url or to copy it completely. is there a tweak to fix this?

---

### Post by bryanlking on 2006-06-08
Easy fix:

Type in about:config in the address bar to bring up the configuration options page.

search for browser.urlbar.clickSelectsAll

Change the boolean value from false to true (double click ought to do it)

Close that page and you're done.

BK

---

### Post by angkor on 2006-06-08
type about:config in the url bar

Search for 'urlbar' and set:

browser.urlbar.clickSelectsAll to 'true'



EDIT: I'm sooooo slooooooooow tonghit. :)

---

