---
title: "Photoshop 7 doesn't work in WINE"
date: 2006-08-15
forum: Desktop Environments
---

### Post by Enigmatic on 2006-08-15
I searched and I tried the 

WINEDLLOVERRIDES=wintab32=n wine '/home/YOURCOMPUTER/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/Photoshop.exe'

command (make launcher, application type), but it doesn't seem to work (yes I replaced YOURCOMPUTER with my username).

This is the error:

Details: Failed to execute child process "WINEDLLOVERRIDES=wintab32=n" (No such file or directory)


Running WINE 0.9.9

---

### Post by cborga1985 on 2006-08-15
Install [Winetools]("http://www.von-thadden.de/Joachim/WineTools/") to set up and configure your wine environment.

---

### Post by Shay Stephens on 2006-08-15
I don't have my main machine in front of me now, but th basics are to run winecfg, add the photoshop executable to the list of applications list, then add wintab32 to the dll override list and set it to native.  Then change the launcher to just: 

wine /your/path/to/photoshop 

and it should all run fine.

---

### Post by Enigmatic on 2006-08-15
Let me clarify a bit..

If I navigate to my directory where Photoshop is installed, open a terminal there and do the command, it loads fine.

Putting the wintab32 override into winecfg and then not using the WINE Dll override command when launching does not work.

Mainly, the only thing I want is to be able to launch it from the desktop from a launcher, but I'm not sure why the command in my original post doesn't work, as it will launch from the Photoshop location just fine (except you would take out the path to Photoshop.exe).

---

