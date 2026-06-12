---
title: "Time Settings - Locations"
date: 2015-04-26
forum: Desktop Environments
---

### Post by Zoot_Nerper on 2015-04-26
Hi Folks,

I hit this problem running Ubuntu 15.04 and 14.04. In System Settings->Time and Date->Clock->Time in other locations. If I cclick on the plus to add a location and type "was" (for Washington), I might get a list of about 15 places, none of which is Washington (fair dues). If I then add an "h", then the list goes away and never comes back. Adding more characters does nothing. Any string of more than 3 chars and I get nothing. The net result is that I cannot add locations. 

Sometimes, 1, 2, or 3 chars gets nothing, particularly after the window loses focus or I attempt a second add.

I did not have this problem while in the UK (the lists would change as I typed), but have recently moved to the NE of Thailand about as far from BKK as you can get.

I am guessing that the list of locations is downloaded as you type rather than being held locally (Ubuntu documentation says you have to wait a little after typing). My Ubuntu mirrors are in BKK I think.

Anyone have this problem and maybe a solution please?

Or where are the locations held? Can I add them from the command line?

One odd thing, this morning first thing after booting up one machine (15.04), I did manage to add "London", but could not add a second. This did not happen on booting a second machine (14.04) though.

---

### Post by sandyd on 2015-04-26
Washington D.C. uses America/New_York timezone, try typing 'New York' instead.

Some additional info:
Looking into the zoneinfo folder to see whats avaliable
```

ls /usr/share/zoneinfo/
Africa      Brazil   Egypt    GB         Hongkong     Jamaica    MST      Portugal    ROK        UTC
America     Canada   Eire     GB-Eire    HST          Japan      MST7MDT  posix       Singapore  WET
Antarctica  CET      EST      GMT        Iceland      Kwajalein  Navajo   posixrules  SystemV    W-SU
Arctic      Chile    EST5EDT  GMT0       Indian       Libya      NZ       PRC         Turkey     zone.tab
Asia        CST6CDT  Etc      GMT-0      Iran         localtime  NZ-CHAT  PST8PDT     UCT        Zulu
Atlantic    Cuba     Europe   GMT+0      iso3166.tab  MET        Pacific  right       Universal
Australia   EET      Factory  Greenwich  Israel       Mexico     Poland   ROC         USv
```

