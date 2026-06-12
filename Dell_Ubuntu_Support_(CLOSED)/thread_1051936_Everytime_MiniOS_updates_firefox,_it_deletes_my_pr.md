---
title: "Everytime MiniOS updates firefox, it deletes my profile."
date: 2009-01-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by skroops on 2009-01-27
Whenever there is a firefox3 update, all of my settings are deleted.  Saved passwords, search history etc.  It also resets my homepage to the default yahoo crap and reenables the toolbar, and kills my adblock plus config.

I've unchecked the yahoo toolbar in the package manager already, but why would it delete all my config?

Anyone have an idea of how to protect it?

---

### Post by ugm6hr on 2009-01-27
This is because Dell made a mistake with their 1st FF update, and then made another when trying to "fix" the first error.

It should (hopefully) not happen again.

Your old profiles are still in your ~/.mozilla folder, just renamed (probably to "web browser.bak"

To remove the Yahoo toolbar:
```
sudo apt-get remove yahoo-toolbar-extension
```

---

### Post by Talon2 on 2009-01-28
> **ugm6hr said:**
> 

To remove the Yahoo toolbar:
```
sudo apt-get remove yahoo-toolbar-extension
```

That is good information.  Something else I would like to know is:

How do I get the Bookmark Toolbar to show?

---

### Post by ugm6hr on 2009-01-28
> **Talon2 said:**
> How do I get the Bookmark Toolbar to show?

View -> Toolbars -> Bookmarks Toolbar

---

### Post by Talon2 on 2009-01-28
> **ugm6hr said:**
> View -> Toolbars -> Bookmarks Toolbar

Thank you sir.  Just what I needed.

I'd buy you a pint but we have a distance problem.

Talon2
USA

---

### Post by ugm6hr on 2009-01-29
> **Talon2 said:**
> I'd buy you a pint but we have a distance problem.


No worries.

I'll take you up on the offer when I'm next in the neighbourhood ;)

---

### Post by skroops on 2009-01-30
Would mark as solved but can't find the option.  Thanks!

---

