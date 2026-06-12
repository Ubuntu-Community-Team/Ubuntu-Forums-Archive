---
title: "network manager passwords"
date: 2011-12-15
forum: Desktop Environments
---

### Post by kakk on 2011-12-15
Hi,
I have a strange problem. Network manager used to save its wireless passwords automatically, but after I deleted my .gnome* folders (due to some other problems), it does not save passwords any more. I really do not know where should I look at? I have checked options in network manager itself, but not much luck. I'm using gnome-classic under 11.10

Any ideas?

---

### Post by jimmydean886-2 on 2011-12-15
You may or may not find help on GNOME.org under their forums. This stuff happens. (unfortunately)

Most of these problems have been worked out, so I hope you find what you're looking for!

---

### Post by thaelim on 2011-12-16
I suspect what has happened is that the login keyring has been deleted when you removed the gnome stuff. You can recreate it by opening the "Passwords and Keys" applet and selecting File->New->Password Keyring - call it 'login'. There may be more steps (I can't test it without deleting my own login keyring, which would be bad!)

---

### Post by kakk on 2011-12-16
> **thaelim said:**
> I suspect what has happened is that the login keyring has been deleted when you removed the gnome stuff. You can recreate it by opening the "Passwords and Keys" applet and selecting File->New->Password Keyring - call it 'login'. There may be more steps (I can't test it without deleting my own login keyring, which would be bad!)

Thanks. I also had to re-enter password for VPN, but that one was saved and now when I open the "Passwords and Keys", it has line called "Password: login", which lists also the VPN password. So in some manner it exists, but nm-applet does not contact it correctly? Where exactly in .gnome* is the "Password and Keys" thing located, maybe I could have a look at them directly?

---

