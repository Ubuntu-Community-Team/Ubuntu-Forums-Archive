---
title: "How to install Unity Privacy Settings in Ubuntu 12.04?"
date: 2012-05-03
forum: Desktop Environments
---

### Post by lads on 2012-05-03
Dear all, I upgraded to 12.04 yesterday and am now going through the new features. By some reason the new Privacy tab in the Systems Settings menu is not available. How can I install it?

Thank you.

---

### Post by stinkeye on 2012-05-03
Do you have this installed ?
```
activity-log-manager-control-center
```

---

### Post by lads on 2012-05-04
No I had not, thank you for replying. From the advertising I got the idea this package would be included in the new release, but it seems it is not. We upgraded another laptop here in the office and the Privacy package was not installed either.

---

### Post by coffeecat on 2012-05-04
> **lads said:**
> We upgraded another laptop here in the office and the Privacy package was not installed either.

Interesting and useful observation - thanks.

The privacy utility is included if you do a fresh install of 12.04 from the desktop CD - the package activity-log-manager-control-center is included in the manifest for the CD and gets installed. Checking the dependencies for the metapackage ubuntu-desktop, I see that activity-log-manager-control-center is listed only as a "recommends", not a dependency. I guess this may be why it is not installed when you do a 11.10 -> 12.04 upgrade.

Would you be prepared to do a bug report?

---

### Post by lads on 2012-05-05
> **coffeecat said:**
> 
Would you be prepared to do a bug report?

I can do it, but is it really a bug or a feature? The upgrade also screwed up the menus with Ambiance but it was an illogic option by the developers.

---

### Post by coffeecat on 2012-05-05
I'd hardly call a missing package that is meant to be there a feature. Sounds like a bug to me. An unfortunate bug because many would find that a useful utility.

---

### Post by greg.dean on 2012-05-08
> **stinkeye said:**
> Do you have this installed ?
```
activity-log-manager-control-center
```
Agreed. Installing this worked.

---

