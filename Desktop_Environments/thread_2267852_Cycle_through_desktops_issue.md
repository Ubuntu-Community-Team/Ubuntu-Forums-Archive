---
title: "Cycle through desktops issue"
date: 2015-03-04
forum: Desktop Environments
---

### Post by JDAIII on 2015-03-04
First things first, I'm on Ubuntu Gnome 14.10 and I'm using zsh as my shell. I got this script from another forum and it worked for me on 13.10 and 14.04, but I cannot figure out why it is not working now. I placed this script in it's own file ~/.backgrounds.sh and I set it with +x owned by my user. And in my ~/.zshrc file I have the command EXEC=/home/jd/.backgrounds.sh under my aliases and above a function, all of which work perfectly. This does not appear to be executing though and I'm at a loss.

What am I doing wrong? The path is correct and it has 20 something background files in it.

The script here is everything that is contained within ~/.bachgrounds.sh

```
#!/bin/bash

cd /home/jd/Pictures/Backgrounds


while [ 1 ]
 do
 set -- *
 length=$#
 random_num=$((( $RANDOM % ($length) +1) ))


 gsettings set org.gnome.desktop.background picture-uri "file:/home/jd/Pictures/Backgrounds/${!random_num}"


 sleep 300
done
```

---

### Post by CantankRus on 2015-03-04
The gsettings value should be of the form....
```
file:[COLOR="#FF0000"]**///**[/COLOR]home/jd/Pictures/Backgrounds/${!random_num}
```

You can test by setting it back to default....
```
**[COLOR="#008000"]glen@Trusty:~$[/COLOR] gsettings reset org.gnome.desktop.background picture-uri**
**[COLOR="#008000"]glen@Trusty:~$[/COLOR] gsettings get org.gnome.desktop.background picture-uri**
'file:**[COLOR="#FF0000"]///[/COLOR]**usr/share/backgrounds/warty-final-ubuntu.png'
```

---

### Post by JDAIII on 2015-03-04
That worked. Thanks. I knew that it was something both simple and layer 8 related.

---

