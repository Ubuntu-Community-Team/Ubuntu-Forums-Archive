---
title: "Shell Script help"
date: 2008-10-27
forum: Desktop Environments
---

### Post by smirnoff76 on 2008-10-27
I wonder if anyone can help? 

I am working on a shell script and have the first part of my script done however as part of the scrip I need it to create a file called Default to /etc/gdm/PostLogin and add the following text in:


#!/bin/sh
#
# Note that output goes into the .xsession-errors file for easy debugging
#
# Extract the wallpaper filename
WALLPAPER="`cat ~/.gconf/desktop/gnome/background/%gconf.xml | sed -n -e 'N
s/^[ \t]*<entry name="picture_filename".*\n[ \t]*<stringvalue>\(.*\)<\/stringvalue>.*$/\1/ip'`"

# Check if the wallpaper file exists. If yes - draw it, if no - use primary background color
if [ -e "$WALLPAPER" ] && [ -f "$WALLPAPER" ] ; then
	xsetbg -onroot "$WALLPAPER"
else
	
	PRIMARY_COLOR="`cat ~/.gconf/desktop/gnome/background/%gconf.xml | sed -n -e 'N
s/^[ \t]*<entry name="primary_color".*\n[ \t]*<stringvalue>\(.*\)<\/stringvalue>.*$/\1/ip'`"
	xsetroot -cursor_name left_ptr -solid "$PRIMARY_COLOR"
fi

exit 0


The problem is I have no idea how to script this part of the file can anyone give any help / pointers? 

The purpose of the scrip is actually based on this link [http://ubuntuforums.org/showthread.php?t=753261](http://ubuntuforums.org/showthread.php?t=753261) which is a mjor pet peeve of mine. 
I am fairly new to ubuntu and the only script I have written so far is an install script for a new install of all the packages I require so I am now trying my hand at other scripting tasks (which I plan to post in the tips n tricks section once done and tested) so any help would be really appreciated!

Thanks in advance.

---

### Post by Claus7 on 2008-10-27
Hello,

maybe I have not get it correctly, yet from what I can make out is that you have a text and you want to create a file, which will include this text under /etc/gdm/PostLogin

So inside the script do :

```
echo "
your text
...
... " > /etc/gdm/PostLogin/Default
```

and it will do what you want.

Yet, you should pay attention to the fact that in order to create a file inside the etc directory, you should be root. So either you should have the right permissions in your script (chmod 777 name_of_your_script) in order to accomplish that, or you should type sudo in front of the command. When the script will run, it will ask you for your password.

Now if you have this text let's say saved as test.txt in your Desktop you could do also :
```
sudo awk '{print}' ~/Desktop/test.txt > /etc/gdm/PostLogin/Default
```

Hope this helped,
Regards!

---

### Post by smirnoff76 on 2008-10-27
Thanks Claus7 that is a great help. 
The script will be running in sudo as there are some packages that need downloading and installing as part of the script. 

I will give it a go this evening and let you know how I get on with it.

---

### Post by mjparme on 2008-10-27
You could echo each line but that would be error prone and tedious, redirect the cat command to a file delimited with a marker, EOF is used by convention but you can use whatever you want. This script illustrates. Note the use of EOF at the end, this says cat all lines to the specified file until the marker is seen (EOF in this case)

```

#!/bin/sh

file=testFile.txt
cat >> $file << EOF
#!/bin/sh
#
# Note that output goes into the .xsession-errors file for easy debugging
#
# Extract the wallpaper filename
WALLPAPER="`cat ~/.gconf/desktop/gnome/background/%gconf.xml | sed -n -e 'N
s/^[ \t]*<entry name="picture_filename".*\n[ \t]*<stringvalue>\(.*\)<\/stringvalue>.*$/\1/ip'`"

# Check if the wallpaper file exists. If yes - draw it, if no - use primary background color
if [ -e "$WALLPAPER" ] && [ -f "$WALLPAPER" ] ; then
xsetbg -onroot "$WALLPAPER"
else

PRIMARY_COLOR="`cat ~/.gconf/desktop/gnome/background/%gconf.xml | sed -n -e 'N
s/^[ \t]*<entry name="primary_color".*\n[ \t]*<stringvalue>\(.*\)<\/stringvalue>.*$/\1/ip'`"
xsetroot -cursor_name left_ptr -solid "$PRIMARY_COLOR"
fi

exit 0
EOF

```

---

### Post by lswb on 2008-10-27
Disregard, sorry

---

