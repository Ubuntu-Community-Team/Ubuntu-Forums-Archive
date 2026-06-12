---
title: "If I'm runing a skype so I can only hear the skype or only the game? How can I hear b"
date: 2008-10-25
forum: Gaming &amp; Leisure
---

### Post by Turge on 2008-10-25
If I'm runing a skype so I can only hear the skype or only the game? How can I hear both of them?

I want to hear the game and the guy I'm talking with him and if I'm playing and the skype is runing I can hear only the skype but if the skype is not running i can hear the game.

Anyone knows maybe how can I fix that problem?

---

### Post by cantormath on 2008-10-25
Sounds like a gamer is trying to cheat....... :lolflag:

---

### Post by crazyfuturamanoob on 2008-10-25
I got the same problem. If I try to play fps game and put some good music playing with totem, I hear only another, not both.

---

### Post by Turge on 2008-10-25
Somebody know how can we fix that problem?

Thank you.

---

### Post by JonahRowley on 2008-10-25
Do you have integrated sound with no hardware mixer?  If so, I think there's a way to enable ALSA software mixing to allow more than one program access to the sound hardware at the same time.

---

### Post by crazyfuturamanoob on 2008-10-25
My sound card is HDA NVidia and chip is Realtek ALC268, does that help? How to enable that software mixing thing?

---

### Post by Turge on 2008-10-25
> **JonahRowley said:**
> Do you have integrated sound with no hardware mixer?  If so, I think there's a way to enable ALSA software mixing to allow more than one program access to the sound hardware at the same time.
My sound card is "HDA intel (Alsa Mixer)".
there is any software for that?

---

### Post by Turge on 2008-10-25
Someone?

---

### Post by Turge on 2008-10-25
> **Turge said:**
> My sound card is "HDA intel (Alsa Mixer)".
there is any software for that?

Can I get that software please?
Or the name of the software or something please?

Thank you.

---

### Post by crazyfuturamanoob on 2008-10-26
> **Turge said:**
> Can I get that software please?
Or the name of the software or something please?

Thank you.

Alsa? OpenAL?

---

### Post by loell on 2008-10-26
before i used to do it in **gnome-alsamixer** , i'm not sure if it still could work today since i didn't touch my pulseaudio.

---

### Post by meborc on 2008-10-26
basically... it should work... but the pulseaudio configuration has been a total mess in ubuntu, so for now, only one program can access sound...

you can change all your sound to ALSA in system-preferences-sound and also in audacious (for music) preferences use ALSA output... this could work

OR if you want to keep pulseaudio, and fix it to work on multiple programs at once, use this perfect guide to do it - [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900) or this [http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965) depending on your system

:guitar:

---

### Post by Turge on 2008-10-26
> **crazyfuturamanoob said:**
> Alsa? OpenAL?
I don't know it's just say there "HDA Intel (Alsa Mixer)".
It's doesn't say there any OpenAL.

What now?

---

### Post by Turge on 2008-10-27
> **meborc said:**
> basically... it should work... but the pulseaudio configuration has been a total mess in ubuntu, so for now, only one program can access sound...

you can change all your sound to ALSA in system-preferences-sound and also in audacious (for music) preferences use ALSA output... this could work

OR if you want to keep pulseaudio, and fix it to work on multiple programs at once, use this perfect guide to do it - [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900) or this [http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965) depending on your system

:guitar:

Ok I don't use any pulseaudio everything in system-preferences-sound already was in Alsa.

Any more things that could help?

---

### Post by Turge on 2008-10-28
> **Turge said:**
> Ok I don't use any pulseaudio everything in system-preferences-sound already was in Alsa.

Any more things that could help?

???????????

---

### Post by derekr44 on 2008-10-29
You basically want those two programs to use the same driver.  Like sharing resources.

---

