---
title: "Shutdown / Restart Delay"
date: 2009-06-04
forum: General Help
---

### Post by Greenwidth on 2009-06-04
I know you can turn off the confirmation dialogues for logout/shutdown/restart together, but can you set them individually?

I would like to have restart as immediate, but I like having the delay enabled for shutdown.

---

### Post by Greenwidth on 2009-06-10
Not possible?

---

### Post by cariboo on 2009-06-10
Right click on the Fast user switcher icon and select Preferences, then uncheck Show confirm dialogs for logout, restart and shutdown.

---

### Post by Legace on 2009-06-10
> **cariboo907 said:**
> Right click on the Fast user switcher icon and select Preferences, then uncheck Show confirm dialogs for logout, restart and shutdown.

Thats not a solution:
> **Greenwidth said:**
> I would like to have **restart as immediate**, but I like having the **delay enabled for shutdown**.

Maybe be you could create a seperate launcher for shutdown.
Just type in the following in the "Command" field:
```
sudo shutdown -h now
```

---

### Post by DiegoTc on 2009-06-10
Why you dont do it by terminal
sudo shutdown -r 0 (that is for restaring)
sudo shutdown -h 0 (Shutdown9

---