In the America folder (America/zonename)
```

lrwxrwxrwx 1 root root   14 Apr 15 18:47 Adak -> ../US/Aleutian
lrwxrwxrwx 1 root root   12 Apr 15 18:47 Anchorage -> ../US/Alaska
lrwxrwxrwx 1 root root   10 Apr 15 18:47 Anguilla -> Montserrat
lrwxrwxrwx 1 root root   10 Apr 15 18:47 Antigua -> Montserrat
-rw-r--r-- 1 root root  896 Apr 15 18:47 Araguaina
drwxr-xr-x 2 root root 4096 Apr 23 14:00 Argentina
lrwxrwxrwx 1 root root   13 Apr 15 18:47 Aruba -> Lower_Princes
-rw-r--r-- 1 root root 2062 Apr 15 18:47 Asuncion
lrwxrwxrwx 1 root root   13 Apr 15 18:47 Atikokan -> Coral_Harbour
lrwxrwxrwx 1 root root   14 Apr 15 18:47 Atka -> ../US/Aleutian
-rw-r--r-- 1 root root 1036 Apr 15 18:47 Bahia
-rw-r--r-- 1 root root 1588 Apr 15 18:47 Bahia_Banderas
-rw-r--r-- 1 root root  344 Apr 15 18:47 Barbados
-rw-r--r-- 1 root root  588 Apr 15 18:47 Belem
-rw-r--r-- 1 root root  976 Apr 15 18:47 Belize
-rw-r--r-- 1 root root  307 Apr 15 18:47 Blanc-Sablon
-rw-r--r-- 1 root root  644 Apr 15 18:47 Boa_Vista
-rw-r--r-- 1 root root  257 Apr 15 18:47 Bogota
-rw-r--r-- 1 root root 2403 Apr 15 18:47 Boise
-rw-r--r-- 1 root root 1087 Apr 15 18:47 Buenos_Aires
-rw-r--r-- 1 root root 2098 Apr 15 18:47 Cambridge_Bay
-rw-r--r-- 1 root root 2015 Apr 15 18:47 Campo_Grande
-rw-r--r-- 1 root root  816 Apr 15 18:47 Cancun
-rw-r--r-- 1 root root  266 Apr 15 18:47 Caracas
-rw-r--r-- 1 root root 1129 Apr 15 18:47 Catamarca
-rw-r--r-- 1 root root  200 Apr 15 18:47 Cayenne
lrwxrwxrwx 1 root root    6 Apr 15 18:47 Cayman -> Panama
lrwxrwxrwx 1 root root   13 Apr 15 18:47 Chicago -> ../US/Central
-rw-r--r-- 1 root root 1522 Apr 15 18:47 Chihuahua
-rw-r--r-- 1 root root  345 Apr 15 18:47 Coral_Harbour
lrwxrwxrwx 1 root root    7 Apr 15 18:47 Cordoba -> Rosario
-rw-r--r-- 1 root root  341 Apr 15 18:47 Costa_Rica
-rw-r--r-- 1 root root  233 Apr 15 18:47 Creston
-rw-r--r-- 1 root root 1987 Apr 15 18:47 Cuiaba
lrwxrwxrwx 1 root root   13 Apr 15 18:47 Curacao -> Lower_Princes
-rw-r--r-- 1 root root  714 Apr 15 18:47 Danmarkshavn
-rw-r--r-- 1 root root 2093 Apr 15 18:47 Dawson
-rw-r--r-- 1 root root 1059 Apr 15 18:47 Dawson_Creek
lrwxrwxrwx 1 root root    9 Apr 15 18:47 Denver -> ../Navajo
lrwxrwxrwx 1 root root   14 Apr 15 18:47 Detroit -> ../US/Michigan
lrwxrwxrwx 1 root root   10 Apr 15 18:47 Dominica -> Montserrat
lrwxrwxrwx 1 root root   18 Apr 15 18:47 Edmonton -> ../Canada/Mountain
-rw-r--r-- 1 root root  684 Apr 15 18:47 Eirunepe
-rw-r--r-- 1 root root  250 Apr 15 18:47 El_Salvador
lrwxrwxrwx 1 root root   19 Apr 15 18:47 Ensenada -> ../Mexico/BajaNorte
-rw-r--r-- 1 root root  728 Apr 15 18:47 Fortaleza
lrwxrwxrwx 1 root root   18 Apr 15 18:47 Fort_Wayne -> ../US/East-Indiana
-rw-r--r-- 1 root root 2206 Apr 15 18:47 Glace_Bay
-rw-r--r-- 1 root root 1877 Apr 15 18:47 Godthab
-rw-r--r-- 1 root root 3219 Apr 15 18:47 Goose_Bay
-rw-r--r-- 1 root root 1287 Apr 15 18:47 Grand_Turk
lrwxrwxrwx 1 root root   10 Apr 15 18:47 Grenada -> Montserrat
lrwxrwxrwx 1 root root   10 Apr 15 18:47 Guadeloupe -> Montserrat
-rw-r--r-- 1 root root  306 Apr 15 18:47 Guatemala
-rw-r--r-- 1 root root  203 Apr 15 18:47 Guayaquil
-rw-r--r-- 1 root root  270 Apr 15 18:47 Guyana
lrwxrwxrwx 1 root root   18 Apr 15 18:47 Halifax -> ../Canada/Atlantic
lrwxrwxrwx 1 root root    7 Apr 15 18:47 Havana -> ../Cuba
-rw-r--r-- 1 root root  454 Apr 15 18:47 Hermosillo
drwxr-xr-x 2 root root 4096 Apr 23 14:00 Indiana
lrwxrwxrwx 1 root root   18 Apr 15 18:47 Indianapolis -> ../US/East-Indiana
-rw-r--r-- 1 root root 1928 Apr 15 18:47 Inuvik
-rw-r--r-- 1 root root 2046 Apr 15 18:47 Iqaluit
lrwxrwxrwx 1 root root   10 Apr 15 18:47 Jamaica -> ../Jamaica
-rw-r--r-- 1 root root 1145 Apr 15 18:47 Jujuy
-rw-r--r-- 1 root root 2362 Apr 15 18:47 Juneau
drwxr-xr-x 2 root root 4096 Apr 23 14:00 Kentucky
lrwxrwxrwx 1 root root   20 Apr 15 18:47 Knox_IN -> ../US/Indiana-Starke
lrwxrwxrwx 1 root root   13 Apr 15 18:47 Kralendijk -> Lower_Princes
-rw-r--r-- 1 root root  243 Apr 15 18:47 La_Paz
-rw-r--r-- 1 root root  417 Apr 15 18:47 Lima
lrwxrwxrwx 1 root root   13 Apr 15 18:47 Los_Angeles -> ../US/Pacific
-rw-r--r-- 1 root root 2781 Apr 15 18:47 Louisville
-rw-r--r-- 1 root root  208 Apr 15 18:47 Lower_Princes
-rw-r--r-- 1 root root  756 Apr 15 18:47 Maceio
-rw-r--r-- 1 root root  463 Apr 15 18:47 Managua
lrwxrwxrwx 1 root root   14 Apr 15 18:47 Manaus -> ../Brazil/West
lrwxrwxrwx 1 root root   10 Apr 15 18:47 Marigot -> Montserrat
-rw-r--r-- 1 root root  257 Apr 15 18:47 Martinique
-rw-r--r-- 1 root root 1416 Apr 15 18:47 Matamoros
lrwxrwxrwx 1 root root   17 Apr 15 18:47 Mazatlan -> ../Mexico/BajaSur
-rw-r--r-- 1 root root 1173 Apr 15 18:47 Mendoza
-rw-r--r-- 1 root root 2283 Apr 15 18:47 Menominee
-rw-r--r-- 1 root root 1456 Apr 15 18:47 Merida
-rw-r--r-- 1 root root  716 Apr 15 18:47 Metlakatla
lrwxrwxrwx 1 root root   17 Apr 15 18:47 Mexico_City -> ../Mexico/General
-rw-r--r-- 1 root root 1684 Apr 15 18:47 Miquelon
-rw-r--r-- 1 root root 3163 Apr 15 18:47 Moncton
-rw-r--r-- 1 root root 1416 Apr 15 18:47 Monterrey
-rw-r--r-- 1 root root 2160 Apr 15 18:47 Montevideo
lrwxrwxrwx 1 root root   17 Apr 15 18:47 Montreal -> ../Canada/Eastern
-rw-r--r-- 1 root root  170 Apr 15 18:47 Montserrat
-rw-r--r-- 1 root root 2284 Apr 15 18:47 Nassau
lrwxrwxrwx 1 root root   13 Apr 15 18:47 New_York -> ../posixrules
-rw-r--r-- 1 root root 2131 Apr 15 18:47 Nipigon
-rw-r--r-- 1 root root 2376 Apr 15 18:47 Nome
lrwxrwxrwx 1 root root   19 Apr 15 18:47 Noronha -> ../Brazil/DeNoronha
drwxr-xr-x 2 root root 4096 Apr 23 14:00 North_Dakota
-rw-r--r-- 1 root root 1522 Apr 15 18:47 Ojinaga
-rw-r--r-- 1 root root  203 Apr 15 18:47 Panama
-rw-r--r-- 1 root root 2108 Apr 15 18:47 Pangnirtung
-rw-r--r-- 1 root root  308 Apr 15 18:47 Paramaribo
lrwxrwxrwx 1 root root   13 Apr 15 18:47 Phoenix -> ../US/Arizona
-rw-r--r-- 1 root root 1483 Apr 15 18:47 Port-au-Prince
lrwxrwxrwx 1 root root   14 Apr 15 18:47 Porto_Acre -> ../Brazil/Acre
lrwxrwxrwx 1 root root   10 Apr 15 18:47 Port_of_Spain -> Montserrat
-rw-r--r-- 1 root root  588 Apr 15 18:47 Porto_Velho
-rw-r--r-- 1 root root  255 Apr 15 18:47 Puerto_Rico
-rw-r--r-- 1 root root 2131 Apr 15 18:47 Rainy_River
-rw-r--r-- 1 root root 1930 Apr 15 18:47 Rankin_Inlet
-rw-r--r-- 1 root root  728 Apr 15 18:47 Recife
lrwxrwxrwx 1 root root   22 Apr 15 18:47 Regina -> ../Canada/Saskatchewan
-rw-r--r-- 1 root root 1930 Apr 15 18:47 Resolute
lrwxrwxrwx 1 root root   14 Apr 15 18:47 Rio_Branco -> ../Brazil/Acre
-rw-r--r-- 1 root root 1129 Apr 15 18:47 Rosario
-rw-r--r-- 1 root root 2356 Apr 15 18:47 Santa_Isabel
-rw-r--r-- 1 root root  626 Apr 15 18:47 Santarem
lrwxrwxrwx 1 root root   20 Apr 15 18:47 Santiago -> ../Chile/Continental
-rw-r--r-- 1 root root  489 Apr 15 18:47 Santo_Domingo
lrwxrwxrwx 1 root root   14 Apr 15 18:47 Sao_Paulo -> ../Brazil/East
-rw-r--r-- 1 root root 1925 Apr 15 18:47 Scoresbysund
lrwxrwxrwx 1 root root    9 Apr 15 18:47 Shiprock -> ../Navajo
-rw-r--r-- 1 root root 2350 Apr 15 18:47 Sitka
lrwxrwxrwx 1 root root   10 Apr 15 18:47 St_Barthelemy -> Montserrat
lrwxrwxrwx 1 root root   22 Apr 15 18:47 St_Johns -> ../Canada/Newfoundland
lrwxrwxrwx 1 root root   10 Apr 15 18:47 St_Kitts -> Montserrat
lrwxrwxrwx 1 root root   10 Apr 15 18:47 St_Lucia -> Montserrat
lrwxrwxrwx 1 root root   10 Apr 15 18:47 St_Thomas -> Montserrat
lrwxrwxrwx 1 root root   10 Apr 15 18:47 St_Vincent -> Montserrat
-rw-r--r-- 1 root root  574 Apr 15 18:47 Swift_Current
-rw-r--r-- 1 root root  278 Apr 15 18:47 Tegucigalpa
-rw-r--r-- 1 root root 1528 Apr 15 18:47 Thule
-rw-r--r-- 1 root root 2211 Apr 15 18:47 Thunder_Bay
lrwxrwxrwx 1 root root   19 Apr 15 18:47 Tijuana -> ../Mexico/BajaNorte
lrwxrwxrwx 1 root root   17 Apr 15 18:47 Toronto -> ../Canada/Eastern
lrwxrwxrwx 1 root root   10 Apr 15 18:47 Tortola -> Montserrat
lrwxrwxrwx 1 root root   17 Apr 15 18:47 Vancouver -> ../Canada/Pacific
lrwxrwxrwx 1 root root   10 Apr 15 18:47 Virgin -> Montserrat
lrwxrwxrwx 1 root root   15 Apr 15 18:47 Whitehorse -> ../Canada/Yukon
lrwxrwxrwx 1 root root   17 Apr 15 18:47 Winnipeg -> ../Canada/Central
-rw-r--r-- 1 root root 2314 Apr 15 18:47 Yakutat
-rw-r--r-- 1 root root 1980 Apr 15 18:47 Yellowknife
```

