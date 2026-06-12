---
title: "ubuntu 11.10 gnome theme issue with top bar"
date: 2012-01-29
forum: Desktop Environments
---

### Post by Pwntastic on 2012-01-29
When logging in the gnome session and applying my new themes the top bar has some useless text in it. It says (file edit view go bookmarks help). This is appearing behind the Activities button. plz help!

---

### Post by markbl on 2012-01-29
That is the unity global menu stuff affecting gnome-shell. Copy/paste the following into a terminal window then log out and back in.
```

echo '[ "$DESKTOP_SESSION" != "ubuntu" ] && unset UBUNTU_MENUPROXY' | sudo tee /etc/X11/Xsession.d/81ubuntu-menu-proxy

```

This won't change anything in a Ubuntu (Unity) session.

---

### Post by Pwntastic on 2012-01-29
Thank you very much =]

---

### Post by errati on 2012-02-23
Thanks. This was a real nuisance!!

---

