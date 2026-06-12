---
title: "Configuration Defaults Gnome Power Management"
date: 2009-03-28
forum: General Help
---

### Post by Gillette on 2009-03-28
I'm running Hardy Heron and recently when I start up the computer a message appears that says something about the Configuration Defaults for the GNome power management are not correct and that I should check with the administrator. Well I'm the administrator and I don't know anything about it.

The computer works fine until I click on the icon to shut the computer down. Then it freezes up and nothing works. The mouse pointer still moves but you can't click on anything. I then have to manually press the button on the computer to shut it down. 

Anyone got a suggestion on getting it to work normally again?

---

### Post by imparja2 on 2009-03-28
Did it happen just after you installed updates.

I had this problem I ran 
sudo dpkg-- configure-a
sudu apt- get update
sudu apt- get upgrade

then I had some troubles with msttcorefonts that I fixed
but try this to start

---

### Post by Gillette on 2009-03-28
I tried "sudo dpkg-- configure-a" but it said command not found.

---

### Post by Ptero-4 on 2009-03-28
it's
```
sudo dpkg --configure -a
```

---

### Post by Gillette on 2009-03-28
sudu apt- get update
sudu apt- get upgrade

These don't seem to be valid commands, even when I change ti to sudo.

---

### Post by Ptero-4 on 2009-03-31
> **Gillette said:**
> sudu apt- get update
sudu apt- get upgrade

These don't seem to be valid commands, even when I change ti to sudo.

They're
```

sudo apt-get update
sudo apt-get safe-upgrade 

```
(the "upgrade" was changed to safe-upgrade somewhere between gutsy and hardy IIRC)

---