In the US folder
```

-rw-r--r-- 1 root root 2384 Apr 15 18:47 Alaska
-rw-r--r-- 1 root root 2379 Apr 15 18:47 Aleutian
-rw-r--r-- 1 root root  353 Apr 15 18:47 Arizona
-rw-r--r-- 1 root root 3585 Apr 15 18:47 Central
lrwxrwxrwx 1 root root   13 Apr 15 18:47 Eastern -> ../posixrules
-rw-r--r-- 1 root root 1675 Apr 15 18:47 East-Indiana
-rw-r--r-- 1 root root  276 Apr 15 18:47 Hawaii
-rw-r--r-- 1 root root 2437 Apr 15 18:47 Indiana-Starke
-rw-r--r-- 1 root root 2216 Apr 15 18:47 Michigan
lrwxrwxrwx 1 root root    9 Apr 15 18:47 Mountain -> ../Navajo
-rw-r--r-- 1 root root 2845 Apr 15 18:47 Pacific
lrwxrwxrwx 1 root root    7 Apr 15 18:47 Pacific-New -> Pacific
-rw-r--r-- 1 root root  272 Apr 15 18:47 Samoa
```

---

### Post by Zoot_Nerper on 2015-04-26
Ah ok, so the locations are held locally in the system.

Trouble is it does not matter what I type, I after the first three chars (there are an awful lot of locations starting with "New"), I don't get a list of locations. Often, I get no list whether I type 1, 2, or 3 or more chars. No list at all.

