---
title: "Discrete Kiba-dock"
date: 2006-11-15
forum: Desktop Environments
---

### Post by Nonno Bassotto on 2006-11-15
Is there a way to make kiba-dock a little more discrete? I'd like to have icon zooming on mouseover and maybe a little bouncing, but I'm not able to do this.

I've played with the settings, but things didn't get much more better. In particular I'd like to have a fixed icon order (otherwise the dok usability tends to zero) and I don't want the icon to jump so high when clicked.

I understand that kiba-dock is a demonstration of what can be done with physical effects in a dock, but this reduces usability. I hope there's a way to lessen the special effects...

---

### Post by mozetti on 2006-11-15
I use the kiba-utils gui to make these changes. At work, and fairly new, so that's about as much as I can give your right now. But, there is a tool available, and it does work.

---

### Post by Nonno Bassotto on 2006-11-15
As I said, I've played a bit with the settings, but with no results. Icons want to jump and bounce everywhere as if they were full of crazy springs.

---

### Post by CatKiller on 2006-11-15
> **Nonno Bassotto said:**
> Is there a way to make kiba-dock a little more discrete? I'd like to have icon zooming on mouseover and maybe a little bouncing, but I'm not able to do this.

You can use the rope model, to have them all tied together. They don't bounce very high then. Or change the model to springs_for_all. I think that will keep them in a fixed order (well, until you move them yourself, anyway), although I haven't tried that model much.

You can even directly change the bounce height directly by changing the /apps/kiba/options/mouseover_effects/bounce_height key in **gconf-editor**. A value of 2.0 is quite a gentle bounce. Actually, I think this value is the same as the "Exec Height" option on the Effects tab of the Launchers screen of the Settings Editor.

You obviously didn't play enough with the settings :)

---

### Post by tehkain on 2006-11-16
Is there a way to make it so it doesn't throw the icon when I click it. I like the zoom and all but throwing is to much.

---

### Post by CatKiller on 2006-11-16
> **tehkain said:**
> Is there a way to make it so it doesn't throw the icon when I click it. I like the zoom and all but throwing is to much.

Of course. Just set the bounce height to 0.

---

### Post by Nonno Bassotto on 2006-11-17
Ok, a throwing height about 0.20 is nice, but sometimes the icon doens't have enough momentum and gets stuck between the others. Anyway it's the best I got for now, thank you (I was looking under the physics tab for this).

I still have to work out how to fix the order ( I know I can with rope model, but then I don't have a dock anymore). I always thought that the usefulness of a mac-like dock was the fact that the icon zooming helps you to aim more quicly and precisely, so you lose less time searching for the icon you need. But if the icons change their order every time...

---

