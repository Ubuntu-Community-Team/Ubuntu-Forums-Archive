---
title: "How much does cedega cost?"
date: 2007-06-18
forum: Gaming &amp; Leisure
---

### Post by kdarkentity on 2007-06-18
im thinking about getting cedega but im curious how much it costs before i get it

---

### Post by justin whitaker on 2007-06-18
> **kdarkentity said:**
> im thinking about getting cedega but im curious how much it costs before i get it

$60 per year. You pay 3 months up front, then $5 per month after that. You can buy the year up front, and get a discount.

---

### Post by kdarkentity on 2007-06-18
jeez thats expensisve

---

### Post by cogadh on 2007-06-18
You only have to pay for the three months, then you can cancel. However you can't get any further updates if you cancel your subsciption at the end of three months.

You might just want to use Wine, they just started adding copy protection support to it, which is the only real advantage Cedega currently has over Wine.

---

### Post by dfreer on 2007-06-18
other than pixel shader 2.0 support, which AFAIK wine has yet to adopt. yay for F.E.A.R.!

---

### Post by cogadh on 2007-06-18
Wine has pixel shader 2.0 support through GLSL, but it is still experimental and is disabled by default. You can enable it with a registry edit, but I can't recommend it as I've never tried it.

If you want to read up on it, look [here]("http://wiki.winehq.org/DirectX-Shaders").

---

### Post by kdarkentity on 2007-06-18
What is GLSL exactly?

---

### Post by hikaricore on 2007-06-18
FYI getting Cedega will _probably not_ instantly solve your problems with WINE that I've seen you
posting about.  Just wanted to throw that out there before you get a huge disappointment.  >.<

---

### Post by cogadh on 2007-06-18
> **kdarkentity said:**
> What is GLSL exactly?
OpenGL Shading Language, it's part of the OpenGL 2.1 specification. It's essentially the equivalent of DirectX's High Level Shader Language and it is what will allow Wine to replicate PS 2.0 and higher.

---

### Post by kdarkentity on 2007-06-18
alright sweet ...do u think i could try to get that to work? ...because im trying to get halo to work in wine and i keep getting errors that i think are related to no shader support... but idk

---

### Post by cogadh on 2007-06-18
Right now it is alpha code, so it is unstable and probably won't work, but you can try it if you want to.

1. Open a terminal and type "regedit" (without the quotes)
2. Navigate through the file tree to HKEY_CURRENT_USER/Software/Wine
3. Right-click in the right hand window and select New > Key
3. Name the key Direct3D and hit enter
4. Right-click again and select New > String Value
5. Name the new string "UseGLSL" (without the quotes)
6. Right-click on the string and select Modify
7. type "enabled" in the field (again, no quotes)
8. Exit regedit and try running the game

See the attached screenshot if the instructions seem confusing.

---

### Post by kdarkentity on 2007-06-18
alright thanks ill try that... im in windows right now tho soo ill prob do it tomorrow

---

### Post by Dragonshadow on 2007-06-18
Cedega is outdated compared to WINE.

---

### Post by cogadh on 2007-06-18
Even I have to say that's not true (and I have a huge dislike for Cedega). CedegaCVS is way out of date, but the paid version of Cedega and Wine are very close. It actually surpasses Wine in copy protection support, at the moment.

---

### Post by frodon on 2007-06-19
> **cogadh said:**
> Right now it is alpha code, so it is unstable and probably won't work, but you can try it if you want to.

1. Open a terminal and type "regedit" (without the quotes)
2. Navigate through the file tree to HKEY_CURRENT_USER/Software/Wine
3. Right-click in the right hand window and select New > Key
3. Name the key Direct3D and hit enter
4. Right-click again and select New > String Value
5. Name the new string "UseGLSL" (without the quotes)
6. Right-click on the string and select Modify
7. type "enable" in the field (again, no quotes)
8. Exit regedit and try running the game

See the attached screenshot if the instructions seem confusing.To give even more choice here is an other way to do exactly the same thing :

1- create a file called filereg :
```
gedit ~/filereg
```
2- put this inside and save it :
```
[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"UseGLSL"="enabled"
```
3- run this command :
```
wine regedit ~/filereg
```

---

### Post by tomcheng76 on 2007-06-19
is it enable or enabled ?
Thanks

---

### Post by cogadh on 2007-06-19
enabled

Sorry, I misstyped in the original post, fixed now.

I feel I must stress that this is not a fully implemented feature of Wine and what is implemented is only experimental. It is not likely to work as anticipated and may actually break games that already work. AFAIK it will not harm anything by trying it and it can be turned off just by deleting the registry entry or changing it to "disabled", but still, use at your own risk..

---

