---
title: "BUG when entering root password"
date: 2010-12-05
forum: Desktop Environments
---

### Post by moderemx on 2010-12-05
Hello

Whenever I am prompted to enter the root password, typical example would be in 'Power Management' clicking the button 'Make Default', pressing ENTER or clicking AUTHENTICATE doesn't close the box. To get passed this I have to press ALT+F4 and it continues which I'm assuming still does authenticate. Can anyone tell me why this is happening or if this is a known problem?

Thanks

---

### Post by Frogs Hair on 2010-12-05
I had a similar problem with the update manager , but it was theme related and when I removed the theme it no longer happened. I'm don't know if that applies in your case.

---

### Post by sisco311 on 2010-12-05
Yep, it's a known bug: [lpbug]649939[/lpbug]

It's fixed, but the package is not available from the official repositories. You have to install polkit-1 (0.96-2ubuntu1.2) from: [https://launchpad.net/~james-w/+archive/polkit](https://launchpad.net/~james-w/+archive/polkit)

```
sudo add-apt-repository ppa:james-w/polkit
sudo apt-get update
sudo apt-get upgrade
```

---

