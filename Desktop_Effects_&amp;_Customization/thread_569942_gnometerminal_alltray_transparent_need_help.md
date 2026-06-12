---
title: "gnometerminal alltray transparent need help"
date: 2007-10-07
forum: Desktop Effects &amp; Customization
---

### Post by fedex1993 on 2007-10-07
Okay i have a transparent gnome terminal on my desktop. My only question is when i put a window behind the terminal it does not show that window eventhoe its fully transparent for the terminal but thats just one and the only glitch any help.


[IMG]http://i20.tinypic.com/24zhh5c.png[/IMG]

---

### Post by FuturePilot on 2007-10-07
That's because it uses pseudo transparency. If you want true transparency you need to be using some type of compositing. Like Compiz or Compiz-Fusion

---

### Post by fedex1993 on 2007-10-07
only problem is compiz doesnt run well and i like not having all the effects but what ever guess i willl just half to deal with it

---

### Post by fedex1993 on 2007-10-07
well could i use beryl because beryl runes fine compiz laggs badly

---

### Post by FuturePilot on 2007-10-07
Yes Beryl will also work. If you're using Feisty it's in the repos.

---

### Post by fedex1993 on 2007-10-07
okay my question is also with beryl is there anyway that i can use beryl just not use a beryl emerald theme just a stock gtk theme?

---

### Post by FuturePilot on 2007-10-07
Yes, you will also want to install Heliodor. It uses whatever your Metacity theme is.
```
sudo apt-get install beryl beryl-manager heliodor
``` 
Start Beryl Manager and go to Window Decorator ( I think, I haven't used Beryl in a long time) and pick GTK Window Decorator (Heliodor)

---

### Post by fedex1993 on 2007-10-07
hmm now all tray doesnt want to work with beryl thats weird

---

### Post by fedex1993 on 2007-10-07
ahh what ever i will just leave it without any cool special effects i just wish there was something that didnt half to change my whole desktop just that terminal to make it full transparent

---

