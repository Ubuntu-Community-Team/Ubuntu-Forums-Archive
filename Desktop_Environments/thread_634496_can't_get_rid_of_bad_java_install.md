---
title: "can't get rid of bad java install"
date: 2007-12-07
forum: Desktop Environments
---

### Post by talkeetnaweb on 2007-12-07
I went to the following link:
[http://www.arh.noaa.gov/satloop.php?sat=goes&sector=4gvf](http://www.arh.noaa.gov/satloop.php?sat=goes&sector=4gvf)
and installed the first choice listed of java. This choice (g-something or other) is absolutely lousy. it slows firefox down to a crawl. I know there is better as my java worked fine back when had to do a manual install in a terminal window. Trouble is, there is no obvious way to uninstall the lousy program so I can try some of the other choices. Synaptic package manager is useless for uninstalling because it doesn't list history and there is no single program to uninstall , just a whole bunch of java and gtj or something listings. If anyone from ubuntu development is listening, please don't let firefox offer that crummy java experience to users any more.

---

### Post by PeterJS on 2007-12-07
That'd be gcj, which is supposed to be used for compiling java code not running things in real time, you're right it's a bad idea to have that as an option for firefox. To get rid of it, open up synaptic, search for gcj and uninstall it from there. The java package you want is sun-java6-plugin (or 5 if that's your thing)

---

### Post by erfahren on 2007-12-07
it may have been gcjwebplugin

anyway, for future reference you can configure which java is used system wide by running:
```

sudo update-alternatives --config java

```
you should see something like;
```

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java
 +        3    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 

```
select the "sun java" one (either 5 or 6, depending on which is installed).

---

