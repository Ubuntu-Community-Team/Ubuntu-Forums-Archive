---
title: "passing parameters in Konqueror file associations to Wine"
date: 2008-11-29
forum: Desktop Environments
---

### Post by hiflyer on 2008-11-29
I had a problem where I could preform a file association in Konqueror to start a wine based program but could not figure out how to pass a file name to the wine based program. I solved the problem and thought it might be of interest to others as I found nothing on the site about it. I did find an old suggestion about a script but this requires no script

The file association looks like

env WINEPREFIX="/home/hiflyer/.wine" wine  "C:\Program Files\WinRAR\WinRAR.exe" "z:%U"

the trick was that I had to put the z: in front of the %U to make this work. "z:%f" also works. z: is defined in wine as the root directory. Apparently wine wants to see a windows like drive in front of the directory. This will not work with all programs as quickpar will start and get the file but it gets confused and does not know what directory it should be working out of and as a result does not work correctly. It does work with winrar.

hopefully this may be helpful to someone.

---

### Post by fmjrey on 2009-09-30
Thanks! It helped me getting the ms powerpoint viewer working straight from dolphin when right cliking the .pps

---

