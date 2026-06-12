---
title: "how do i unpack?"
date: 2005-10-26
forum: Desktop Environments
---

### Post by bete on 2005-10-26
I downloaded Azureus from their webpage.
It came in a tar.gz2 format, so how do i unpack it and install it?

---

### Post by psychicdragon on 2005-10-26
You can open a tar file with a gui program called file-roller, it's called Archive Manager in the gnome menu I believe. It behaves a lot like WinZip.

Or, to unpack it from the command-line you can do something like:
```
tar zxf file.tar.gz -C /some/where
```

I wouldn't recommend you install Azureus this way though. It makes it more or less impossible to uninstall later. Take a look at this excellent guide: [HOWTO: Installing Azureus on Breezy]("http://ubuntuforums.org/showthread.php?t=75272&highlight=azureus") for a better way to install Java and Azureus.

---

### Post by Jenda on 2005-10-26
Indeed. What you downloaded is probably the source code. You don't want to mess with that...
Use the HOWTO above.

---

### Post by bete on 2005-10-26
Used the how-to.. Worked great :D Thanks!

---

### Post by Jenda on 2005-10-26
You're welcome. Enjoy Ubuntu!

---

