---
title: "Is Steam Possible?"
date: 2007-01-03
forum: Gaming &amp; Leisure
---

### Post by sdmike on 2007-01-03
Is it possible for me to download steam onto Edgy? So I can install and play counter strike source.

If so, can someone point me into the right direction.

---

### Post by maxamillion on 2007-01-03
[http://appdb.winehq.org/](http://appdb.winehq.org/)  <-- steam and cs:source are said to be functional

[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb) <-- here is how to install the emulator

---

### Post by sdmike on 2007-01-03
Ok so I installed steam with the latest wine and when I go to setup my steam account the boxes and colors of the program are there BUT THERE IS NOT TEXT AND I CAN'T TYPE AND TEXT IN.

Why is this?

---

### Post by sdmike on 2007-01-03
It looks like this and every other box has no text.

[IMG]http://a146.ac-images.myspacecdn.com/images01/44/l_79165ac637aee84e104adc11c9a62bd9.png[/IMG]

---

### Post by Shatrat on 2007-01-03
I believe you need to install Tahoma font or something like that, there is a Steam and CS:S how to floating around somewhere on this forum that goes through it step by step if you search for it.

---

### Post by rekahsoft on 2007-01-03
You have to install the tahoma fonts. I have included the .ttf file so all you do is copy it to your ~/.wine/drive_c/windows/fonts directory like so:```
cp path/to/tahoma.ttf ~/.wine/drive_c/windows/fonts
```

---

### Post by sdmike on 2007-01-03
rekahsoft you are the man thank you.

---

### Post by sdmike on 2007-01-03
OMG I see text now but I can't tyoe anything into the boxes. Just when I think I'm so close I get shutdown. lol

So is there another package I need in order to type text into the boxes so I can grab my steam account?

---

### Post by Shatrat on 2007-01-03
I had this problem too, I just messed around with it till it let me.  It seems to me I switched back and forth from username ot password a few times and probably some other frantic crap before it let me do it.

---

### Post by rekahsoft on 2007-01-03
> **sdmike said:**
> OMG I see text now but I can't tyoe anything into the boxes. Just when I think I'm so close I get shutdown. lol

So is there another package I need in order to type text into the boxes so I can grab my steam account?

For some reason you are not able to type into the text box. Write what u want using a text editor, copy it, then right click on the text box and paste it in. The password boxes should work :)

---

### Post by sdmike on 2007-01-04
ok I finally logged in by right then left clicking. I installed CSS then when the game start the stupid steam window is in my way. Then I click on it to go away and the game goes away. Then I try to minimiz the steam window and the computer freezes.

What now?

:(

---

### Post by pay on 2007-01-04
Read through this [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games)
Start the game with this ```
wine steam.exe -applaunch 240
```

---

### Post by sdmike on 2007-01-04
That totally worked but why is the game lagging so much, I thought it would be a hair quicker than winders.

---

### Post by diepruis on 2007-01-04
> **sdmike said:**
> That totally worked but why is the game lagging so much, I thought it would be a hair quicker than winders.

Do you have an ATi card?

---

