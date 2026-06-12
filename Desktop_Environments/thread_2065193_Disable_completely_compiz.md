---
title: "Disable completely compiz"
date: 2012-10-01
forum: Desktop Environments
---

### Post by adamitj on 2012-10-01
Hi!

I had Ubuntu 12.04 installed, so I did:

```
sudo apt-get install xubuntu-desktop compiz compizconfig-settings-manager
```

After all, I did:

```
compiz --replace &
```

And I replaced Xfwm4 by compiz, but I don't like it... so I'm trying to disable compiz without success, I also tried:

```
xfwm4 --replace
```

and

```
gtk-window-decorator --replace --metacity-theme greybird
```

But the fourth button on window toolbar still visible (that one which minimize window to one floating bar) and character rendering is buggy (appears that don't have the exact suavization).

What can I do to restore Xubuntu and XFCE original window manager and decorator?

---

### Post by adamitj on 2012-10-01
Oh! Dear God! I found the solution. Desperately I removed folder ~/.config/xfce4 and restarted the session... 

... but I lost every custom config I had. Anyways, it worked.

---

