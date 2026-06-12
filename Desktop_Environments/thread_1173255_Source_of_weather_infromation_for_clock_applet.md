---
title: "Source of weather infromation for clock applet"
date: 2009-05-29
forum: Desktop Environments
---

### Post by Korandder on 2009-05-29
Where does the clock applet get its weather information? Is it possible to point it towards a specific source or weather station?

I ask this as are a few Environment Canada weather stations in my city and there can be a large range in temperatures between them. The applet seems to be using the one in the harbour which is right now nine degrees cooler than station at the university I work at or at the airport.

I am using Jaunty and Gnome 2.26.1

---

### Post by Forlornity on 2009-06-06
Bump to this, I've been wondering how to get my location on the weather as well, nearest it gives me is about 30 miles away.

---

### Post by njsharp on 2009-06-27
I too wondered where the clock applet gets its weather info.  I couldn't be bothered to get the applet's src file, so I just ran wireshark and changed the location to force requerying.  I found my PC accessed:
     [http://140.90.128.70/](http://140.90.128.70/)
which, surprise surprise is:
     [http://weather.noaa.gov/](http://weather.noaa.gov/)
and I found it sent this http query:
     GET /cgi-bin/mgetmetar.pl?cccc=EDDT HTTP/1.1
which generated several 1514 byte packets of response from the server.

Hope this helps!

---

