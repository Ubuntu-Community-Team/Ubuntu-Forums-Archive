---
title: "What installs QT 4?"
date: 2009-03-04
forum: General Help
---

### Post by brandon88tube on 2009-03-04
I wanted to know what installs QT 4 because all of a sudden I have it installed on my desktop and I never went out of my way to install it. I wanted to know if it possibly installs with VirtualBox because that is the only thing that I just recently installed. Other then that I would have to say I have no idea and maybe I got compromised, though I doubt it.

---

### Post by kestrel1 on 2009-03-04
No, it wont be VirtualBox.

EDIT: Ignore this!!!!!

---

### Post by Tibuda on 2009-03-04
> **kestrel1 said:**
> No, it wont be VirtualBox.

You are wrong, VirtualBox uses Qt.

---

### Post by brandon88tube on 2009-03-04
So, is it VirtualBox or not? Getting mixed messages here.

---

### Post by Slim Odds on 2009-03-04
> **brandon88tube said:**
> So, is it VirtualBox or not? Getting mixed messages here.

A number of different application require Qt (lots of applications require lots of libraries).

Have you tried searching in Synaptic?

---

### Post by kestrel1 on 2009-03-04
> **danielrmt said:**
> You are wrong, VirtualBox uses Qt.
Sorry, just looked & found it does. My mistake.
Must have been a bad install, because VirtualBox has never put QT4 on the desktop for me.

---

### Post by lykwydchykyn on 2009-03-04
> **brandon88tube said:**
> I wanted to know what installs QT 4 because all of a sudden I have it installed on my desktop and I never went out of my way to install it. I wanted to know if it possibly installs with VirtualBox because that is the only thing that I just recently installed. Other then that I would have to say I have no idea and maybe I got compromised, though I doubt it.

QT4 is a programming library, not a program; so I'm not sure what you mean it's on your desktop.  Is it a shortcut?  A tarball?

---

### Post by brandon88tube on 2009-03-04
Oops I said desktop when I meant under System > Preferences there is Qt 4 Settings.

---

### Post by lykwydchykyn on 2009-03-04
Do this:
 - open synaptic
 - click search
 - select "dependencies" from the dropdown list
 - enter "qt4" or "libqt4" in the search field.
 - look for things in the search results with green boxes next to them.

---

### Post by Rallg on 2009-03-04
QT4 is a set of program-support libraries, and it has its own interface. It is good stuff, not a virus. Probably the only reason you might not want it installed free is if you are using it to develop your own programs for later commercial use, because there are different licenses for paid commercial users and free open-source users. In that case, you would need to be using the paid license version.

QT4 is a product of Trolltech. You can look them up on the Internet, if you wish.

---

### Post by Slim Odds on 2009-03-04
> **Rallg said:**
> QT4 is a set of program-support libraries, and it has its own interface. It is good stuff, not a virus. Probably the only reason you might not want it installed free is if you are using it to develop your own programs for later commercial use, because there are different licenses for paid commercial users and free open-source users. In that case, you would need to be using the paid license version.

QT4 is a product of Trolltech. You can look them up on the Internet, if you wish.

Actually, they just released version 4.5 today, which has a new license (LGPL).  :guitar:

---

### Post by Tibuda on 2009-03-04
> **brandon88tube said:**
> So, is it VirtualBox or not? Getting mixed messages here.

Yes, VirtualBox requires Qt to run, so your package manager (Synaptic/apt-get) installed it.

---

### Post by Rallg on 2009-03-04
Thanks, "Slim Odds," for mentioning QT4.5. Also, I notice that Trolltech now has a different business name, or partnership, or whatever. :)

---

### Post by brandon88tube on 2009-03-04
Thanks for the replies, I didn't think it was a virus or anything, I just wanted to know how I had gotten it and it turns out that it was probably from VirtualBox.

---

### Post by Slim Odds on 2009-03-04
> **Rallg said:**
> Thanks, "Slim Odds," for mentioning QT4.5. Also, I notice that Trolltech now has a different business name, or partnership, or whatever. :)

They are now owned by Nokia

---

### Post by kestrel1 on 2009-03-05
> **brandon88tube said:**
> Oops I said desktop when I meant under System > Preferences there is Qt 4 Settings.

That is normal & it would have been VBox that put it there.

---

### Post by snova on 2009-03-05
> **brandon88tube said:**
> Oops I said desktop when I meant under System > Preferences there is Qt 4 Settings.

If you wish to remove it, it was installed by the **qt4-qtconfig** package.

---

### Post by andrew.46 on 2009-03-06
Hi,

There is a nice commandline method:

```
andrew@skamandros:~$ [COLOR="Red"]**apt-cache showpkg libqtcore4 | grep -i virtualbox**[/COLOR]
  virtualbox-ose,libqtcore4 4.5.0~+rc1
```


or the full list:

```
apt-cache showpkg libqtcore4 > qt4
```

Andrew

---

