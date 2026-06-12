---
title: "Neo-Geo Emulator For Linux"
date: 2010-08-28
forum: Gaming &amp; Leisure
---

### Post by MaximB on 2010-08-28
Hello !

In Windows there is the NeoRageX neo-geo emulator, but none of it's and other "mame" roms work under any Linux neo-geo emulator : kamefu, kxmame and gmameui.
It always gives errors on every rom I chose.

I've tried it with neo-geo specific roms that are used with NeoRageX and specific neo-geo emulators, and also with Mame neo-geo roms.
none of them work.

Why ? 
Is there any Linux neo-geo emulator that is up to the job ?

P.S
Are those Emulators come with everything needed (except roms) ? 
Do I need to get the bios manually, if so where do I put it ?

Thanks
Maxim.

---

### Post by CharmyBee on 2010-08-28
NeoRageX has been long dead, no one really uses it anymore. It's very old and it's very broken. Players of that moved on to Kawaks in Windows.


MAME is your best bet from the top of my head.

---

### Post by aweasd on 2010-08-28
try using XGngeo (a front-end for GnGeo)

---

### Post by honeybear on 2010-08-29
try mame, the new one, it works fine

or gngeo

>  ('neo geo pocket', 'ngp',
                ('GENERIC', 'mednafen', ' ', '', [ 'ngp', 'zip' ] )),

('Neo Geo', '/neogeo',
               ('GENERIC', 'xe','--fullscreen', '/neogeo', ['sms' , 'zip' ])) ,

('Neo Geo CD', '/neogeocd',
               ('GENERIC', 'xe','--fullscreen', '/neogeocd', ['sms' , 'zip' ])) ,

('Capcom CPS1n2', '/cpschanger',
        ('GENERIC', 'xmame.SDL', '-fullscreen -scale 2 -jt 5', '',  [ 'bin' ,  'zip' ] )) ,



---

### Post by MaximB on 2010-08-29
> **honeybear said:**
> try mame, the new one, it works fine

or gngeo

The mame from the repros doesn't work with those roms that I have.
I've installed gngeo from source but it wouldn't run (it can't find some folders), and I didn't find a 64-bit version of gngeo.

---

### Post by Cresho on 2010-08-29
im bookmarking this.  I have the best mame games out there working with all 127 plus neo geo games I have tried.  I use an x arcade stick with it as well.  It works.  Ill post something later since i just upgraded to lucid lynx and will need to work out a few things.

---

### Post by DangerOnTheRanger on 2010-09-01
It could be that it's not the emulator that's the problem, but the ROMs.
What ROMs are you trying to run?

---

### Post by MaximB on 2010-09-02
Some SNK games, like Samurai Showdown 4, KOF98, KOF2003 etc...  they work on Windows emulators.

---

### Post by aweasd on 2010-09-03
> **MaximB said:**
> The mame from the repros doesn't work with those roms that I have.
**I've installed gngeo from source but it wouldn't run (it can't find some folders), and I didn't find a 64-bit version of gngeo.**

Try installing GnGeo and Xgngeo from [here]("https://launchpad.net/~ronmi/+archive/misc/+packages"). I use it for playing KOF2002 and no problems at all, IMO it's the best Neo-Geo emu out there (Linux).

---

### Post by babai on 2010-09-03
From a certain version(i dont remember), mame dropped using the old neogeo bios, instead it uses a newer bios of larger size of about 1.3mb. Update ur bios by downloading the new neogeo.zip and all of ur roms will work just fine.

---

### Post by MaximB on 2010-09-04
> **babai said:**
> From a certain version(i dont remember), mame dropped using the old neogeo bios, instead it uses a newer bios of larger size of about 1.3mb. Update ur bios by downloading the new neogeo.zip and all of ur roms will work just fine.

Where the bios should be located (on the system, path)?

---

### Post by babai on 2010-09-04
The bios(neogeo.zip) should be placed in the folder where ur roms are located, in my machine its ~/.mame/roms/

---

