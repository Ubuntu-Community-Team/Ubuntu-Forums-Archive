---
title: "rpg Stendhal"
date: 2005-06-08
forum: Gaming &amp; Leisure
---

### Post by SilvioTO on 2005-06-08
would I like to try this game playable on line with java web start technology but when I clic on play in this page [http://arianne.sourceforge.net/?arianne_url=games/game_stendhal](http://arianne.sourceforge.net/?arianne_url=games/game_stendhal)

[http://arianne.sourceforge.net/jws/stendhal.jnlp](http://arianne.sourceforge.net/jws/stendhal.jnlp)

a window ask me wich program use to open; firefox is default, but don't work; open a blank page and ask me again the same things. I have correctly installed Java on my hoary. Anyone can help me?

Thanks.

---

### Post by SilvioTO on 2005-06-08
ok, I understand. Download the zip files of stendhal, extract it, open console, enter in the stendhal folder then: java -jar stendhal-0.03.jar

---

### Post by Locomorto on 2005-06-08
[QUOTE=SilvioTO]ok, I understand. Download the zip files of stendhal, extract it, open console, enter in the stendhal folder then: java -jar stendhal-0.03.jar[/QUOTE]
 Yes thats how you do it. Be aware that it is very bpring in its current state ;).

---

### Post by SilvioTO on 2005-06-11
Very nice game! try it and meet me! my name in game is SilvioTO and this is my character

[IMG]http://www.sb-informatica.it/mycontent/silviostendhal.jpg[/IMG]

At this url the simply manual of game: [http://arianne.sourceforge.net/wiki/index.php/StendhalManual](http://arianne.sourceforge.net/wiki/index.php/StendhalManual)

here the home page of the game server: [http://stendhal.ombres.ambre.net/](http://stendhal.ombres.ambre.net/)

here to download the game and description: [http://arianne.sourceforge.net/?arianne_url=games/game_stendhal](http://arianne.sourceforge.net/?arianne_url=games/game_stendhal)

Hi!
Silvio.

---

### Post by digby on 2005-06-11
It looks like Zelda for the SNES!!!  Does it play like Zelda?  If so, I think I've found another way to waste way too much time...

---

### Post by SilvioTO on 2005-06-11
I like minimalist graphic. I like this game for similarity with Zelda.

---

### Post by zorkerz on 2006-04-26
[quote=SilvioTO]ok, I understand. Download the zip files of stendhal, extract it, open console, enter in the stendhal folder then: java -jar stendhal-0.03.jar[/quote]
Why I enter this command I get this response.  
"Failed to load Main-Class manifest attribute from stendhal-0.44.jar"
Anyone have any ideas what to do.  Im useing Dapper Drake flight 6 at the moment.
elias

---

### Post by zorkerz on 2006-04-26
Ok now im getting this.
"zorkerz@estle:~/Desktop/Stendhal0.48$ java -jar stendhal-0.48.jar
Configuring Log4J using data/conf/log4j.properties
Exception in thread "main" java.lang.NoClassDefFoundError: games.stendhal.client .StendhalClient
   at java.lang.Class.initializeClass(libgcj.so.7)
   at games.stendhal.client.stendhal.main(stendhal.java:147)
Caused by: java.lang.ClassNotFoundException: java.lang.Iterable not found in gnu .gcj.runtime.SystemClassLoader{urls=[file:stendhal-0.48.jar], parent=gnu.gcj.run time.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.VMClassLoader.defineClass(libgcj.so.7)
   at java.lang.ClassLoader.defineClass(libgcj.so.7)
   at java.security.SecureClassLoader.defineClass(libgcj.so.7)
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   ...1 more"

It seams to me like it might be a problem with java but i don't know enough to figure out what to do.  Help much appreciated.
elias

---

### Post by zorkerz on 2006-04-26
Ok ive got it to work.  I installed sun's java again and ran this command "sudo update-alternatives --all" to make sure it used sun's java instead of blackdown.
elias

---

