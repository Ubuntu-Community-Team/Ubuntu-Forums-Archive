---
title: "SideCandy Weather gDesklet problems"
date: 2005-06-02
forum: Desktop Environments
---

### Post by Kyral on 2005-06-02
I just might be missing something, but I cannot get this to display my weather. I live in the USA, so I assume I put in "United States of America" into the Country box, but I put my city into the City box and it either displays "Fail" or "Ambiousgus(sp?)". I know there is another place named the same, but in another state. and I have tried putting <city>, <state abbrev> with the same results. Many thanks for help :D

---

### Post by Psquared on 2005-06-02
[QUOTE=Kyral]I just might be missing something, but I cannot get this to display my weather. I live in the USA, so I assume I put in "United States of America" into the Country box, but I put my city into the City box and it either displays "Fail" or "Ambiousgus(sp?)". I know there is another place named the same, but in another state. and I have tried putting <city>, <state abbrev> with the same results. Many thanks for help :D[/QUOTE]

Use the GoodWeather desklet from [www.gdesklets.gnomedesktop.org](www.gdesklets.gnomedesktop.org). I seem to remember that the sidecandy weather desklet didn't work for me -- or maybe it was just too hard to setup. GoodWeather is very easy. You just put in your zip code and it gets the weather from weather.com.

---

### Post by jerrybme on 2005-06-02
Side candy uses the "US" plus the state abbreviation. I live in Illinois so the country line reads US IL.

---

### Post by bradlis7 on 2006-03-24
If you put in the zip code into the city, and US into the country, it works, but displays the zip code instead of the city name. I'd like for it to be able to display the city name though.

I put "Lubbock" into city and "US TX" into country, but it still says ambiguous.

If only the US had used unique city names...

---

### Post by TitusDalwards on 2006-04-22
if your problem hasn't been solved you can use [conky]("http://conky.sourceforge.net/").
for installation:
```
sudo apt-get install conky
```
```
$ zcat /usr/share/doc/conky/examples/conkyrc.sample.gz > ~/.conkyrc
```

---

