---
title: "Where did she get the goldfish??"
date: 2009-02-27
forum: General Help
---

### Post by Czarzhan on 2009-02-27
My wife has an old Toshiba Satelite running Ubuntu 8.10. This evening, as we were preparing dinner, our two year old decided to do... something. When I noticed she was there, she had just closed a screen that had GNOME in the title (it went away too fast). Now, a little goldfish periodically swims across the screen, and it doesn't appear to be associated with the screensaver. We have been unable to track down what has been generating it.

Any ideas on how to get rid of the little bugger?

---

### Post by sailthesea on 2009-02-27
Its probably one of the panel applets
Try clicking on it to see what launches or right click panel and check what is enabled 
 Two years old you say? I see a future there:P

---

### Post by Ms_Angel_D on 2009-02-27
lmao reminds me of my kids when they we're little my son in particular. He's always been fascinated with electronics and computers, he's 15 on monday now though MY GOOS HOW TIME FLIES!!

---

### Post by yther on 2009-02-27
Is it [this]("http://www.eeggs.com/items/50088.html") fish?  :)

---

### Post by Czarzhan on 2009-02-27
> **sailthesea said:**
> Its probably one of the panel applets
Try clicking on it to see what launches or right click panel and check what is enabled 
We found it on Add To Panel, but there doesn't seem to be a way to remove it. Clicking on it just makes it swim offscreen for a moment.
> **sailthesea said:**
> Two years old you say? I see a future there:PYou have no idea.

---

### Post by unutbu on 2009-02-27
Right-click on gnome panel, select the "About Panels" menu item. Type 'fff', and a fish appears!

Open a terminal (Applications>Accessories>Terminal), type
```
killall gnome-panel
``` 
to clear.

PS. Very impressive 2 year old :)

---

### Post by Fire-Eyes on 2009-02-27
> **unutbu said:**
> Right-click on gnome panel, select the "About Panels" menu item. Type 'fff', and a fish appears!

Open a terminal (Applications>Accessories>Terminal), type
```
killall gnome-panel
``` 
to clear.

PS. Very impressive 2 year old :)



thanks...she is a pain in the butt sometimes, but her and electronics jive.
She tries to eat technology all the time..lol  I can not even explain.

oh by the way I am the mom/wife....
thank you

---

### Post by MarblePanther on 2009-02-27
Clicking on the fish makes it go away.  At least it did for me

Very cool GNOME easter egg!

---

### Post by Fire-Eyes on 2009-02-27
> **MarblePanther said:**
> Clicking on the fish makes it go away.  At least it did for me

Very cool GNOME easter egg!

When I click it it would swim quickly off screen and the come back moments latter. Why would you want it? About drove me batty.

---

### Post by MarblePanther on 2009-02-27
> **Fire-Eyes said:**
> When I click it it would swim quickly off screen and the come back moments latter. Why would you want it? About drove me batty.

Haha, you're right, it just came back on mine too :)

The OP's suggestion:

```
 killall gnome-panel 
```

does the trick

As for why anyone wants it?  :confused:

Just GNOME devs having fun, I guess

---

### Post by sailthesea on 2009-02-27
Brilliant!
I think its time for someones first machine You,ll have to keep an eye on that one!:grin

---

### Post by Fire-Eyes on 2009-02-27
> **sailthesea said:**
> Brilliant!
I think its time for someones first machine You,ll have to keep an eye on that one!:grin

she has a leap frog my first computer...she will get my laptop if we ever get the money for a replacement...:P

---

### Post by sailthesea on 2009-02-27
Sounds like she could earn enough to buy it for you if she wanted to!
Bless!

---

