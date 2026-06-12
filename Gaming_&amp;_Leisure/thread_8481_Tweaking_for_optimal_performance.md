---
title: "Tweaking for optimal performance"
date: 2004-12-17
forum: Gaming &amp; Leisure
---

### Post by erpe on 2004-12-17
I'm running America's Army under Ubuntu (which now is my main OS). However i was wondering if you pro-user out there could share some tips on how to tweak the performance of the Ubuntu distro for gaming.

i notice a slight drop in performance in America's Army (an avarage decrease of 10 fps) in comparision to AA running under Win XP.

I have an Athlon XP with an radeon 9600 XT graphics card.

---

### Post by jdodson on 2004-12-18
[QUOTE=erpe]I'm running America's Army under Ubuntu (which now is my main OS). However i was wondering if you pro-user out there could share some tips on how to tweak the performance of the Ubuntu distro for gaming.

i notice a slight drop in performance in America's Army (an avarage decrease of 10 fps) in comparision to AA running under Win XP.

I have an Athlon XP with an radeon 9600 XT graphics card.[/QUOTE]

i know that in the case of doom for win xp the developers said they do some visual c++ optimizations that gcc does not support.  they said it made the winxp version a bit faster.  they were working on speed optimizations for gcc, however it might or might not come later.  i know that developers will optimize for visual c++ and just gcc it with no optimizations because people are generally happier just to get a gnu/linux port.  i think the optimzations thing(out of your control) is a reason.,

i also think there might be some tweaks you can do to speed things up.  however, i know of none:)  anyways, i guess this wasnt much help..... ok i will stop typing now :mrgreen:

---

### Post by erpe on 2004-12-18
Lol , We'll thanks for replying  anyway. In the meantime i tried some tweaking of  my own (installing the newest radeondrivers from stanchina.net) and all i got was an broken ubuntu (somethging with XF86Config-4 ) And no clue how to fix this.  :?

---

### Post by AndersAA on 2004-12-18
[QUOTE=erpe]Lol , We'll thanks for replying  anyway. In the meantime i tried some tweaking of  my own (installing the newest radeondrivers from stanchina.net) and all i got was an broken ubuntu (somethging with XF86Config-4 ) And no clue how to fix this.  :?[/QUOTE]


XF86Config-4 is in /etc/X11/XF86Config-4, you can try changing "ati" to "radeon" in the driver section if you broke your ati (or radeon) driver.

---

### Post by p!=f on 2004-12-18
You might want to try to build a kernel based on Con Kolivas patchset which is aimed at performance which doesn't mean it's not stable. :)
For more informations follow links below.

Con Kolivas kernel patch homepage:
[http://members.optusnet.com.au/ckolivas/kernel/](http://members.optusnet.com.au/ckolivas/kernel/)

Patchets based on -ck:
CKO patchset:
[http://kem.p.lodz.pl/~peter/cko/](http://kem.p.lodz.pl/~peter/cko/)
Nitro sources:
[http://sepi.be/nitro.php/](http://sepi.be/nitro.php/)

Both CKO and Nitro are worth a try.

---

### Post by lameaim on 2004-12-18
Try playing around with hdparm.  eg. [http://linuxtimes.net/modules.php?name=News&file=article&sid=457](http://linuxtimes.net/modules.php?name=News&file=article&sid=457)

---

### Post by erpe on 2004-12-18
[QUOTE=AndersAA]XF86Config-4 is in /etc/X11/XF86Config-4, you can try changing "ati" to "radeon" in the driver section if you broke your ati (or radeon) driver.[/QUOTE]

It's a bit offtopic but i was wondering how i must edit the config-4 file (i got only the commandline at my disposal).  I have 'cd to  /etc/X11 and tried the command "sudo gedit XF86Config-4," but that wasn't working   :-| . Do you know how edit this file from the commandpropt? 


And thanks for the tweaking tips!, they look very promising, i can't wait to try them out!  :grin:

---

### Post by astoltz on 2004-12-18
[QUOTE=erpe]It's a bit offtopic but i was wondering how i must edit the config-4 file (i got only the commandline at my disposal).  I have 'cd to  /etc/X11 and tried the command "sudo gedit XF86Config-4," but that wasn't working   :-| . Do you know how edit this file from the commandpropt?[/QUOTE]

gedit only works in gnome (I guess that's not exactly correct, but close enough) which is why it's not starting.  Try:
```
sudo nano /etc/XF86Config-4
```

---

### Post by erpe on 2004-12-20
Ok guys thanks for tips  :-D

---

### Post by audscott on 2005-03-10
[QUOTE=erpe]It's a bit offtopic but i was wondering how i must edit the config-4 file (i got only the commandline at my disposal).  I have 'cd to  /etc/X11 and tried the command "sudo gedit XF86Config-4," but that wasn't working   :-| . Do you know how edit this file from the commandpropt? 


And thanks for the tweaking tips!, they look very promising, i can't wait to try them out!  :grin:[/QUOTE]

I got ahold of the pressed X86 & AMD 64 loaders, had a ball all weekend - I had one consistent problem regarding the XF86Config file (?etc/X11/XF86Config-4).  It seems in AMD 64 after editing the file to get my MX1000 mouse clicking on all buttons I could not get back into GUI.  I'd get a "screen not found.

DFI Nforce3 board, A64 3200, DVD, ls120, GeForce 6800 GT, Ultra 500 watt PSU, Old WD drive laying around as slave on IDE channel 2.

I don't want this to be verboise:  This wold be after suceesfully laoding Nvidia driver (apt-get install nvidia-glx) and setting driver perameters (nvidia-glx-config enable).  If I didn't edit the Config-4 file, I can alt/contr f1 to leave and f7 return to GUI, reboot into GUI and edit several other files with incident - but after 10, maybe 12 loads (I told you I had fun), this one the consistent problem I just couldn't find a resolution.

Can anyone give me specific instruciton or direction?

I should mention, I'm an old time XP user whp has desperately sought an alternative, so am a Linux newby will to work hard to get a descent Linux box going.   Ubuntu rocks!!  :D

---

### Post by purcel116433 on 2007-05-15
> **erpe said:**
> Lol , We'll thanks for replying  anyway. In the meantime i tried some tweaking of  my own (installing the newest radeondrivers from stanchina.net) and all i got was an broken ubuntu (somethging with XF86Config-4 ) And no clue how to fix this.  :?


[Yahoo chemistry Equity Line Credit Bankruptcy physics](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/incest-porn.html)

---

