---
title: "[SOLVED] Windows look corrupt"
date: 2007-07-24
forum: Desktop Effects &amp; Customization
---

### Post by upthelum on 2007-07-24
Can anyone even hazard a guess as to what's going on here? I posted this in General Help but got no response so thought i would try here. I've been messing with software installations and having problems but everything was fine until i switched my machine on this morning, then Ubuntu booted to the user password screen which looks like this too. Synaptic, Thunar and other programs look like this, displaying squares instead of text. If anyone knows whats wrong i'd love to hear it, thanks in advance...

---

### Post by Espreon on 2007-07-24
Did that happen after an upgrade from Edgy to Feisty? I tried upgrading to Feisty from Edgy and got that result. The only solution I know of is to reinstall...

---

### Post by upthelum on 2007-07-24
Unfortunately i may have inadvertently upgraded, is the only way to repair it to reinstall?

---

### Post by upthelum on 2007-07-24
Can anyone verify this before i go ahead and re-install the os?

---

### Post by hyperair on 2007-07-24
I upgraded from Edgy to Feisty and never experienced that problem. Could you try:
```

sudo dpkg-reconfigure fontconfig-config

```

---

### Post by upthelum on 2007-08-04
Well since the last post i upgraded and most is fine so far...

---

