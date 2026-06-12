---
title: "How do I install this program?"
date: 2009-06-22
forum: General Help
---

### Post by Robbyx on 2009-06-22
Could someone please clarify what  I should do to execute the script. 
I have created a folder called:

/home/rob/.cronometer

It now contains:
CRONoMeter.app
_MACOSX
cronometer.sh




The contents of cronometer.sh are as folows:

 ```
#!/bin/sh

# INSTRUCTIONS
#  1) Install Java 1.5 or later for Linux (http://java.com/download/)
#  2) Download Mac OS X Version and Unzip in desired location
#  3) Place this launcher script next to the application bundle 
#  4) Execute script to launch CRON-o-Meter

cd "CRONoMeter.app/Contents/Resources/Java/"
java -cp cronometer.jar:jcommon-1.0.10.jar:jfreechart-1.0.6.jar:swingx-0.9.3.jar:cronometer.jar:usda_sr21.jar:crdb_003.jar:docs.jar ca.spaz.cron.CRONOMETER
```

---

### Post by michy99 on 2009-06-22
First, make sure you have Java 1.5 or later.```
java -version
```Then make sure the script is executable.```
chmod a+x cronometer.sh
```To run it do```
./cronometer.sh
```

---

### Post by Robbyx on 2009-06-22
Thank you.

---

### Post by Robbyx on 2009-06-22
Can you please tell me how to make it run as an icon.

Do I put this ./cronometer.sh into a new item in the edit menus?

---

### Post by ad_267 on 2009-06-22
You can then also make a launcher to start the application from your desktop or menu (assuming it's a graphical application). You can right click on the menu and select edit menus then create a new item or right click on the desktop and select create launcher. Then for the command give the full path to the cronometer.sh script, ie. /home/rob/.cronometer/cronometer.sh

Edit: I posted this before I saw your run as an icon question, but I think this does what you want.

---

### Post by michy99 on 2009-06-22
I think this will work as the command for a launcher:```
cd /home/rob/.cronometer && ./cronometer.sh
```

---

### Post by ad_267 on 2009-06-22
I think you need to use the full path to the script, I don't think you can use cd in a launcher, but I just realised my instructions won't work. To get them to work you have to edit the cronometer.sh script.

Change:
```
cd "CRONoMeter.app/Contents/Resources/Java/"
```
To:
```
cd "$HOME/.cronometer/CRONoMeter.app/Contents/Resources/Java/"
```

That way you can run the cronometer.sh script from a launcher and it will still be able to find the .jar files it needs.

---

### Post by Robbyx on 2009-06-23
Thank you very much for your help. The launcher works as does the program.

---

