---
title: "Sound not working in games"
date: 2005-05-30
forum: Gaming &amp; Leisure
---

### Post by YopY on 2005-05-30
I've been using Ubuntu for... erm, half a week now, and no real problems yet. Well, except this one. See, i've installed a few random games from Universe, but none of them seem to have the sound in them working really. Wether this is because there is no sound or because there's something wrong with my computer, i don't know, but seeing that sound does work in other applications like when booting up etc, i suspect there's something odd going on. 

So, anyone have any idea what my problem might be? I have a common intergrated sound chip, and it works fine in other apps, just not in games.

---

### Post by Marquis_de_Carabas on 2005-05-30
[QUOTE=YopY]I've been using Ubuntu for... erm, half a week now, and no real problems yet. Well, except this one. See, i've installed a few random games from Universe, but none of them seem to have the sound in them working really. Wether this is because there is no sound or because there's something wrong with my computer, i don't know, but seeing that sound does work in other applications like when booting up etc, i suspect there's something odd going on. 

So, anyone have any idea what my problem might be? I have a common intergrated sound chip, and it works fine in other apps, just not in games.[/QUOTE]

If it's an integrated sound chip then it's probably not capable of mixing seperate audio streams in hardware.

Assuming you don't want to go out and buy another sound card (my Audigy 2 has worked perfectly with Ubuntu from the start), [this HowTo](http://ubuntuforums.org/showthread.php?t=32063) should be worth checking out.

Failing that, I know that this issue has cropped up for a few people so a search should give you quite a few threads to look through.

Best of luck!

(Edit: Of course it's also possible that you just haven't installed a game which has sound effects yet. Try Gnometris (should already be installed) and if you hear the beeps then ignore everything I've said above...)

---

### Post by Toddy on 2005-05-30
Try this:

sudo apt-get install libsdl1.2debian-all

worked for me...

---

### Post by YopY on 2005-05-31
@Marquis: That particular game has the sound working for me, yes. 

@Toddy: Did that, and it works ^_^. Thanks a lot

---

