---
title: "Fujitsu-Siemens Amilo A 1640/1650 and Ubuntu?"
date: 2005-06-30
forum: Desktop Environments
---

### Post by Morimando on 2005-06-30
Monday or Tuesday, finally my new notebook will arrive. It's gonna be an Amilo 1640 with a Sempron 3000+ built in, that according to the data sheet is a 64bit processor.
Will Ubuntu be working with this? Since i don't remember specialties for F-S laptops in any kernel i'm not to sure. I hope Ubuntu'll work with it, i'll first gonna try the Ubuntu 64bit edition :)
Does anyone know about F-S notebooks and Ubuntu? I'd be very happy to hear it'll work without problems, and if there are problems, i'd be very pleased to know if they can be solved and how.
Thanks in advance, chaps!

---

### Post by psoleko on 2005-06-30
The sempon processor family does not have 64-bit instructions, Some are based on the Athlon64/Opteron core but have the extra 64 bit instructions and registers disabled. Some Semprons are based on the Barton core Socket A processors. Not sure which one is in your laptop although it appears to be the Socket A variant. Install regular Ubuntu i386 then at the console type the command 
uname -m 
if it says i686 you have an athlon64 based sempron, if it says k7, you have the socket A variety. Let me knwo if I can be of any more help. 
Good Luck!

---

### Post by Morimando on 2005-06-30
Thanks for that info for starters, i searched the net for about a week now (well not all the time though), but just could find out that some sempron are 64bit and some are not. In the technical data from F-S it says the Sempron in Amilo A series IS a 64bit, but i can't quite validate this, till my notebook arrives.
 I'll do as you told me and then  i'll post again here, as soon as my notebook arrives, which, unfortunately, will most likely be monday or tuesday. I had hoped the person i bought it from (eBay) to send it so it arrives before the weekend, but she doesn't seem to be a person that gives a shit about the wishes of those that buy things from her ^^ well, however i'll be here then.

---

### Post by Morimando on 2005-06-30
[QUOTE=psoleko]
uname -m 
if it says i686 you have an athlon64 based sempron, if it says k7, you have the socket A variety. Let me knwo if I can be of any more help. 
Good Luck![/QUOTE]
weird thing though, that when i execute the said command on my Athlon XP+ 2400 it shows i686... did i fail to notice my Athlon is a 64bit thoroughbred, or is it just an error?  :smile: 
well must be that my computer just ROCKS ;)  \\:D/

---

### Post by barbarian on 2005-06-30
Hello, I have exactly the same notebook. All functions works pretty well even display, thaks to [Herr Winischoffer](http://www.winischhofer.at/linuxsisvga.shtml)  But my pcmcia wireless card is not recognizied, unfortunatelly.. ](*,) 

I'm planning to try Susse 9.3..

---

### Post by Morimando on 2005-07-01
[QUOTE=barbarian]Hello, I have exactly the same notebook. All functions works pretty well even display, thaks to [Herr Winischoffer](http://www.winischhofer.at/linuxsisvga.shtml)  But my pcmcia wireless card is not recognizied, unfortunatelly.. ](*,) 

I'm planning to try Susse 9.3..[/QUOTE]
Hmm well i hope that WiFi won't be a problem since it's integrated with the Sempron processor.. thanks for the link regarding the SiS graphics chipset, i'll have a look at it as soon as my notebook arrives :) 
But whatever happens, i'll never put a SuSe on my laptop  [-X  ;-) however, i'm thinking about trying Fedora Core 4 ... but i guess i'll stick to Ubuntu (in case the Sempron should really be 64bit i'll maybe install Gentoo again, since the compile times seem to be a lot better with 64bit)

---

### Post by barbarian on 2005-07-01
By the way, Amilo A1630 has 64bit Athlon processor , Amilo A1640 - 32bit Sempron.
Afaik, there is no integrated WiFi chipset in f-s amilo A1640.

for:
pretty large hd - 60GB
DVD writer
1280 x 800 display
512 MB ram

cons:
poor perfomance share video chipset SiS M760.
there is no integrated WiFi chipset.

---

### Post by Morimando on 2005-07-01
[QUOTE=barbarian]By the way, Amilo A1630 has 64bit Athlon processor , Amilo A1640 - 32bit Sempron.
Afaik, there is no integrated WiFi chipset in f-s amilo A1640.

for:
pretty large hd - 60GB
DVD writer
1280 x 800 display
512 MB ram

cons:
poor perfomance share video chipset SiS M760.
there is no integrated WiFi chipset.[/QUOTE]
afaik WLAN is integrated with the Sempron. The SiS is indeed not the best graphics chip, but well... i need it for university, not for gaming, for gaming, my desktop is fully functional.
As for the 64bit => the 1640 is listed with Sempron 2800 which is 32bit, but on eBay the model I bought is listed with Sempron 3000, which afaik is the first of the 64bit Sempron series. But it could as well be that the Sempron 3100 is the first 64bit Sempron ^^ We'll see,,

---

### Post by Morimando on 2005-07-01
I'm somewhat unsure about things ... it says it's an Amilo A 1640-GGX2, but there seems to be no "offical" Amilo with the suffix GGX2 around. does anyone know how the "GGX2" makes the notebook different?
Is there even any change?

---

### Post by barbarian on 2005-07-01
Waw, you brave man to buy such thigs as notebook on Ebay :) 
I've bought mine from Fujitsu-Siemens authorized vendor, ofcorse, perhaps, mine cost more. But 2 years waranty, it goes to part 'for'. By the way, Herr Winischoffer is slightly wrong -  Windows driver doesn't show any horisontal splashes while you watch movie on TV,as he has writed on his website. I have dual boot WinXP & Ubuntu. So I have tested  both. Maybe I tweaked my xorg not enough, but still..

Maybe someone knows the solution to accelerate SiS M760 / 760 chipset perfomance it would be cool :roll:

---

### Post by Morimando on 2005-07-01
I also got 2yrs warranty, too.. directly from F-S since the notebook is completely new and unused ^^

---

### Post by barbarian on 2005-07-02
[QUOTE=barbarian]I'm planning to try Susse 9.3..[/QUOTE]

Or I will wait breezy..

---

