---
title: "aircrack-ng GUI interface is it possible?"
date: 2009-01-03
forum: Desktop Environments
---

### Post by tednumber8 on 2009-01-03
I would like to run aircrack as a gui interface, has anyone got a way to do this?

---

### Post by stderr on 2009-01-03
Most people after buggering around with the aircrack binaries for ages wouldn't mind some form of GUI. There isn't one.

The closest you will come are some tiny Winblows projects to make a GUI for it. Like [this one]("http://nazircon.googlepages.com/"). Which has been discontinued, what with it being illegal and all. (Perhaps due to including some .dlls required to interface it with the NIC?) You *may* be able to find some tiny projects that still exist, but probably not for Linux, and the Windows ones may well not be legal (although the source code seems to be GPLv2).

Basically, [this]("http://www.aircrack-ng.org/doku.php?id=tutorial") is your starting point.

edit: You've opened quite a number of threads & posts about this single issue...one will suffice, the rest are just cluttering the forums. And if someone else is looking for help on the same issue, it makes it much harder for them if advice is spread over 3 or 4 different threads. If you don't get a response to a question in a few days you can always bump the thread. 

I know you're desperate for an "easy" way to just "get aircrack working", but I don't think there is one. I went through the same thing a year or so back - you have to follow the tutorials and read the documentation. It's not that painful and in the long run you'll learn a lot more. 

As for one of your other threads, you seem slightly confused (sorry if I'm reading it wrong) - a GUI is an extra thing which has to be written. If a CLI application doesn't provide a GUI interface, there is only the CLI interface. e.g. ndiswrapper is CLI. There's been a GUI app written for it called ndisgtk. e.g.2 EnvyNG provides CLI and GUI, and you switch between them with command line switches. There's no hidden GUI to "unlock" or something with aircrack ;) And for someone other than the authors of aircrack to write a GUI for it would be... hell, I would've thought. Which is probably why no serious projects have happened.

edit2: I suppose it would be *possible* to create a simple GUI (far easier to create a bash script) to do some simple things once aircrack's all set up. I can't see it really helping... at all. 
  - *You will still need to sort out your problems with aircrack first and get it working!* 
  - It would be just as easy to use the commands anyway once it's all set up... in fact, probably easier
  - In the time it'd take to write a little GUI to do very little, you could have done all you wanted to with aircrack and probably written a thesis on the entire experience

SO, you really want to figure out how to fix the problems in your first (I think...) aircrack thread, which you can do from official documentation.

---

### Post by taylor102387 on 2009-04-01
I have just created a script that makes life so much easier (for aircrack-ng). You can download below or go to:

[http://code.google.com/p/aircrack-ng-bash-script/](http://code.google.com/p/aircrack-ng-bash-script/)


||
||
||
\/

---

### Post by criser80 on 2010-01-04
Try this one, its for linux and runs well under Ubuntu.
[http://forum.aircrack-ng.org/index.php?topic=6329.0]("http://forum.aircrack-ng.org/index.php?topic=6329.0")

---

### Post by HumanDictionary on 2010-01-28
> **taylor102387 said:**
> I have just created a script that makes life so much easier (for aircrack-ng). You can download below or go to:

[http://code.google.com/p/aircrack-ng-bash-script/](http://code.google.com/p/aircrack-ng-bash-script/)


||
||
||
\/
OMG thank you so much for that!

---

### Post by dan-420 on 2010-09-05
yea it works great thnx :p

---

### Post by Ernie S. on 2010-09-19
Try learning kismet, wireshark, ettercap, etc. These tools can give you a more "graphical" display of your packet captures. Each one has its own abilities as well, such as MITM attacks ans so on. As for the actual cracking of wep/wpa/wpa2 keys, I'm not really sure why you would want a GUI. There really isn't much to see...

---

