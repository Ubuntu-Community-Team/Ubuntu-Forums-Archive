---
title: "I lost x"
date: 2009-12-11
forum: Desktop Environments
---

### Post by SoylentSteak on 2009-12-11
I wasn't even doing any upgrading. 

I tried ```

sudo apt-get remove x-window-system-core xserver-org
sudo apt-get install x-window-system-core xserver-org


```

But it said something about not being able to parse something. 

What am I to do? :(

---

### Post by ibuclaw on 2009-12-11
> **SoylentSteak said:**
> I wasn't even doing any upgrading. 

I tried ```

sudo apt-get remove x-window-system-core xserver-org
sudo apt-get install x-window-system-core xserver-org


```

But it said something about not being able to parse something. 

What am I to do? :(

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Or select the **Fix X** option in the Recovery Menu.

---

### Post by synapsys on 2009-12-11
> **tinivole said:**
> ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Memorize this, it's saved my butt more than once...

---

### Post by SoylentSteak on 2009-12-11
> **synapsys said:**
> Memorize this, it's saved my butt more than once...

I have no clue what to do after that. I'm not an advanced user. :confused:

Also, for some reason, pressing F10 on boot no longer allows me to go into recovery mode.

---

### Post by avajesh on 2009-12-12
select the recovery mode from grub menu.

---

