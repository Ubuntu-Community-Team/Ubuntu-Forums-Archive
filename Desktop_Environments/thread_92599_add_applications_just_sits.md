---
title: "add applications just sits??"
date: 2005-11-19
forum: Desktop Environments
---

### Post by ESPOiG on 2005-11-19
i used the method of getting wine from the wine hq site and used the instructions for just installing it normally... so i tried it but it didnt work and so i decided to try and put 'deb' actually infront of the html link to the site or wateva i dont fully understand it... but in doing this it failed and gave me sum error message and now doesnt work at all it just sits and loads into the app

can sumone help me please im stuck and i need it so i can use wine

---

### Post by adwait on 2005-11-20
I don't quite understand what you have done......but first remove wine altogether with:
```
sudo apt-get remove wine
```.
. Now, make your /etc/apt.source.list look like [this]("http://www.psychocats.net/linux/sources.php"). To edit the file:
```
sudo gedit /etc/apt/sources.list
```

Now run
```
sudo apt-get update
sudo apt-get install wine
```

That should hopefully do it.

---

### Post by manicka on 2005-11-20
I would suggest using this sources.list. It will give you the latest version of wine which is more stable than the breezy version.

[http://doc.gwos.org/index.php/Sources.list](http://doc.gwos.org/index.php/Sources.list)

---

### Post by ESPOiG on 2005-11-20
well apprentley it did install cuz i watched all the files download and stuff through the terminal but i culdnt locate it within the applications... eg accessories etc nor could i locate it within the 'add applications' application... so i dunno exactly how do u run the program do u use it through like and launcher that has been placed in programming or sumtin in appllications or do u right click the .exe file of the windows program... i dunno somone plz tell me what has gone wrong

---

### Post by manicka on 2005-11-20
wine is not a program that you run as such, but rather it is an emulator that is used to run  and install windows programs in Linux. The only gui panel that you can see with wine is the config contril panel. You can run this by running the command 

winecfg

How you get the Windows program to install nad run varies from program to program. Some will work and some not at all. The advice at winehq is a good place to start for finding out how to install a windows program and use it with the emulator - wine.

---

