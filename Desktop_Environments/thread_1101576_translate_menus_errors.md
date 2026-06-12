---
title: "translate_menus errors"
date: 2009-03-20
forum: Desktop Environments
---

### Post by fusa on 2009-03-20
Whenever I install something I receive the following error: "Script /etc/menu-methods/translate_menus returned error status 1."  Installation completes, but I would like to correct this error if possible.

---

### Post by fusa on 2009-03-22
Does anyone have any idea what could cause this?

---

### Post by jsday187 on 2009-06-05
Me too. WTF!! Its pissing me off. It basically lists every item in my menu like this:
```

/usr/share/menu/xarchiver: line 1: syntax error near unexpected token xarchiver'
/usr/share/menu/xarchiver: line 1: `?package(xarchiver):needs="X11" section="Applications/File Management"\'
Execution of /usr/share/menu/xarchiver generated no output or returned an error.

```Starting with this:
```

Processing triggers for menu ...

```Follwed by the same:
```

update-menus[2998]: Script /etc/menu-methods/translate_menus returned error status 1.

```at the end. You too?? 
Other than that though nothing appears to be wrong with anything as far as I can tell at the moment.
It happens when I install or remove a package with apt-get in the terminal as well as on package upgrades I think... I'll have to check that next time I upgrade one. Anyone have a clue what's causing this?
****

---

