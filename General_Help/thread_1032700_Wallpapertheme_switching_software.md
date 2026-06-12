---
title: "Wallpaper/theme switching software?"
date: 2009-01-06
forum: General Help
---

### Post by metroidnemesis13 on 2009-01-06
I have several nice wallpapers that I'd like to automatically cycle through every few minutes.  Is there a program that can do this automatically?  Or is there code I can put in the terminal that would do this automatically?  Thanks.

---

### Post by mtbsoft on 2009-01-06
You can either use [wallpaper tray]("http://linux.softpedia.com/get/Desktop-Environment/Tools/Wallpaper-Tray-19873.shtml") or some of the features in Compiz (though I can't, for the life of me, find the setting just now).

---

### Post by ve4cib on 2009-01-06
Here's a quick-and-dirty Python script I've been using to shuffle backgrounds:

```

#!/usr/bin/python
import os,random,gconf,time

# how long should the program wait between switches? (seconds)
SLEEP_TIME=1800

# Change this to the folder where your wallpapers are stored
folder= os.path.expandvars("$HOME/pictures/Backgrounds")

gconf_path= "/desktop/gnome/background/picture_filename"

lastWallpaper=gconf.client_get_default().get_string(gconf_path)

while True:
    currentWallpaper = gconf.client_get_default().get_string(gconf_path)
    if(currentWallpaper==lastWallpaper):
        wallpapers= os.listdir(folder)
        wallpaper= os.path.join(folder, random.choice(wallpapers))
        gconf.client_get_default().set_string(gconf_path, wallpaper)
        lastWallpaper = wallpaper

    else:
        lastWallpaper = currentWallpaper

    time.sleep(SLEEP_TIME)

```

Copy-and-paste the code (changing the directory if needed), save it, make it executable, and add it to your startup programs (Tools>Preferences>Sessions)




And if you happen to use Fluxbox here's a similar script for that.  Same process, but just add it to your ~/.fluxbox/startup file (with an & at the end!)

```

#!/usr/bin/python
import os
import time
import random

# change this as necessary
BG_PATH = '$HOME/pictures/Backgrounds/'

#how long to wait between switches (seconds)
SLEEP_TIME=1800


if(__name__=='__main__'):
    #
    # check to see if this script is already running
    #
    pipe=os.popen('ps aux|grep setbg-fluxbox')
    lines=pipe.readlines()
    pipe.close()
    
    
    time.sleep(10)
    while True:
        pipe = os.popen('ls '+BG_PATH)
        bgnames = pipe.readlines()
        pipe.close()
        
    
        rnd = random.randint(0,len(bgnames)-1)
        
        cmdstr = 'fbsetbg -a \"'+BG_PATH+bgnames[rnd].strip()+'\"'
        os.system(cmdstr)
        
        # sleep for 15 minutes before picking a new background
        time.sleep(SLEEP_TIME)

```

---

### Post by Secret Neo on 2009-01-06
does that python code able to fade the images or is it just a simple cut to next image

---

### Post by ve4cib on 2009-01-06
It's a simple cut to the next image.  Image A one moment *bink* image B the next.

---

