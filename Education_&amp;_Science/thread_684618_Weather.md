---
title: "Weather"
date: 2008-02-01
forum: Education &amp; Science
---

### Post by sadman64 on 2008-02-01
I'm not sure if this is the right forum to post this, but I need information about ubuntu's weather program, if it's available. I am doing a project for school where I have to report the current weather. Currently, I am going to have to parse weather.com's html page. I was just wondering if ubuntu's weather service was open source, and I could possibly use their weather information for my web service. Any information would be appreciated. Thanks.

---

### Post by sadman64 on 2008-02-01
Also, it doesn't have to be specifically ubuntu's service. Any API would be useful. Parsing html isn't the easiest way to get the information, so I was just looking for a service to provide the information.

---

### Post by rufius on 2008-02-01
[http://ftp.gnome.org/pub/GNOME/sources/gnome-applets/2.20/](http://ftp.gnome.org/pub/GNOME/sources/gnome-applets/2.20/)

Thats the sources repository for the gnome-applets. When you untar that file, you'll find a directory inside called libgweather, thats probably what you want.

I don't know much about it beyond that.

Hope that helps :)

---

### Post by sadman64 on 2008-02-01
hey, thanks. that's what i wanted. now i just have to figure out what is easier, seeing if i can figure out that source code, or parsing and html file.

---

### Post by Scooby Doo on 2008-02-04
Why can't you subscribe to yahoo's RSS feed for the location you want? It's in an XML format - much easier than parsing a full page.

---

### Post by sadman64 on 2008-02-05
it has to be for any zip code that is entered, and it only returns the current information once. i found out that weather.com has an xml data base that i can use.

---

