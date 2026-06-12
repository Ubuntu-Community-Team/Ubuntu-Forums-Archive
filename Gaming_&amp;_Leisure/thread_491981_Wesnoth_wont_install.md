---
title: "Wesnoth wont install"
date: 2007-07-04
forum: Gaming &amp; Leisure
---

### Post by ataiger on 2007-07-04
I checked this page
[http://www.wesnoth.org/wiki/CompilingWesnoth](http://www.wesnoth.org/wiki/CompilingWesnoth)

and did what it says.
I unzipped the tar file, did ./configure, make, and sudo make install. (for sure I installed all required packages)

Everything seems fine, except for that the wesnoth doesn't appear under the game menu. Anyone know why?? I'm using a Korean localized version of Feisty.

---

### Post by joselin on 2007-07-04
The easy way... just type:

```
sudo apt-get install wesnoth
```

---

### Post by Steveway on 2007-07-04
Wesnoth is in the repos.
Just open up Synaptic, search for wesnoth and install the right package, no need to compile it yourself.
EDIT: To slow. ^^

---

### Post by ataiger on 2007-07-04
Thanks for the replies.
I just wonder why I can't do it on my own.. ;)

---

### Post by ataiger on 2007-07-04
I checked my synaptic...

wesnoth was installed, but wesnoth-data was not installed. What does this mean?

EDIT:
[http://gaming.gwos.org/e107_plugins/content/content.php?content.6](http://gaming.gwos.org/e107_plugins/content/content.php?content.6)
what does "make checkinstall" mean??

---

### Post by joselin on 2007-07-04
```
$ apt-cache search wesnoth-data
wesnoth-data - data files for Wesnoth

```
I think that can be languages, levels or something like that.

---

### Post by joselin on 2007-07-04
> **ataiger said:**
> 
[http://gaming.gwos.org/e107_plugins/content/content.php?content.6](http://gaming.gwos.org/e107_plugins/content/content.php?content.6)
what does "make checkinstall" mean??

Reading the web, seems that there is an scrip to check that the installation went fine.

Regards

---

