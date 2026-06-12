---
title: "Set seamonkey as Gnome default browser"
date: 2006-02-06
forum: Desktop Environments
---

### Post by el_Salmon on 2006-02-06
Hi,

I'm a Seamonkey user since a few days but I cannot set Seamonkey as default browser in Gnome. If I set "seamonkey %s" as Default Browser in Preferences Applications of Gnome, when I click on any link at client e-mail or Gaim it doesn't response. However, if I choose Firefox in Preferences Applications list as default browser, it launchs Firefox.

---

### Post by art on 2006-02-06
maybe if you set it to full path to seamonkey it will work. In command line type 
**which seamonkey **
and use this instead.
HTH

---

### Post by el_Salmon on 2006-02-06
Thank you, but the problem is that it works fine only if I set "Launch in terminal". So it raises a terminal every time I click in a URL.

---

### Post by emarkay on 2006-10-12
Any further information - same problem here.

---

### Post by emarkay on 2006-10-13
Posted "here" and "there" - so far no concrete solution...

[http://forums.mozillazine.org/viewtopic.php?p=2536809#2536809](http://forums.mozillazine.org/viewtopic.php?p=2536809#2536809)

---

### Post by Frak on 2006-10-13
Do you have a link of it leading to \ like firefox does?

---

### Post by dannyboy79 on 2006-10-13
what about setting it inside system, prefs, preferred apps? there is a web browser tab in there and it currently states gnome-www-browser %s for mine so I am not sure what this means but I can tell you that the default browser on my sytem is firefox.

---

### Post by emarkay on 2006-10-16
I just deleted FF - We'll see if that solves the problem... :)

---

### Post by el_Salmon on 2006-10-16
Is a joke? :-k

---

### Post by emarkay on 2006-10-16
> **el_Salmon said:**
> Is a joke? :-k

Um, is what a joke?

I prefer SM and loathe FF and want to have SM be my preferred browser.

---

### Post by emarkay on 2006-10-16
However uninstalling FF breaks a few things in Ubuntu - will continue to investigate.

---

### Post by neverping on 2008-01-18
Very simple, people! I was able to figure myself!

Just make a symbolic link to the SeaMonkey binary. Which mean:

sudo ln -s /usr/local/seamonkey/seamonkey /usr/bin/seamonkey

Then, open "System" and then "application preferences" and change from "firefox" to "seamonkey".

I rule! :)

:popcorn: :popcorn:

---

