---
title: "Postgresql+GIS+R Resources"
date: 2010-05-26
forum: Education &amp; Science
---

### Post by spinoza666 on 2010-05-26
Hi,

I'm in the process of learning GIS (Qgis, GRASS) and Python (Numpy), and am already proficient in R and Postgresql. I know there's a lot of documentation on how to interface R with Postgresql, how to interface Python with R, how to interface GRASS with Postgresql, and so on, but I am looking for some documentation on how to efficiently use these together as a 'package'. So far I haven't come up with something really good.

Does anybody know of a book, manual etc, that focuses on how to use at least three of these together?

Cheers:)

---

### Post by spinoza666 on 2010-06-01
Bump! Anyone?


Quality resources for a Postgresql-GRASS-R or Postgresql-GRASS-Python combo?

---

### Post by gunksta on 2010-06-02
I have used Postgres with R but I've never used GRASS. I'm not sure if there are any guides for using all three as a single tool. But I will agree with you that Postgres + R is a powerful combination that is too often over-looked.

As I recall, GRASS is GIS software, correct?

Assuming that my memory serves correctly, couldn't you use the GIS tools built into R and Postgres to do what you want to do? Both products have GIS capabilities. I doubt they work too well together, bust depending on what you want to do, the parts are already there for GIS work.

Just a thought.

---

### Post by spinoza666 on 2010-06-02
Hey,

I have been considering the approach you've suggested, but not quite landed on anything yet. It's definitely a good option though. 

It strange that there's so little on this combo of mine though, as it seems to be very good setup. Postgresql can handle GIS-data with PostGIS, and Quantum GIS, which comes with a friendly GUI, can access this, plus get added functionality with a GRASS-plugin. GRASS is, as far as I can gather, the best GIS solution for Linux, although only command line. As you already know, Postgresql and R is a good option, and as you said, R is quite capable with spatial statistics. Python is just a bonus on top of this, as it's general purpose programming language, which can interface with all of the above, adding flexibility.

So in short I think this is a very good combo, and it's a shame there's not much out there on it. I guess I will just have to plod along learning one by one.

---

### Post by earlycj5 on 2010-06-02
> **spinoza666 said:**
> Hey,

I have been considering the approach you've suggested, but not quite landed on anything yet. It's definitely a good option though. 

It strange that there's so little on this combo of mine though, as it seems to be very good setup. Postgresql can handle GIS-data with PostGIS, and Quantum GIS, which comes with a friendly GUI, can access this, plus get added functionality with a GRASS-plugin. GRASS is, as far as I can gather, the best GIS solution for Linux, although only command line. As you already know, Postgresql and R is a good option, and as you said, R is quite capable with spatial statistics. Python is just a bonus on top of this, as it's general purpose programming language, which can interface with all of the above, adding flexibility.

So in short I think this is a very good combo, and it's a shame there's not much out there on it. I guess I will just have to plod along learning one by one.

It sounds interesting to me as well.  Though so far, I've managed to escape only using the spatial capabilities in R.

I'm interested in an integrated, more powerful approach such as this, but have yet to find a reason for it, so I've not learned it.

---

### Post by spinoza666 on 2010-06-02
Hey,

I have been considering the approach you've suggested, but not quite landed on anything yet. It's definitely a good option though. 

It strange that there's so little on this combo of mine though, as it seems to be very good setup. Postgresql can handle GIS-data with PostGIS, and Quantum GIS, which comes with a friendly GUI, can access this, plus get added functionality with a GRASS-plugin. GRASS is, as far as I can gather, the best GIS solution for Linux, although only command line. As you already know, Postgresql and R is a good option, and as you said, R is quite capable with spatial statistics. Python is just a bonus on top of this, as it's general purpose programming language, which can interface with all of the above, adding flexibility.

So in short I think this is a very good combo, and it's a shame there's not much out there on it. I guess I will just have to plod along learning one by one.

---

### Post by spinoza666 on 2010-06-04
Well, for those of you that are interested, I have found some resources, but not for my 'dream' combo. The first covers PostGIS, Postgresql, qgis and GRASS, while the second covers qgis, GRASS, and a bit of R. Definitely not quite what I am after though. I will keep you posted in my quest:

 [http://wiki.osgeo.org/wiki/Educational_Content_Inventory#Introduction_to_FOSS_GIS_using_QGIS_.8.2C_PostgreSQL.2C_PostGIS.2C_and_the_Grass_plugin_for_QGIS]("http://wiki.osgeo.org/wiki/Educational_Content_Inventory#Introduction_to_FOSS_GIS_using_QGIS_.8.2C_PostgreSQL.2C_PostGIS.2C_and_the_Grass_plugin_for_QGIS")

[http://www.plantsciences.ucdavis.edu/plant/qgislabs.htm]("http://www.plantsciences.ucdavis.edu/plant/qgislabs.htm")

---

### Post by spinoza666 on 2010-06-05
Now we are getting somewhere. I found this book which seem like an okay introductory text, and have duly ordered it from my library:

[http://www.pragprog.com/titles/gsdgis/desktop-gis](http://www.pragprog.com/titles/gsdgis/desktop-gis)

This does not seem to cover R integration, but together with the two links in my last post, I'm happy with this for now. Hopefully this has been helpful for others than me:)

---

### Post by gunksta on 2010-06-05
Once you learn how to integrate the three of these - you should write an introductory text.

---

### Post by spinoza666 on 2010-06-05
Hehe I may you just do that:) Just gotta get an exam and my master out of the way first... But yeah it's sorely needed I would say.

---

