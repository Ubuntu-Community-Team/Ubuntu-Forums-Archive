---
title: "Installing Doom 3"
date: 2005-12-11
forum: Gaming &amp; Leisure
---

### Post by Kobra on 2005-12-11
Ok, whats the way to install Doom 3?  I already looked at the Ubuntu Wiki, and tried downloading the binaries, but when I click on the binary on the server, it only comes up with a screen full of funky text.  Whats up with that?

---

### Post by Zelut on 2005-12-11
Could you please post a link to the Wiki instructions & also, if possible, a copy of the 'funky text' that lists on the screen?  Might help narrow down the problem..

---

### Post by Kobra on 2005-12-11
Your wish is my command:
[https://wiki.ubuntu.com/Doom3?highlight=%28Doom%29](https://wiki.ubuntu.com/Doom3?highlight=%28Doom%29)

```
)ÍŒ÷!®&Ñ$1,Ìùõ9çÞFƒ´=öÔ¦2ÉV–’ôÇý¾çÞn]¾ëß¼LŸýO~NÏNO¿{ùòÙéééÙ÷¯N·ãóâüüôÕ³³Ó/O¿ûþôûWßsü«ï¾fNŸýŸÆ×¶2æY®‹¯ûÖû¿ÓÏ¿å³wUks~pw}hÎzçæ¾LlíÌdÐ¿ºì}uæÞÈúÚ42!1/ÏÎ_œž¾ÚÛ»ÍœõÎäªW¶6i~¼´kgæEî‹Œ¿×k›'ÞØJ†ß”eQq™ÙÆôçuú˜ú´È&‡½½½»UêÃ6fQTF)66I*ç½ó&õ¾Á¯EÑä	ö2ë&«Ó2³Wlc|š/±kx‚osg*'DöŒé“œ2sX=KÁP±0O$úÉ™•}Ä–éGÐÅu°#þ13—O˜úÔ,šº©âz^®<Is»¶5ø0vV45dáåpRDBä66›°Ú]˜U]—''OOO½Œž÷@ÙÛãVØ?år63µ›¯òtŽ¿V.+ÍSZ¯‚\ââÞ9Ùñø¯ÝZµ1§*dFGVÿ½ÄìííÝŒïSóf<1×ã+s?L¦{_¶‘c3¬)²ÊQé.§…
›oLã¡u‘¤°BÎ¼¾¹ÏœË!D¸n–qR!ä’És“¤X¯.ª
FaéuñHÓq•»LÎ1!ZNÏÜ*¤²»Û7ìO•i72f&v[bæ,òó$	{!a¹{2gi+ÄÌ³<÷‚ÔDhÓáÍÛÑÀÜŽúïøÖÿqpeÞö¯¿!Ä/ÈôÞÂèÉ2HÂ»Úl¨Ã²*–túÍÙ=RÔ¶ä[¡lÞT•Ëëlc¼¥ôÒ¼g~ZAäYa®nÃ5²Ø:‚i
Ù©AÏÜ2Í9^ä€‡Ü¤µ®´ÂºØ†ªJóÚÎëÞ7éçª7érU¯I§à<¯1¥g†‹ÈÉá2à°ýºÖlYfÝÈIpÓ½ŽdÙ0wjY•;v¹¥^SF+™Ð«ƒå‡<.vÈˆ±¨!™ û:å(:B‘¯ÕF3Ûäó•Þ–`Æ²|—pâWÅ5ÖSˆ*óZ+JšìŽý4¼9a®WÃËþl~ø#jðóàòþ®ÿz4ø=æÔZÕ±ég¾ˆÛ²Ô‰^lÍOiŽ=1€>„að`Z–ûèæJGãÈ!Ò‡×žŒQ
Mn£1^—¡™00Zsye.WnþÐ3ï¡›¹…Š¼ÔFÄœBÒ@Î[ixÆ-}‘.ƒSÚNU4ËÕŽÆûVü=óTIX}_ÂÉƒ}
÷
¢½7ÿò ¸DðuÇ„ìn›üá5v•dÒOÈ¼Æ1I=ôFV3ý«û7—ÐÙ»«	Aê^R™Ë—ä|ÔU:kBxº¬eRÈ‘yfÈ6!ÎõCž]» µŠï*zÿÌ€#Kî
ÓÔi–þê~‹ÑfúŠX±e ¼â$ó²wº•à¹* `òåÐ44/©‘7„èL½ qµM3h“±ÊA
```

---

### Post by gpw797 on 2005-12-12
I followed the instructions here 

[http://zerowing.idsoftware.com/linux/doom](http://zerowing.idsoftware.com/linux/doom)

and it worked fine.

---

### Post by IYY on 2005-12-12
Have you actually downloaded the binary, or are you trying to open it inside your browser? If it's the second, then you should right click on the link and select the option that saves the file to your computer.

---

### Post by bb002 on 2005-12-13
I've noticed on my machine that all linux binaries (dunno why) but firefox tries to open them up as plain text files and I have to right-click save-as.

[edit]
I followed the patch instructions at gpw797's url. ID's seems to have goofed because the patch instructions aren't really patch instructions they never say to run the patch binary.You should run the patch binary before it says "Start the game with the command: doom3".

I just beat the game with no problems (other than the fact that I absolutely sucked and died alot) so I can unoffically verify that using the patch instructions as fresh installation instructions work.

Since I had since a hard time with installing nwn, i though it best to make a list of my instructions for later reference should I ever need them.

```

To install doom3:

   1) pick a install location. Replace "doom3" in the follow commands with install location.
   2) copy /Setup/data/base/pak002.pk4 from cd 1 to doom3/base/
   3) copy /Setup/data/base/pak000.pk4 and pak001.pk4 from cd 2 to doom3/base/
   4) copy /Setup/data/base/pak003.pk4 and pak004.pk4 from cd 3 to doom3/base/
   5) Download latest Doom3 linux patch from "ftp://ftp.idsoftware.com/idstuff/".
   6) run patch downloaded in step 5 and install it to doom3/
   7) Play game or install expansion.

To install doom3 expansion:

   1) copy d3xp/pak000.pk4 from expansion cd to doom3/d3xp/


```

---

### Post by Curlydave on 2005-12-13
Step 1: Download the Doom3 installer, preferably the latest one with patch 3.

Step 2: Open the readme file within

Step 3: Copy the .pak files specified in the readme from the Doom3 CDs to the base directory created by the Doom3 installer.

Step 4: Launch Doom3, and set the sound to OSS. 

There you go!

---

