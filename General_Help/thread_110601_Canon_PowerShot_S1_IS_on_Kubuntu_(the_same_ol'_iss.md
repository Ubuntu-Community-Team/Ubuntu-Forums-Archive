---
title: "Canon PowerShot S1 IS on Kubuntu (the same ol' issue)"
date: 2005-12-31
forum: General Help
---

### Post by branco on 2005-12-31
Just like many users of Ubuntu/Kubuntu, I have also been experiencing troubles with USB digital camera. BTW, I am a newbie in the Linux world, so I must ask you to make your answers (if any) a bit more detailed, TIA. :)

My digicam used to work happily under 5.04 Hoary. But after updating to Breezy, it stopped working. At first, no USB device except my HP LaserJet printer worked. But my brother plugged in his mp3 player and suddenly all USB storage devices worked (?!). However, the digicam still doesn't work. I have tried to make a couple of GUI apps (actually gThumb and Digikam) recognize my Canon PowerShot S1 IS. Both recognized the device as "Canon PowerShot S1 IS (normal mode)", which is okay, I guess.

In gThumb, the 'Import Photos' dialogue halts at "lock keys failed" error. Digikam just said it could not connect to the camera. The KDE System Settings is unable to do anything with the device.

Although no icon is placed on the KDE desktop, I did try to type "camera://Canon PowerShot S1 IS (normal mode)@[usb:002,002]/" into the Konqueror address bar. The status bar said something to the effect that the camera was detected but the final result was that Konqueror said: "Could not read file /."

The listing of "/proc/bus/usb/devices" yields (among other things) the following:

```
T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=04a9 ProdID=309c Rev= 0.01
S:  Manufacturer=Canon Inc.
S:  Product=Canon Digital Camera
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=06(still) Sub=01 Prot=01 Driver=(none)
E:  Ad=01(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   8 Ivl=96ms
```

(Needless to say, I have no idea what this is. I've just seen this listing quoted in a thread, so I did the same).

Last lines in "/var/log/messages" look like this:

```
Dec 31 12:14:19 localhost kernel: [4296173.880000] ohci_hcd 0000:00:02.1: wakeup
Dec 31 12:14:19 localhost kernel: [4296174.115000] usb 2-1: new full speed USB device using ohci_hcd and address 5
Dec 31 12:14:20 localhost usb.agent[11370]:      libgphoto2: loaded successfully
```

I also tried to add the following line:

/dev/sda1 /mnt/usbstorage vfat rw,user,noauto 0 0

to "/etc/fstab" but that doesn't help either.

I have also tried creating a "camera" group and adding my user to there, but that didn't help.

Moreover, I have tried running gThumg and Digikam as a superuser, but to no avail.

I'm all out of ideas (not that I had many of them). Is there an easy and elegant solution to this issue?

Other USB devices (including a scanner, a stick-drive, and an iRiver mp3 player) work just fine.

Oh, and BTW, the above applies to GNOME as well...

Well, sorry for this lengthy description...

---

### Post by branco on 2006-01-04
Just to be clear,

I'm running KDE 3.5 installed with kubuntu-desktop package over GNOME (Ubuntu). So, basically I'm running a Kubuntish system. ;) 

Anyway, the Digikam and (lib)gphoto2 both auto-detect my camera as "Canon PowerShot S1 IS (normal mode)", which is correct. However, trying to access the camera this way is a no-go for (lib)gphoto2 because there is a bug that makes (lib)gphoto2 fail when trying to lock the camera (I suppose in order to stop it from automatically powering down). :confused: 

To bypass this, I manually added a "Canon PowerShot S1 IS (PTP mode)" in order to access the camera. I don't know what implications might this have other than my camera just working. If anyone knows something, please tell me. :p

---

