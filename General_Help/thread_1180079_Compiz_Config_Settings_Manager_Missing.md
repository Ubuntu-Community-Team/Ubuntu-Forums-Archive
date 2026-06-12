---
title: "Compiz Config Settings Manager Missing"
date: 2009-06-06
forum: General Help
---

### Post by TimHeckman on 2009-06-06
Greetings

The interesting thing is I JUST installed this package for my buddy less than a week ago on his PC.

Now when looking through Synaptic Package Manager I do not see the item there.

I've made sure all repositories are available and have reloaded my sources multiple times.

Was the item removed, or am I missing something?

Thanks for your help.

---

### Post by zika on 2009-06-06
> **TimHeckman said:**
> Greetings

The interesting thing is I JUST installed this package for my buddy less than a week ago on his PC.

Now when looking through Synaptic Package Manager I do not see the item there.

I've made sure all repositories are available and have reloaded my sources multiple times.

Was the item removed, or am I missing something?

Thanks for your help.
compizconfig-settings-manager ... Did You choose Status->All ... ?

---

### Post by Legace on 2009-06-06
Try with Add/Remove.  Type in following in Terminal:
```
/usr/bin/gnome-app-install
```

Select "Show -> All available applications".
Then search for **compiz** and see if you can find it there.

You could manually get the .deb, too: [http://packages.ubuntu.com/jaunty/compizconfig-settings-manager](http://packages.ubuntu.com/jaunty/compizconfig-settings-manager) [for Jaunty]

---

### Post by TimHeckman on 2009-06-06
> **Legace said:**
> Try with Add/Remove.  Type in following in Terminal:
```
/usr/bin/gnome-app-install
```

Select "Show -> All available applications".
Then search for **compiz** and see if you can find it there.

You could manually get the .deb, too: [http://packages.ubuntu.com/jaunty/compizconfig-settings-manager](http://packages.ubuntu.com/jaunty/compizconfig-settings-manager) [for Jaunty]

That worked. Thanks.  I completely didn't think about the Add/Remove application.  I've used it before, but primarily I deal with Synaptic...or go old school and use apt-get in terminal.

Cheers!

---

### Post by Legace on 2009-06-06
Glad it worked, enjoy ;)

---

