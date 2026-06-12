---
title: "Can someone give me a bit of help with curl and conky"
date: 2008-12-27
forum: General Help
---

### Post by markp1989 on 2008-12-27
Im trying to make a small bash script that will check the RSS Feed on bbc weather site for my local town. 

So far i have

```
curl http://feeds.bbc.co.uk/weather/feeds/rss/obs/world/0008.xml | grep "Temperature" > temp 
``` 

and it gives me the following out put 

```

Temperature: 2&#xB0;C (36&#xB0;F), Wind Direction: NE, Wind Speed: 13 mph, Relative Humidity: 77&#37;, Pressure: 1034mB, Falling, Visibility: Good

```

what i would like is to have all the info broken up on more then one line

like so: 
Temperature: 2C (36F),
Wind Direction: NE,
Wind Speed: 13 mph, 
Relative Humidity: 77&
Pressure: 1034mB, Falling,
Visibility: Good

can some one give me a few pointers?

thanks markp1989

---

### Post by markp1989 on 2009-01-15
just threw this together you will have to change the url at the top to match the rss of your location (currently its set for london), the cuts, etc are setup for the bbc weather RSS, but do international weather, so it should be ok for most people

```

curl http://feeds.bbc.co.uk/weather/feeds/rss/obs/world/0008.xml  >/dev/null 2>&1 > .weatherfeedrs
echo Temperature:     `cat .weatherfeedrs | grep "Temperature"| cut -f2 -d' ' | tr '&#xB0' ' ' | cut -c 1-4`C
echo Wind Direction:  `cat .weatherfeedrs| grep "Temperature"| cut -f6 -d' ' | tr -d ','`
echo Wind Speed:      `cat .weatherfeedrs | grep "Temperature"| cut -f9 -d' '` mph
echo Humidity         `cat .weatherfeedrs | grep "Temperature"| cut -f13 -d' ' | tr '&#xB0' ' ' | cut -c 1-3`%
echo pressure `cat .weatherfeedrs | grep "Temperature"| cut -f15 -d' '` `cat .weatherfeedrs | grep "Temperature"| cut -f16 -d' '`
echo Visability:      `cat .weatherfeedrs | grep "Temperature"| cut -f7 -d':'| cut -c2-20`
rm .weatherfeedrs 

```

this can be called by conky , or just ran in the command line.

this is the current output it gives
```

[mark@markspc Desktop]$ ./weather.sh 
Temperature: 5 C
Wind Direction: SE
Wind Speed: 14 mph
Humidity 79 %
pressure 1013mB, Rising,
Visability: Very good
[mark@markspc Desktop]$ 

```

---

