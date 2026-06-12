---
title: "checking current RAM usage?"
date: 2008-12-07
forum: General Help
---

### Post by gusteman on 2008-12-07
A big hello to all you friendly helpful community members.
Most likely I am asking a very stupid question, but being a novice I would like to know the following: is there any application (preferably graphic) that gives me a clear and instant overview on the RAM that is being used (in real-time) and by which applications and/or programs?
I am running Gutsy with 264Mb SDRAM and find, it very hard to run several applications. For instance GIMP runs slower that a snail. Maybe I could be able to clear some RAM by shutting down a few applications, but the problem is that I don't have a clue on which ones to shut down. Any suggestions??? Thanks in advance :p

---

### Post by Idefix82 on 2008-12-07
System->Administration->System Monitor.

The easiest remedy for your problem though is to buy some more RAM. 256MB is really very little. Another thing you could try is replace GNOME with a more lightweight desktop.

---

### Post by binbash on 2008-12-07
free -m

---

### Post by Forlong on 2008-12-07
There is an applet for your GNOME panel called system monitor. It's configurable so it will show the current RAM usage.

---

### Post by brunolabs on 2008-12-07
I use the System Monitor on the top panel.

Right-click -> Add to panel... -> System Monitor.

---

### Post by Wartender on 2008-12-07
yes the "traditional" way to do it is through system monitor, however, there are other ways, such as some [screenlets]("http://www.screenlets.org/index.php/Home"), or (my favorite) [conky]("http://conky.sourceforge.net/"). these give you constant updates on many things, such as RAM and processor (conky can even do network and music, among other things, and is significantly lighter than using screenlets)

---

### Post by OrangeCrate on 2008-12-07
+1 for Conky.

It's available for installation in Synaptic, or from the terminal as:

sudo apt-get install conky

---

