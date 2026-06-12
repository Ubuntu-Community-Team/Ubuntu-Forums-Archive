---
title: "RPM Install"
date: 2005-12-16
forum: General Help
---

### Post by Lvnielen on 2005-12-16
HI,

I have a standard instalation from Ubuntu, and i will install a aplication, but it goes not but its a RPM file.

Who can tell me how i can install a RPM file on Ubuntu?

Sorry for the bad english:confused: :( , i from the netherlands:D 

thanks

---

### Post by DaMasta on 2005-12-16
First I suggest seeing if a debian package is available. If not:
sudo apt-get install alien
sudo alien package-name.rpm
sudo dpkg -i package_name.deb

---

### Post by Rinzwind on 2005-12-16
Ik ook :)

Als je een RPM package wil gebruiken zul je die moeten her-pakken. Dat doe je met 'alien op deze manier:
If you want to use an RPM package you need to re-pack it so it works with Ubuntu/debian. You do that with 'alien' and it's installed with this command:
```
sudo apt-get install alien
```

Ga dan met je favouriete shell naar waar het bestand is opgeslagen en doe dit:
Then go visit the file with your favourite shell and do this:
```
sudo alien {original-name}.rpm
```

Daarna installeer je dit nieuwe installatie-bestand met:
After that you can install it with
```
sudo dpkg -i {original-name}.deb
```

Mind you: This is a raw draft and I'd rather have a real name of a .rpm so I can test the alien command and re-packing 1st. Try at your own risc ;) 


And see! Bi-lingual support on ubuntuforums.org.

---

### Post by Lvnielen on 2005-12-16
Volgens mij is het gelukt nu alleen nog kijken waar het programma zelf staat (AVG viruscanner voor linux)

is er ergens een NL handleiding voor ubuntu?

---

### Post by MonolithTMA on 2005-12-16
You could always try the babelfish.

I translated your previous post using it.

> According to me it has succeeded now only still look at where the programme himself stands (AVG viruscanner for linux) there are somewhere Netherlands guide for ubuntu?

[AltaVista - Babel Fish Translation]("http://babelfish.altavista.com/")

De vertaling in Babelfish is niet altijd mooi, maar het geeft gewoonlijk de juiste ideeën.

The translation in Babelfish is not always pretty, but it usually gives the right ideas.

---

### Post by Rinzwind on 2005-12-16
[QUOTE=Lvnielen]Volgens mij is het gelukt nu alleen nog kijken waar het programma zelf staat (AVG viruscanner voor linux)

is er ergens een NL handleiding voor ubuntu?[/QUOTE]

2 Dutch forums (not as big as this one tho ;) )
[http://www.ubuntu-linux.nl/forum/](http://www.ubuntu-linux.nl/forum/)
[http://forum.ubuntu-nl.org/index.php](http://forum.ubuntu-nl.org/index.php)

And did you check the menu? Most-likely inside sytem.

And WTF do you want a virusscanner for!?
It's not going to make you any safer than when you are not using it :P 

Just delete every weird e-mail you get and stay away from weird websites. Stick to websites that prove to be genuine.
It worked for me for over 10 years allready and till recently (Ubuntu I've been using for 3 weeks now) even with Windows 98, 98 SE, ME and XP. :)

---

### Post by Lvnielen on 2005-12-16
> **Rinzwind]2 Dutch forums (not as big as this one tho  said:**
> http://www.ubuntu-linux.nl/forum/[/url]
[http://forum.ubuntu-nl.org/index.php](http://forum.ubuntu-nl.org/index.php)

And did you check the menu? Most-likely inside sytem.

And WTF do you want a virusscanner for!?
It's not going to make you any safer than when you are not using it :P 

Just delete every weird e-mail you get and stay away from weird websites. Stick to websites that prove to be genuine.
It worked for me for over 10 years allready and till recently (Ubuntu I've been using for 3 weeks now) even with Windows 98, 98 SE, ME and XP. :)

ik wilde kijken hoe het instaleren van software onder linux gaat....en ik had toch toevallig liggen...
ik ga straks waarschijnlijk een multi boot maken van me pc met XP en linux ditributie en wil ik eigenlijk meer op ubuntu werken dan op xp dus ben veel linux pakketten aan het testen onder andere p het instaleren van nieuwe software

---

### Post by Rinzwind on 2005-12-16
Ok :) 

Well alot of software is inside the packages and those (in general) install without a problem. 

Without doing alot I can browse the web with wireless, use email, watch video and listen to music, share with my PC, print remotely. And all with a laptop :)


Oh and this site [http://ubuntuguide.org/](http://ubuntuguide.org/) has ALOT of packages with the correct command line syntax to install them.

---

