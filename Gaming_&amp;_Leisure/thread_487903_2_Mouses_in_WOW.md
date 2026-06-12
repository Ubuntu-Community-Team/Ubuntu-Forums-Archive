---
title: "2 Mouses in WOW"
date: 2007-06-29
forum: Gaming &amp; Leisure
---

### Post by Abss1185 on 2007-06-29
Hi, i got WoW running in wine for ubuntu but when i run it, it shows the normal desktop mouse as well as the WoW mouse and also the WoW mouse moves slower than my actual mouse, what im asking is, is there anyway i can just get my WoW mouse showing, i can live with it being lower its just i dont know what im clicking on right way when i have two mice. Thx in advance.

---

### Post by Ripfox on 2007-06-30
Known issue...no cure as far as I know.

---

### Post by sc3252 on 2007-06-30
it only shows 2 mice(mouses??) if you are running the game in direct x mode.  You want to run the game in opengl mode for full performance.

```

cd world of warcraft location
wine wow.exe -opengl

```

---

### Post by Abss1185 on 2007-06-30
SC ty sooo much i have one mouse now, but it still runs a lil slow but hey thx again bud =)

---

### Post by Motoxrdude on 2007-06-30
> **Abss1185 said:**
> SC ty sooo much i have one mouse now, but it still runs a lil slow but hey thx again bud =)
What video card do you have?
If it's an ATI card, this is normal. Basicly the ati drivers for linux is pretty crappy.

---

### Post by AndrewRiedi on 2007-06-30
I got my D3D hardware cursor patch accepted a little while back.  Try making sure you have a recent Wine and select the little check box for a hardware cursor if you want to play in D3D mode.  Thanks.  ;)

---

### Post by Ripfox on 2007-06-30
So you can play in D3D with one mouses now? Wow, cool. I have an intel gm945 so no opengl mode for me...

---

### Post by AndrewRiedi on 2007-06-30
> **ripfox said:**
> So you can play in D3D with one mouses now? Wow, cool. I have an intel gm945 so no opengl mode for me...

Yep yep.  ;)

---

