---
title: "How to set a fixed timezone for Mate"
date: 2022-09-26
forum: Desktop Environments
---

### Post by broiledsmurf on 2022-09-26
Hello, 

I'm wanting to set a fixed timezone for my machine.  In other words, I don't want it to try and autodetect my timezone anymore.  I want to set it to a certain timezone, and I want it to "stay put."  Sadly, the Date and Time Manager for Mate is not working the way it should.  It asks me to authenticate before it opens, which is fine.  However, once it opens, all the controls are "locked" and there is no "unlock" button.  I am unable to change anything in the dialog.  Any ideas on how to fix this?

I'm using Mate 1.26.0 and Ubuntu 22.04

Thank you for taking a look.

---

### Post by #&amp;thj^% on 2022-09-26
Check for available timezones in the system.

```
timedatectl list-timezones
```
Search for your timezone from the list of available timezones. 
or use something like:
```
 timedatectl list-timezones | grep -i America
```
resluts:
```

America/Adak
America/Anchorage
America/Anguilla
America/Antigua
America/Araguaina
America/Argentina/Buenos_Aires
America/Argentina/Catamarca
America/Argentina/ComodRivadavia
America/Argentina/Cordoba
America/Argentina/Jujuy
America/Argentina/La_Rioja
America/Argentina/Mendoza
America/Argentina/Rio_Gallegos
America/Argentina/Salta
America/Argentina/San_Juan
America/Argentina/San_Luis
America/Argentina/Tucuman
America/Argentina/Ushuaia
America/Aruba
America/Asuncion
America/Atikokan
America/Atka
America/Bahia
America/Bahia_Banderas
America/Barbados
America/Belem
America/Belize
America/Blanc-Sablon
America/Boa_Vista
America/Bogota
America/Boise
America/Buenos_Aires
America/Cambridge_Bay
America/Campo_Grande
America/Cancun
America/Caracas
America/Catamarca
America/Cayenne
America/Cayman
America/Chicago
America/Chihuahua
America/Coral_Harbour
America/Cordoba
America/Costa_Rica
America/Creston
America/Cuiaba
America/Curacao
America/Danmarkshavn
America/Dawson
America/Dawson_Creek
America/Denver
America/Detroit
America/Dominica
America/Edmonton
America/Eirunepe
America/El_Salvador
America/Ensenada
America/Fort_Nelson
America/Fort_Wayne
America/Fortaleza
America/Glace_Bay
America/Godthab
America/Goose_Bay
America/Grand_Turk
America/Grenada
America/Guadeloupe
America/Guatemala
America/Guayaquil
America/Guyana
America/Halifax
America/Havana
America/Hermosillo
America/Indiana/Indianapolis
America/Indiana/Knox
America/Indiana/Marengo
America/Indiana/Petersburg
America/Indiana/Tell_City
America/Indiana/Vevay
America/Indiana/Vincennes
America/Indiana/Winamac
America/Indianapolis
America/Inuvik
America/Iqaluit
America/Jamaica
America/Jujuy
America/Juneau
America/Kentucky/Louisville
America/Kentucky/Monticello
America/Knox_IN
America/Kralendijk
America/La_Paz
America/Lima
America/Los_Angeles
America/Louisville
America/Lower_Princes
America/Maceio
America/Managua
America/Manaus
America/Marigot
America/Martinique
America/Matamoros
America/Mazatlan
America/Mendoza
America/Menominee
America/Merida
America/Metlakatla
America/Mexico_City
America/Miquelon
America/Moncton
America/Monterrey
America/Montevideo
America/Montreal
America/Montserrat
America/Nassau
America/New_York
America/Nipigon
America/Nome
America/Noronha
America/North_Dakota/Beulah
America/North_Dakota/Center
America/North_Dakota/New_Salem
America/Nuuk
America/Ojinaga
America/Panama
America/Pangnirtung
America/Paramaribo
America/Phoenix
America/Port-au-Prince
America/Port_of_Spain
America/Porto_Acre
America/Porto_Velho
America/Puerto_Rico
America/Punta_Arenas
America/Rainy_River
America/Rankin_Inlet
America/Recife
America/Regina
America/Resolute
America/Rio_Branco
America/Rosario
America/Santa_Isabel
America/Santarem
America/Santiago
America/Santo_Domingo
America/Sao_Paulo
America/Scoresbysund
America/Shiprock
America/Sitka
America/St_Barthelemy
America/St_Johns
America/St_Kitts
America/St_Lucia
America/St_Thomas
America/St_Vincent
America/Swift_Current
America/Tegucigalpa
America/Thule
America/Thunder_Bay
America/Tijuana
America/Toronto
America/Tortola
America/Vancouver
America/Virgin
America/Whitehorse
America/Winnipeg
America/Yakutat
America/Yellowknife
```
to set your value use as an example:
```
sudo timedatectl set-timezone Asia/Tokyo
###or:
sudo timedatectl set-timezone America/Denver
```


The above command is similar to doing the following two manual steps:

    Unlink your currently-used timezone.

```
sudo unlink /etc/localtime
    [sudo] password for user:
```

    Link /etc/localtime to your new timezone.

```
sudo ln -s /usr/share/zoneinfo/Asia/Tokyo /etc/localtime
```

Confirm changes using "timedatectl". 
```
timedatectl
               Local time: Mon 2022-09-26 16:17:47 MDT
           Universal time: Mon 2022-09-26 22:17:47 UTC
                 RTC time: Mon 2022-09-26 16:17:47
                Time zone: America/Denver (MDT, -0600)
System clock synchronized: yes
              NTP service: active
          RTC in local TZ: yes

```

---

### Post by TheFu on 2022-09-26
Does putting the desired timezone into /etc/timezone and rebooting not work?
```
$ more /etc/timezone 
America/New_York
```

I don't know if a GUI tool will override the system default, once it has been set - I'd expect it would since the GUI is a positive user actions on a per-user basis.  You can also set the TZ environment variable in your shell startup file. For bash, it would be 
```
$ more ~/.bashrc
export TZ="America/New_York"
```

If the timezone uses daylight savings or not, that change will happen automatically ... or not.  It is possible to for a "UTC+6" timezone too.

If that doesn't work, 
```
$ sudo tzselect 
```
should effectively do the same things, just with a TUI. tzselect can be used with coordinates in ISO 6709 notation as well, so "40 degrees 42 minutes north, 74 degrees 3 minutes west." becomes "+4042-07403" entered into the tool. That's the example they show. I've never tried it.

None of what I've posted is Mate specific.  Does the Mate User's Guide have different instructions?  A quick search didn't find that - the MateWiki seems to be about building Mate for developers, not what to point-n-click for end-users.

---

### Post by broiledsmurf on 2022-09-26
Thank you!  This worked perfectly.  When I restarted the machine, it kept the timezone that I set.

---

### Post by #&amp;thj^% on 2022-09-27
You had two reply's for two different methods here, could you point to the one that worked for you. please!
For the sake of clarity.
I am however glad one worked out for you.
EDIT: FTR both methods will work on Ubuntu..I .wanted that to be clear. ;)

---

