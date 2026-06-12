---
title: "Firestarter error"
date: 2009-06-22
forum: General Help
---

### Post by ~sHyLoCk~ on 2009-06-22
After installing firestarter I have added the permission in sudoers list and also added it in startup application! But everytime my system starts I get this error window pops up:

```
Firestarter error: failed to open system log. No event information will be available."
```

What should I do?

---

### Post by lovinglinux on 2009-06-23
> **~sHyLoCk~ said:**
> What should I do?

Forget about Firestarter and install gufw.

Open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

```
sudo apt-get purge firestarter && sudo apt-get install ufw gufw
```

Then open gufw through "System >> Administration >> Firewall Configuration"

Firestarter is not recommended anymore and it hasn't been updated for a while. Errors like yours are becoming common. Besides, you don't need to run it at boot. Firestarter and gufw are just firewall managers. They allow you to easily create iptables (the real firewall) rules and can be closed after initial setup, because iptables runs in the background.

Don't forget to remove the permission from sudoers.

---

### Post by ~sHyLoCk~ on 2009-06-23
> **lovinglinux said:**
> Forget about Firestarter and install gufw.

Open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

```
sudo apt-get purge firestarter && sudo apt-get install ufw gufw
```

Then open gufw through "System >> Administration >> Firewall Configuration"

Firestarter is not recommended anymore and it hasn't been updated for a while. Errors like yours are becoming common. Besides, you don't need to run it at boot. Firestarter and gufw are just firewall managers. They allow you to easily create iptables (the real firewall) rules and can be closed after initial setup, because iptables runs in the background.

Don't forget to remove the permission from sudoers.

Actually problem is solved! I don't use ufw. I use firestarter as a gui for iptables. Thanks anyway. I rebuild using the new package uploaded today by fukawi2. :)

---

### Post by perspectoff on 2011-05-02
Nah. Gufw is only approaching Firestarter's functionality in 2011.

The reason Firestarter hasn't been updated is because it has been pretty effective and stable for some time.

UFW/GUFW was an attempt to re-invent the wheel, and only recently are its options and usability starting to approach Firestarter's....

I don't see any deep packet inspection in UFW... when it does that, I'll admit that it's better than Firestarter.

The syslog problem is new for me in Natty... Still looking for the solution.

---

