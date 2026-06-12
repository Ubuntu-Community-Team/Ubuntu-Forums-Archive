---
title: "[SOLVED] How do I get back my Ubuntu display manager?"
date: 2008-02-25
forum: Desktop Environments
---

### Post by solarwind on 2008-02-25
Hey all,

I recently installed xubuntu-desktop and now I'm stuck with the xubuntu style display manager. How do I get my normal GDM back?

---

### Post by Scheater5 on 2008-02-25
I do believe what you're looking for is
```
sudo dpkg-reconfigure gdm
```

Then just select GDM from the menu.

---

### Post by solarwind on 2008-02-25
> **Scheater5 said:**
> I do believe what you're looking for is
```
sudo dpkg-reconfigure gdm
```

Then just select GDM from the menu.

I tried that, it still gives me the xubuntu thing.

---

### Post by BoeBoe on 2008-02-26
Remember to select the right display manager on login screen.

---

### Post by solarwind on 2008-02-26
> **BoeBoe said:**
> Remember to select the right display manager on login screen.

Where is that?

---

### Post by y-lee on 2008-02-26
> 
Originally Posted by BoeBoe* Remember to select the right display manager on login screen.*

Where is that?


When you first login in to your system there should be something labeled **sessions** / Click it and there you can selected different desktop environments if you have them installed.

---

### Post by solarwind on 2008-02-26
> **y-lee said:**
> When you first login in to your system there should be something labeled **sessions** / Click it and there you can selected different desktop environments if you have them installed.

No no, I know *that*, but what I want to get back is the original GDM and not the XFCE display manager thing.

---

### Post by y-lee on 2008-02-26
Can you select it from here?

```
gksu gdmsetup
```

---

### Post by y-lee on 2008-02-26
If gksu gdmsetup doesn't work maybe

```
sudo dpkg-reconfigure xdm
```

and select gdm from the list there might.

---

### Post by solarwind on 2008-02-26
> **y-lee said:**
> Can you select it from here?

```
gksu gdmsetup
```

Thanks a lot! That worked! It turns out I was running it without sudo...

---

