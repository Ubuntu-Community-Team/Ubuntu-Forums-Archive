---
title: "[SOLVED] Making Avant-Window-Navigator stay above Gnome Panels"
date: 2007-09-13
forum: Desktop Effects &amp; Customization
---

### Post by happy-and-lost on 2007-09-13
I love AWN, but am bored with the same old Mac-ish way of using it. So I'm trying out a new space-saving design...

[[img]http://xs219.xs.to/xs219/07374/midsep.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs219&d=07374&f=midsep.png)

Works nicely, except for the fact that when I click on the Gnome panel, AWN goes behind it. Is there a way of making AWN stick above the panel (maybe using Compiz window rules)?

:KS

---

### Post by smartboyathome on 2007-09-13
Isn't there a way to set priorities in CompizConfig? I think I remember seeing one in there. If so, you should try setting Avant to the highest, and then I think nothing will cover it.

---

### Post by acelin on 2007-09-13
How would I so this in beryl?

---

### Post by smartboyathome on 2007-09-13
> **acelin said:**
> How would I so this in beryl?

Maybe set focus stealing prevention to high? this would not be good if you are gaming, though.

---

### Post by acelin on 2007-09-13
Okay- where is that? I think i might know, but i am not sure...

---

### Post by smartboyathome on 2007-09-13
I don't use beryl anymore, but last I looked it was in the main options.

---

### Post by acelin on 2007-09-13
That did not do it...hmmm... are there any options to set AWN's specifically?

---

### Post by smartboyathome on 2007-09-13
Not that I know of. Perhaps try fusion and looking for something about priorities.

---

### Post by acelin on 2007-09-13
I have an intergrated card- no fusion for me.

---

### Post by Nessa on 2007-09-13
How did you do that? (I have compiz-fusion)

---

### Post by acelin on 2007-09-13
DO what? I have beryl on an intergrated card

---

### Post by Nessa on 2007-09-13
@threadstarter

How did you make awn appear on top of the panel?

---

### Post by acelin on 2007-09-13
I have beryl on an inegrated graphics card- 

what are you asking?

---

### Post by the yawner on 2007-09-13
@thread starter

I have tried that layout a while back, but I got 2 problems with that layout. The first one, the one you mentioned now. The second one, the lack of control over the space in which AWN draws its icons. Since it is placed on the center of the screen, eventually you'll cover up the other applets on the panel especially when you have too many launchers and open windows.

 But I did managed a workaround, but not one I would prefer. Reading your post, I tried it out again to give you an idea what am I talking about. (Err.. How do you do thumbnails here?)Heh.

[AWNLayout.png]("http://img.photobucket.com/albums/v90/kiel_008/screenies/ubuntu/AWNLayout.png")

---

### Post by happy-and-lost on 2007-09-14
> **Nessa said:**
> @threadstarter

How did you make awn appear on top of the panel?

It runs above the panel if the panel is at the bottom. I just made all the other bits invisible.

In gconf, AWN has an option to keep below, but not one for above. Maybe I just need to write a patch for it...

---

### Post by happy-and-lost on 2007-09-15
For anyone interested... I have now SOLVED this problem.

Using devilspie, with a .ds file reading...

```
(if (is (application_name) "avant-window-navigator") (above))

```

Easy as, well, pie!

---

### Post by Rupertronco on 2007-09-15
> **acelin said:**
> I have an intergrated card- no fusion for me.

I'm running fusion smoothly on a notebook which is a P3-1200mhz and intgegrated graphics, you should try it out.

---

### Post by Nessa on 2007-10-01
> **happy-and-lost said:**
> For anyone interested... I have now SOLVED this problem.

Using devilspie, with a .ds file reading...

```
(if (is (application_name) "avant-window-navigator") (above))

```

Easy as, well, pie!

Where is that and how do I do that?

---

