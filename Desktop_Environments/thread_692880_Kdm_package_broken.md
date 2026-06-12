---
title: "Kdm package broken"
date: 2008-02-10
forum: Desktop Environments
---

### Post by Mainlake on 2008-02-10
Hello!

When I'm trying to update my system with Adept manager it doesn't work. It downloads new packets, but it starts to install them, I get just a error message saying "Changes couldn't be done. There migh have been problems in downloading the packets, or changes might have broken down some packets". I've tracked down this problem to kdm package. In adept manager it says: ```
kdm state: broken(installed) request:Pause(no change) 
```

And in command line I get following:
```
tuomas@experience:~$ sudo apt-get install kdm
Luetaan pakettiluetteloita... Valmis
Muodostetaan riippuvuussuhteiden puu
Reading state information... Valmis
kdm on jo uusin versio.
Saatat haluta suorittaa "apt-get -f install" korjaamaan nämä:
Näillä paketeilla on tyydyttämättömiä riippuvuuksia:
  kdm: Riippuvuudet: kdebase-bin (= 4:3.5.8-0ubuntu2.2) mutta 4:3.5.8-2ubuntu3~gutsy1~ppa1 on merkitty asennettavaksi
E: Kaikkia riippuvuuksia ei ole tyydytetty. Kokeile "apt-get -f install" ilmanpaketteja (tai ratkaise itse).
tuomas@experience:~$ sudo apt-get -f install
Luetaan pakettiluetteloita... Valmis
Muodostetaan riippuvuussuhteiden puu
Reading state information... Valmis
Korjataan riippuvuuksia... Valmis
Seuraavat paketit POISTETAAN:
  kdm
0 päivitetty, 0 uutta asennusta, 1 poistettavaa ja 4 päivittämätöntä.
1 ei asennettu kokonaan tai poistettiin.
Noudettavaa arkistoa 0t.
Purkamisen jälkeen vapautuu 1606kt levytilaa.
Haluatko jatkaa [K/e]? K
dpkg: error processing kdm (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 kdm
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Short translation:
Kdm is the newest package. kdm: Dependencies: kdebase-bin (= 4:3.5.8-0ubuntu2.2) but 4:3.5.8-2ubuntu3~gutsy1~ppa1 is marked to be installed.
Tried to fix it with "apt-get -f install", as suggested, but the result is seen above...

And reinstalling:
```

tuomas@experience:~$ sudo aptitude reinstall kdm
Luetaan pakettiluetteloita... Valmis
Muodostetaan riippuvuussuhteiden puu
Reading state information... Valmis
Luen tilatietoja
Alustan pakettien tiloja... Valmis
Rakennan merkkitietokantaa... Valmis
Nämä paketit ovat RIKKI:
  kdm
Nämä paketit on automaattisesti jätetty odottamaan:
  acroread-escript
Nämä paketit on jätetty odottamaan:
  acroread acroread-plugins firefox
0 päivitettävää pakettia, 0 uutta asennusta, 1 uudelleen asennettavaa, 0 poistettavaa ja 4 päivittämätöntä.
Tarvitsee noutaa 664kB arkistoista. Levytilaa kuluu 0B purkamisen jälkeen.
Näillä paketeilla on tyydyttämättömiä riippuvuuksia:
  kdm: Riippuvuudet: kdebase-bin (= 4:3.5.8-0ubuntu2.2) mutta 4:3.5.8-2ubuntu3~gutsy1~ppa1 on asennettu.
Resolving dependencies...
Seuraavat toiminnot selvittävät nämä riippuvuudet:

Poista paketit:
kdm

119 pistettä

Hyväksytkö tämän ratkaisun? [Kyllä=y/ei=n/lopeta=q/?] y
Nämä paketit on automaattisesti jätetty odottamaan:
  acroread-escript
Nämä paketit POISTETAAN automaattisesti:
  kdm
Nämä paketit on jätetty odottamaan:
  acroread acroread-plugins firefox
Nämä paketit POISTETAAN:
  kdm
0 päivitettävää pakettia, 0 uutta asennusta, 1 poistettavaa ja 4 päivittämätöntä.
Tarvitsee noutaa 0B arkistoista. Levytilaa vapautuu 1606kB purkamisen jälkeen.
Haluatko jatkaa? [Kyllä=y/ei=n/?] y
Kirjoitan tilatietoja... Valmis
dpkg: error processing kdm (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 kdm
E: Sub-process /usr/bin/dpkg returned an error code (1)
Jonkin paketin asennus epäonnistui.  Yritän toipua:
Segmentation fault (core dumped)

```

So how do I fix this??? Using Kubuntu.

---

