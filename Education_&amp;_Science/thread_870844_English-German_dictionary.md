---
title: "English-German dictionary"
date: 2008-07-26
forum: Education &amp; Science
---

### Post by KOTAPAKA on 2008-07-26
I need an English-German dictionary and vice versa. I am looking for a Linux version. My last resort is wine.

---

### Post by tech4web on 2008-07-26
you can use MDic dictionary.

[mdic.sourceforge.net]("http://mdic.sourceforge.net")  << more information.

this is it's description.
--------------------------------------------------
MDic is a multilingual dictionary for GNU/Linux operating system.
It is only needed to select (or highlight) a word to view its meaning on the screen. MDic is able to pronounce the words by default if espeak tool is installed, or if KDE text to speech configured properly. It is also possible to use Babylon glossaries (.bgl) , Stardict dictionaries (.ifo) , Freedict dictionaries (.tei) and Sdictionary dictionary (.dct) by converting them via "mdicconv" convertor tool, that you can download it from here.

The only pre-requirements to use MDic is Qt4 library. 
---------------------------------------------------

---

### Post by borobudur on 2008-09-13
Do you know this weblink:

[http://dict.leo.org/](http://dict.leo.org/)[URL="http://dict.leo.org/"]
[/URL]

---

### Post by darthmob on 2008-09-13
I don't know any offline dictionary but I am using beolingus online with firefox 'custom' bookmarks. that way I can simply open a new tab and type 'ende awesomeness' (english - deutsch, vice versa would be deen - deutsch english) and it this case it opens **_[that]("http://dict.tu-chemnitz.de/dings.cgi?lang=de&service=en-de&opterrors=0&optpro=0&query=awesomeness&iservice=&dlink=self&comment=")_** page.

the bookmark itself looks like that:
[IMG]http://images.voric.com/files/bookmark_ghs80.jpg[/IMG]

important are location and keyword. keyword specifies with which word you can open this bookmark.
the location is basically the desired page with a '%s' where the search term is (you can easily find that position when actually searching on a page eg. with test and replacing test in the link with %s).

the location for german - english is: ```
http://dict.tu-chemnitz.de/dings.cgi?lang=de&service=deen&opterrors=0&optpro=0&query=%s&iservice=&comment=
```

english - german: ```
http://dict.tu-chemnitz.de/dings.cgi?lang=de&service=en-de&opterrors=0&optpro=0&query=%s&iservice=&dlink=self&comment=
```

---

### Post by FrankVdb on 2008-09-14
If you're looking for an off-line dictionary, have a look at elcombri.de. They have the best free English<>German dictionary around.

All the dictionaries that I use (I'm an interpreter of Dutch, German and English) are paid ones, with one exception: elcombri. Don't know where the name comes from but it's fairly complete and reliable. 

There is a Linux version running on Java but I haven't managed to get it to work yet so I'm running the Windows version in a virtual machine, together with all my other dictionaries.

---

### Post by kford on 2009-05-23
FrankVdb - thanks for the tip.

As for getting Elcombri to run, place the "translator11c.jar" file and the dictionary file in the same directory.  In a terminal, navigate to the directory and run this command:

```
java -Xmx256m -jar translator11c.jar
```

If Elcombri fails to start, you may not have Java installed.  Try:

```
java -version
```

If you don't get something along the lines of

```
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu7)
OpenJDK 64-Bit Server VM (build 14.0-b08, mixed mode)
```

then you may need to install java.  [ I think, but I reserve the right to be wrong, Java OpenJDK has shipped with Ubuntu by default since Intrepid. ]

Otherwise, run this command in a terminal to install the OpenJDK JRE:

```
sudo apt-get install openjdk-6-jre
```

If, however, Elcombri starts but hangs on "Loading dictionary..." increase the "-Xmx256m" value in the above command to 384 or so.  Although Elcombri started without a hitch on my desktop, it hung on my laptop.  Increasing the JVM heap memory worked.

Best of luck!

---

### Post by SuperSonic4 on 2009-05-23
When it comes to getting a dictionary nothing beats a hard copy paper version. I'm still using mine from ~2000ish.

I'm personally using a translator plasmoid to do the job but that would go via google - gtranslator looks like a good one though

---