### Post by 080812jk on 2008-10-30
&#12290;&#12290;&#65288;&#25105;&#26159;[**&#35895;&#27468;&#20248;&#21270;**](http://www.bjgoogleyh.cn/googleyh/index.html)&#36825;&#37324;&#32473;&#22823;&#23478;&#32463;&#39564;&#30340;&#65289; &#22823;&#23478;&#21040;&#30334;&#35835;&#25628;&#19979;&#23601;&#30693;&#36947;&#65306;[**&#35895;&#27468;&#20248;&#21270;**](http://www.bjgoogleyh.cn/googleyh/index.html)&#19977;&#22269;&#32676;&#33521;&#20256;6&#20813;&#36153;&#19979;&#36733; &#21435;&#30475;&#19979;[**&#35895;&#27468;&#20248;&#21270;**](http://www.bjgoogleyh.cn/googleyh/index.html)&#26159;&#19981;&#26159;&#31532;&#19968;&#39029;&#31532;7&#26465;&#19977;&#22269;&#32676;&#33521;&#20256;6&#19979;&#36733; &#26159;&#19981;&#26159;&#31532;&#20108;&#39029; &#20498;&#19977;&#65288;&#36825;&#20010;&#20851;&#38190;&#27425;&#19981;&#33021;&#38752;&#21069;&#30340;&#21407;&#22240;&#26159;&#30334;&#24230;&#27809;&#26377;&#26356;&#26032;&#25105;&#36825;&#19968;&#36148;&#30340;&#35760;&#24405;&#65292;&#37027;&#37324;&#26174;&#31034;&#30340;&#36824;&#26159;.&#19977;&#22269;&#32676;&#33521;&#20256;6&#39640;&#36895;&#19979;&#36733;&#65289;&#25110;&#32773;&#22823;&#23478;&#29992;&#65306;&#19977;&#22269;&#32676;&#33521;&#20256;6&#39640;&#36895;&#19979;&#36733; &#26159;&#19981;&#26159;&#25490;&#31532;&#19968; &#65292;&#22823;&#23478;&#20063;&#21487;&#20197;&#28857;&#30334;&#24230;&#30340;&#35760;&#24405;&#30475;&#19979;&#25105;&#36825;&#19968;&#36148;&#21457;&#30340;&#26102;&#38388;ps:&#27969;&#30528;&#26202;&#19978;&#25110;&#32773;&#26126;&#22825;&#32487;&#32493;&#65288;&#36825;&#20063;N&#20851;&#38190;&#65292;&#25105;&#23601;&#26159;&#27809;&#26377;&#22788;&#29702;&#22909;&#36825;&#37324;&#30340;&#19968;&#28857;&#65292;&#22909;&#22810;&#27809;&#26377;&#34987;&#25910;&#24405;&#38752;&#21069;&#65289;&#12290;&#12290;&#19981;&#28982;&#19968;&#22825;&#33267;&#23569;&#21487;&#20197;&#24102;&#26469;&#22909;&#20960;&#21315;&#65292;&#24212;&#35813;&#25105;&#30005;&#24433;&#21306;&#19981;&#20570;&#20248;&#21270;&#65292;&#22914;&#26524;&#20248;&#21270;&#20102;&#19981;&#30693;&#36947;&#30005;&#24433;&#33021;&#24102;&#26469;&#22810;&#23569;&#12290;&#12290;&#21621;&#65281;&#65281;&#26202;&#19978;&#32487;&#32493;&#12290;[**google&#25216;&#26415;**](http://www.bjgoogleyh.cn/googlejs/index.html)&#12290;[url=http://www.bjgoogleyh.cn/googlejs/index.html]**google&#25216;&#26415;**[/url&#37027;&#19968;&#31867;&#20851;&#38190;&#35789;&#21069;5&#24038;&#21491;&#30340;&#27604;&#36739;&#22909;&#12290;&#12290;&#36825;&#26679;&#30340;&#25628;&#32034;&#29575;&#20063;&#27604;&#36739;

---

### Post by meborc on 2008-10-31
> **Turge said:**
> ???????????

well, i know you can do it both with alsa and with pulseaudio.. i would try it with pulseaudio with one of the links i provided... those links show how to fix pulseaudio to work fine in ubuntu... try it out!

---

