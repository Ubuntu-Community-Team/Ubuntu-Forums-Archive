---
title: "add a custom file association for a new mime type"
date: 2012-06-14
forum: Desktop Environments
---

### Post by richpri on 2012-06-14
I am running UBUNTU 11.10 and Gnome 3 [not UNITY].

I am attempting to add a custom file association for a application called Rails. This application has nothing to do with "Ruby on rails".

Here are the steps I followed:

1. Placed this Overrides.xml file on    /usr/share/mime/packages

```
<?xml version='1.0' encoding='utf-8'?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
    <mime-type type="application/rails">
        <glob pattern="*.rails"/>
    </mime-type>
</mime-info>
```

2. Executed update-mime-database /usr/share/mime

3. Placed this desktop file in /usr/share/applications/rails.desktop

```
[Desktop Entry]
Exec=/home/rich/Rails/rails.sh %U
Version=1.1
Name=Rails for 18xx
GenericName=Rails
X-GNOME-FullName=Rails for 18xx
Comment=This is the 18xx game software
Path=/home/rich/rails
Icon=/home/rich/rails/logo.png
StartupNotify=true
Terminal=false
Type=Application
```

4. Added this line to /usr/share/applications/defaults.list

```
application/rails=rails.desktop
```

5. Logged out and back in.

But when I select a .rails file nothing happens!
What am I doing wrong?

By the way the directory for /home/rich/Rails is

```
-rw-rw-r-- 1 rich rich  366721 2012-06-13 21:39 18xx.log
-rw-r--r-- 1 rich rich     745 2012-05-30 06:14 AUTHORS
drwxr-xr-x 9 rich rich    4096 2012-05-30 06:14 lib
-rw-r--r-- 1 rich rich   18009 2012-05-30 06:14 LICENSE
-rw-r--r-- 1 rich rich 3467059 2012-05-30 06:14 rails-1.7.5.jar
-rwxr-xr-x 1 rich rich      43 2012-05-30 06:14 rails.sh
-rw-r--r-- 1 rich rich     738 2012-05-30 06:14 README
-rw-r--r-- 1 rich rich     611 2012-05-30 06:14 readme.txt
```

and /home/rich/Rails/rails.sh contains
```

#!/bin/bash
java -jar ./rails-1.7.5.jar $1
```

---

### Post by mc4man on 2012-06-14
I would do a bit differently & not bother with /usr/share/applications/defaults.list
Shown here, talks about doing locally or system wide
[http://ubuntuforums.org/showthread.php?p=11924283#post11924283](http://ubuntuforums.org/showthread.php?p=11924283#post11924283)

Quickly did here based on what you did though used a script in ~/bin for something else (irrelevant to process, just needed something

Basically this 
created a  ~/Documents/rails.xml using your .xml
Then - 
```
sudo xdg-mime install --novendor  ~/Documents/rails.xml
```
 ```
sudo update-mime-database   /usr/share/mime
```

```
sudo gedit  /usr/share/applications/rails.desktop
```
used your .desktop as is just altering paths & icon to me, _but_ added this to bottom
```
MimeType=application/rails
```

Then ended with
```
sudo xdg-desktop-menu install --novendor /usr/share/applications/rails.desktop
```

screen shows found association, I'm sure you'll get the idea

---

### Post by richpri on 2012-06-14
Thanks for your reply.

I followed your steps exactly and the problem persists.

Right clicking on a rails file does get a menu with 
"open with rails for 18xx" at the top but when I click 
on that option nothing happens.

Double clicking on the file also produces a null result.

Is there any log or trace of the mime code that could
throw any more light on this situation?

---

### Post by mc4man on 2012-06-14
It works ok here to the extent I can try. (open a script on the dummy .rails file

A few things - 
I usually do locally by putting the .desktop in ~/.local/share/applications but works ok here in /usr/share/applications

the "sudo xdg-desktop-menu install --novendor /usr/share/applications/rails.desktop" command is not needed locally & probably not if putting the .desktop in /usr/...
Once you use it then if you edit the .desktop you have to re-run the command to realize the edit

So - the most likely cause of nothing happening is either  your Exec= line isn't correct in this instance  - opening the file from context menu or more likely the script itself in this instance.
What I might do is uninstall so you could edit the .desktop freely if need be - (any edits should then take immediate effect
```
sudo xdg-desktop-menu uninstall  /usr/share/applications/rails.desktop
```

Then try adjusting your script or editing your Exec= line to get it to work-  
(maybe try quoting the $1

---

### Post by richpri on 2012-06-14
Thanks for your help but I am giving up on this. 
I think that I will wait to see if the ability 
to add a custom file association for a new mime 
type will be restored to gnome 2 like it was in
the old gnome.  I sure hope so.

---

