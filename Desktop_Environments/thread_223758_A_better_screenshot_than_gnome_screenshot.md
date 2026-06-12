---
title: "A better screenshot than gnome screenshot"
date: 2006-07-26
forum: Desktop Environments
---

### Post by ardchoille on 2006-07-26
Here is a nice bash script for a customised screenshot. I don't much like the gnome screenshot app because I never figured out how to specify a certain filename or have it save to a path that I want it to save to.. nor have I figured out how to have it save some screenshots in .jpg, others in .png and still others in .gif. So, I wrote a bash script that can do all that.

You'll need to have imagemagick installed to be able to use this in gnome.

```

#!/bin/bash

# Ask the user to choose a directory and filename
mypath=`zenity --file-selection --directory`
myfilename=`zenity --entry --title="Screenshot" --window-icon=/usr/share/icons/gnome/32x32/apps/applets-screenshooter.png --text="Please enter a filename."`

# Check to see if the returned /path/file already exists
while [ -e $mypath"/"$myfilename ]
do
	zenity --error --title="Screenshot" --window-icon=/usr/share/icons/gnome/32x32/apps/applets-screenshooter.png --text="$mypath/$myfilename already exists. Please choose another filename."
	myfilename=`zenity --entry --title="Screenshot" --window-icon=/usr/share/icons/gnome/32x32/apps/applets-screenshooter.png --text="Please enter a filename."`
done

# Take the screenshot and save it to the /path/filename as returned above
import -frame $mypath"/"$myfilename

# Display the screenshot
display $mypath"/"$myfilename


```


And, here is one with a 5 second delay so you can minimise windows or change windows before the screenshot starts:

```

#!/bin/bash

# Delay for 5 seconds
sleep 5

# Ask the user to choose a directory and filename
mypath=`zenity --file-selection --directory`
myfilename=`zenity --entry --title="Screenshot" --window-icon=/usr/share/icons/gnome/32x32/apps/applets-screenshooter.png --text="Please enter a filename."`

# Check to see if the returned /path/file already exists
while [ -e $mypath"/"$myfilename ]
do
	zenity --error --title="Screenshot" --window-icon=/usr/share/icons/gnome/32x32/apps/applets-screenshooter.png --text="$mypath/$myfilename already exists. Please choose another filename."
	myfilename=`zenity --entry --title="Screenshot" --window-icon=/usr/share/icons/gnome/32x32/apps/applets-screenshooter.png --text="Please enter a filename."`
done

# Take the screenshot and save it to the /path/filename as returned above
import -frame $mypath"/"$myfilename

# Display the screenshot
display $mypath"/"$myfilename


```

I use the openbox window manager in gnome instead of Metacity and I have added a menu item for this bash script. I hope this can be of use to someone :)

---

### Post by aysiu on 2006-07-26
Does the delay script need to be that complex? I usually do something like this: ```
gnome-screenshot --delay 5
```

---

### Post by ardchoille on 2006-07-26
Well, the delay part is simply "sleep 5", and this script uses import which can save to many different formats.

With gnome-screenshot, how do you specify a path and filename for the screenshot? Can gnome-screenshot save in .png, .jpg, .gif and others?

---

### Post by aysiu on 2006-07-26
> **ardchoille said:**
> Well, the delay part is simply "sleep 5", and this script uses import which can save to many different formats.
Ah, I get it. Thanks for the clarification.

---

### Post by llamakc on 2006-07-26
I've always been fond of 'scrot'.

---

### Post by ardchoille on 2006-07-26
Hmm.. maybe I should try scrot and write a script to use it with zenity for nice gui's. My girlfriend doesn't like the command line and that is why I wrote a script that used zenity for the gui's.

---

### Post by tefflox on 2008-01-30
```
#!/bin/bash

# mkscreenshot  

  myfilename="Screenshot.png"

# Check to see if the returned /path/file already exists
  while [ -e /home/jess/screenshots/$myfilename ]
  do
      # zenity --error --title="Screenshot.png" --window-icon=/usr/share/icons/gnome/32x32/apps/applets-screenshooter.png --text="File Exists"
      
      myfilename=`zenity --entry --title="Screenshot" --window-icon=/usr/share/icons/gnome/32x32/apps/applets-screenshooter.png --text="Enter new filename."`
    
#### it's efficient to integrate a gnome-screenshot effect of appending '-[1-9]' (i don't know how to express that or do it :)
  done

# Take the screenshot and save it to the /path/filename as returned above
import -frame /home/jess/screenshots/$myfilename

# Display the screenshot
display /home/jess/screenshots/$myfilename

> **ardchoille said:**
> Here is a nice bash script for a customised screenshot. I don't much like the gnome screenshot app because I never figured out how to specify a certain filename or have it save to a path that I want it to save to.. nor have I figured out how to have it save some screenshots in .jpg, others in .png and still others in .gif. So, I wrote a bash script that can do all that.

You'll need to have imagemagick installed to be able to use this in gnome.
```> **ardchoille said:**
> 

```

#!/bin/bash

# Ask the user to choose a directory and filename
mypath=`zenity --file-selection --directory`
myfilename=`zenity --entry --title="Screenshot" --window-icon=/usr/share/icons/gnome/32x32/apps/applets-screenshooter.png --text="Please enter a filename."`

# Check to see if the returned /path/file already exists
while [ -e $mypath"/"$myfilename ]
do
    zenity --error --title="Screenshot" --window-icon=/usr/share/icons/gnome/32x32/apps/applets-screenshooter.png --text="$mypath/$myfilename already exists. Please choose another filename."
    myfilename=`zenity --entry --title="Screenshot" --window-icon=/usr/share/icons/gnome/32x32/apps/applets-screenshooter.png --text="Please enter a filename."`
done

# Take the screenshot and save it to the /path/filename as returned above
import -frame $mypath"/"$myfilename

# Display the screenshot
display $mypath"/"$myfilename


```And, here is one with a 5 second delay so you can minimise windows or change windows before the screenshot starts:

```

#!/bin/bash

# Delay for 5 seconds
sleep 5

# Ask the user to choose a directory and filename
mypath=`zenity --file-selection --directory`
myfilename=`zenity --entry --title="Screenshot" --window-icon=/usr/share/icons/gnome/32x32/apps/applets-screenshooter.png --text="Please enter a filename."`

# Check to see if the returned /path/file already exists
while [ -e $mypath"/"$myfilename ]
do
    zenity --error --title="Screenshot" --window-icon=/usr/share/icons/gnome/32x32/apps/applets-screenshooter.png --text="$mypath/$myfilename already exists. Please choose another filename."
    myfilename=`zenity --entry --title="Screenshot" --window-icon=/usr/share/icons/gnome/32x32/apps/applets-screenshooter.png --text="Please enter a filename."`
done

# Take the screenshot and save it to the /path/filename as returned above
import -frame $mypath"/"$myfilename

# Display the screenshot
display $mypath"/"$myfilename


```I use the openbox window manager in gnome instead of Metacity and I have added a menu item for this bash script. I hope this can be of use to someone :)

---

