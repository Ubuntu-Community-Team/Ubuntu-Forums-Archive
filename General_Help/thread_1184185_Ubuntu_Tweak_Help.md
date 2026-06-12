---
title: "Ubuntu Tweak Help"
date: 2009-06-10
forum: General Help
---

### Post by biffthemandible on 2009-06-10
I followed the directions on the ubuntu tweak site ([http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)) on how to download tweak for jaunty 9.04. [FONT=monospace]But when i type in 'sudo apt-get install ubuntu tweak' it tells me it can't find the package. I don't know what to do. I imported the key, modified the sources list as instructed, and updated but it still says it can't find the package. [/FONT][COLOR=#0000FF][/COLOR][COLOR=#0000FF][/COLOR]

---

### Post by aesis05401 on 2009-06-10
I don't use that package, but a quick search reveals that you need a hyphen between 'ubuntu' & 'tweak' : 
```

sudo apt-get install ubuntu-tweak

```

Is that just a typo on your posting here or were you leaving out the hyphen when attempting to install?

---

### Post by colau on 2009-06-10
> **biffthemandible said:**
> I followed the directions on the ubuntu tweak site ([http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)) on how to download tweak for jaunty 9.04. [FONT=monospace]But when i type in 'sudo apt-get install ubuntu tweak' it tells me it can't find the package. I don't know what to do. I imported the key, modified the sources list as instructed, and updated but it still says it can't find the package. [/FONT][COLOR=#0000FF][/COLOR][COLOR=#0000FF][/COLOR]
You have to add these lines first in /etc/apt/sources.list
```

deb http://ppa.launchpad.net/tualatrix/ubuntu jaunty main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu jaunty main

```
```

sudo apt-get update
sudo apt-get install ubuntu-tweak

```

---

### Post by jmszr on 2009-06-10
biffthemandible,

If the above doesn't fix it, you can install it from here: [http://www.getdeb.net/search.php?keywords=ubuntu+tweak](http://www.getdeb.net/search.php?keywords=ubuntu+tweak) .

---

### Post by biffthemandible on 2009-06-10
I was leaving out the hyphen. Well that wasn't at all embarrassing. Thank you both

---

