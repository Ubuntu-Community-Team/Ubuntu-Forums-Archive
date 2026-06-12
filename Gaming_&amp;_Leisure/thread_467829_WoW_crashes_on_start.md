---
title: "WoW crashes on start"
date: 2007-06-08
forum: Gaming &amp; Leisure
---

### Post by rob1101 on 2007-06-08
when ever i start [LEFT][COLOR=red][FONT=serif]**_WoW_**[/FONT][/COLOR][/LEFT]
 the screen usually just goes white and i here sound trying to play, ( i think it is trying to play a movie ) the game just freezes there. i cant even get to the [LEFT][COLOR=green][FONT=serif]**_character_**[/FONT][/COLOR][/LEFT]
 [LEFT][COLOR=red][FONT=serif][B][U]loggin


EDIT: lol forgot to turn off google spellcheck, it late...or well early actually...
[/U][/B][/FONT][/COLOR][/LEFT]

---

### Post by Sockerdrickan on 2007-06-08
[COLOR="Red"]WtF[/COLOR]
[COLOR="Orange"]I don't get what your[/COLOR] [COLOR="Red"]problem[/COLOR] [COLOR="DarkRed"]is[/COLOR]

---

### Post by Feba on 2007-06-08
I've seen a few posts of yours, why the heck do you have google spellcheck at all? Feisty comes with a built in spellchecker for email/internet/IM last I checked.

---

### Post by rob1101 on 2007-06-11
> **Feba said:**
> I've seen a few posts of yours, why the heck do you have google spellcheck at all? Feisty comes with a built in spellchecker for email/internet/IM last I checked.

how do i access this spell checker? if your talking about the red lines that appear under misspelled words, they don't always catch everything.

and to restate my original problem. basically when i start up WoW it crashes

---

### Post by jrocket on 2007-06-11
How are you running WoW?  Through wine or cedega?  Are you using d3d or opengl?

---

### Post by rob1101 on 2007-06-12
> **jrocket said:**
> How are you running WoW?  Through wine or cedega?  Are you using d3d or opengl?

i am running it through wine and i dont know if im using d3d or open gl. how do i tell?

---

### Post by hikaricore on 2007-06-12
> **rob1101 said:**
> i am running it through wine and i dont know if im using d3d or open gl. how do i tell?

[B]
OpenGL (the right way)[/B]
```

cd ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/
wine WoW.exe -opengl
```



**D3D (the wrong way)**

1. Blinding starting WoW from a menu or desktop icon paying absolutely no regard to the fact that every HowTo in existance tells you not to do it this way right off the bat,
especially if you are having trouble.  This of course assumes you havn't manually set opengl mode in your Config.wtf.

2. Running:
```
wine WoW.exe
```
From whatever directory you feel like ignoring the fact that this will always fail unless you happen to be in the WoW folder by accident.  Again this assumes you havn't manually modified Config.wtf.

---

### Post by Sammi on 2007-06-12
@hikaricore
I want to learn the way of the sarcastic. Will you be my Jedi master? :p

---

### Post by Big Bear on 2007-06-12
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

That and only that got me running WoW on my system in like 2-3 hours... which includes the time it took to install, patch, and tweak to work.

---

### Post by Echelon1230 on 2007-06-17
I start up WoW and select my character and enter the game without problems. I go into my video options to lower them for a more smooth game. I click "OK" and it freezes. I have no clue what to do here.. Any suggestions?

---

### Post by hikaricore on 2007-06-17
> **Echelon1230 said:**
> I start up WoW and select my character and enter the game without problems. I go into my video options to lower them for a more smooth game. I click "OK" and it freezes. I have no clue what to do here.. Any suggestions?

You can't change the settings in WoW in opengl mode.  (this is mentioned in every howto)
Run the game with the d3d flag to make changes then restart the game in opengl mode.

You can also manually edit the config.wtf file as it's only a text file.  ^_^

Hope this helps.

--Aaron

---