I see in the file locations you give above that the time locations are binaries. I guess these binaries are added to a list of locations that the clock settings holds somewhere. Where is the file that holds this list?

I did not have this problem in the UK (where I set several locations), but do here (Thailand), so something must be going across the Net too??

---

### Post by sandyd on 2015-04-26
Hmm...

So the GUI doesn't seem to want to behave...

Lets try this through another way...
```

sudo dpkg-reconfigure tzdata
```

Should give you a nice text-based console to choose your appropriate timezone.

Side note: Ubuntu converts to the timezone from BIOS time, which it assumes to be UTC. If you have other OSes, they may have a fight over the time in the BIOS (Windows uses localtime), and subsequently change the time each time the OS is booted into.

---

### Post by Zoot_Nerper on 2015-04-27
Thanks for you replies sandyd.

sudo dpkg-reconfigure tzdata  does allow me to set my time zone, but this was set already. It does not  allow me to chose other additional time zones that I would like my  panel clock to show.

I checked with my BIOS and it's time shows the correct value for UTC.

I have no dual boots.

So, where does the System Settings store the list of additional time zones? Then I can go edit the file.

--Zoot

---

### Post by Zoot_Nerper on 2015-04-27
I found the following in a file in $HOME/.cache/upstart/indicator-datetime.log.1.gz