### Post by brainkilla on 2006-01-05
PTP mod ne moze i nece imati bilo kakve negativne posledice na rad sistema, to je samo Canonov fazon da ima svoj protokol (Picture Transfer Protocol) i gnjavi ljude... ako ti aparat radi u PTP modu, probaj da iskljucis tu opciju na samom aparatu, pa onda ponovo odradi --auto-detect iz gphoto2 ili digikama/gthumba. Mene muci druga stvar - moj aparat koji radi kao USB disk ne mogu da sprijateljim sa Digikamom, jer se opcija za Mass Storage koja je uvek postojala u delu Add Camera tu vise ne nalazi! Postoji samo USB PTP ali USB Mass Storage ne? AKo mozes da me prosvetlis, molim te da to ucinis ;)

Ok, sorry for 'speaking' Serbian, but it would be little odd to address branco in English. I need help with Digikam too, but my problem lies in a fact I have a USB Mass Storage camera which cannot be selected in Digikam Add Camera wizard, since the regular option for choosing UMS camera is simply missing! Any help would be greatly appreciated...

---

### Post by branco on 2006-01-05
The Digikam USB Mass Storage can be found in the 'Camera Selection' section. I don't know if you've just missed it, but do check it out. BTW, I'm using Digikam version 0.7.2 on KDE 3.5, so if you haven't updated yet, maybe that's the issue...

Anyway, check out the attached screenshot.

If you want to update, I think Kubuntu repos are the ones you should use. Just in case, those are:

deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main
deb-src [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main

I have ditched Ubuntu (and GNOME) completely, so those are the main update repos for me at the moment.

Nadam se da ti je ovo bilo od ikakve pomo&#263;i...

Moj Canon ne podr&#382;ava isklju&#269;ivanje PTP moda... Ta&#269;nije nema nikakvih opcija za PTP ili bilo koji drugi mod pristupa. Uostalom taj bag je prijavljen na sourceforge.com. Izgleda da nije do kernela nego ba&#353; do glibphoto2.

Ina&#269;e, da li ti je poznato i&#353;ta o novom anti-piratskom zakonu? &#268;uo sam da &#263;e zabraniti "slanje i prijem CD-a iz inostranstva". Ne znam da li &#263;e se to ikako odnositi i na Ubuntu, ali bilo bi mi veoma &#382;ao da ne dobijem diskove narednih verzija.

Pozdrav :smile:

---

### Post by brainkilla on 2006-01-06
@Attached Thumbnails ;)
Upravo ti to pricam, ja jednostavno nemam tu opciju u Digikamu! Ne znam kako i zasto, Digikam koristim od verzije 0.5 i nikada nisam imao ovaj problem... Instalirao sam verziju 0.8 iz nekog nezvanicnog repozitorijuma, pomislio da je lose kompajlirana, instalirao svoj .deb Osmice koji sam furao na Sidu pre par meseci, medjutim isto... Udjem u KDE da probam, isto... Nije da cu bas da riknem bez Digikama, ali ipak sije ostale programe za dve duzine. Hvala na pomoci u svakom slucaju. I poseti [http://ubuntu.fsn.org.yu](http://ubuntu.fsn.org.yu) i [http://gnuzilla.fsn.org.yu](http://gnuzilla.fsn.org.yu) - prva adresa je forum srpskog LoCo tima ciji sam clan a drugi casopisa GNUzilla, magazina za slobodan softver. p0z i hvala

---

### Post by branco on 2006-01-06
E jebiga... Ne znam bas toliko o linux-u da bih mogao da ti pomognem...na zalost. Hehe, poceo sam da ga koristim tek negde od septembra. Hvala za linkove. Obavezno cu ih pogledati.

---

### Post by brainkilla on 2006-01-06
Ma to je neka glupost, da li kamera io-slave ili nesto drugo (gphoto, sam digikam gone berserk...), resice se kao i uvek. Uglavnom, drago mi je da vidim ljude iz Srbije da koriste Linux/Ubuntu, i da su zadovoljni. Poseti ove linkove, a ako citas SK pogledaj moj tekst o igrama na Linuxu u poslednjem broju 8-) ;)

---

