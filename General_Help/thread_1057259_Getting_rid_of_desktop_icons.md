---
title: "Getting rid of desktop icons"
date: 2009-02-01
forum: General Help
---

### Post by u'b'u'n't'u on 2009-02-01
I don't know how I did it but somehow there are four icons on the desktop that I cannot delete. They are:

Home
Documents
Network
Trash

(I'm a n00b)

---

### Post by taurus on 2009-02-01
Open a terminal and type

Applications -> Accessories -> Terminal
```
gconfig-editor
```
Expand the apps tab, then nautilus -> desktop and remove the check mark for volumes_visible.

---

### Post by u'b'u'n't'u on 2009-02-01
Wow this website is amazing. after 2 minutes i get my answer 
THANKYOUTHANKTOU

---

### Post by sidious1741 on 2009-07-21
> **taurus said:**
> Open a terminal and type

Applications -> Accessories -> Terminal
```
gconfig-editor
```
Expand the apps tab, then nautilus -> desktop and remove the check mark for volumes_visible.

I'm using gnome (Jaunty) and gconfig-editor doesn't exist for me.

---

### Post by michy99 on 2009-07-21
If it is not installed, you can install it.```
sudo apt-get install gconfig-editor
```

---

### Post by scouser73 on 2009-07-21
> **u'b'u'n't'u said:**
> I don't know how I did it but somehow there are four icons on the desktop that I cannot delete. They are:

Home
Documents
Network
Trash

(I'm a n00b)

Another way is to install Ubuntu Tweak and disable them from showing on the desktop, also Ubuntu Tweak has a load of software that you may be interested in, and this can be found [[COLOR="Red"]**Here**[/COLOR]]("http://ubuntu-tweak.com/")

---

### Post by hyperdude111 on 2009-07-21
Did you install ubuntu-tweak ? 

It gives you an option to show and hide some/all desktop icons with a user friendly GUI.

---