> ** (unity-control-center:3871): WARNING **: Could not connect to geoname lookup server: Operation was cancelled 
 
** (unity-control-center:3871): WARNING **: Could not connect to geoname lookup server: Operation was cancelled 
 
** (unity-control-center:3871): WARNING **: Could not connect to geoname lookup server: Operation was cancelled 
 
** (unity-control-center:3871): WARNING **: Could not connect to geoname lookup server: Operation was cancelled 
 
** (unity-control-center:3871): WARNING **: Could not connect to geoname lookup server: Operation was cancelled 
 
** (unity-control-center:3871): WARNING **: Could not connect to geoname lookup server: Operation was cancelled 
 
(unity-control-center:3871): GLib-GObject-WARNING **: invalid unclassed pointer in cast to 'CcTimezoneCompletion' 
 
** (unity-control-center:3871): WARNING **: Could not connect to geoname lookup server: Operation was cancelled


So, it is trying to go across the net somewhere and failing (or looks like to me).

I have four of these files in this directory. Two from today and then also 21/04 (the day I installed 15.04) and 22/04. So either geoname lookup server has been down for days or the timeout is too short.

--Zoot

---

### Post by mc4man on 2015-04-27
14.04 seems ok with adding add. locations but 15.04 is definitely bugged - 
[https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1440157](https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1440157)

---

### Post by Zoot_Nerper on 2015-04-27
OK thanks mc4man.

I will watch and see what happens on Launchpad.

-- Zoot

---

