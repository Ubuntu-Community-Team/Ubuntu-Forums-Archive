---
title: "Replacing the Panel Menu Icon with a Ubuntu Orb"
date: 2007-09-15
forum: Desktop Effects &amp; Customization
---

### Post by acelin on 2007-09-15
How do i change the Menu Icon in Feisty- on the panel up top- to a Ubuntu Orb?

This menu is the one that has places and systems in a menu...:guitar::guitar::guitar::guitar:

---

### Post by FuturePilot on 2007-09-15
Do you mean right click on the panel>Add To Panel>Main Menu:?:

---

### Post by acelin on 2007-09-15
yes- how would I change its icon to a Ubuntu orb?

---

### Post by dougfractal on 2007-09-15
[IMG]http://www.brianward.us/myspace/public/ubuntu-orb.png[/IMG]
do you mean this image.

look in 
/usr/share/icons/gnome/22x22/places
start-here.png
also you might have to fix all the other sizes.

---

### Post by acelin on 2007-09-15
You you give me more detailed instructions...

---

### Post by dougfractal on 2007-09-15
Well I started playing with inkscape and now I offer you a choice.
[IMG]http://fractaldimension.org.uk/ubuntu/dougubuntuorb.png[/IMG]

so
```
wget -O ubuntu-orb.png http://www.brianward.us/myspace/public/ubuntu-orb.png
```

or
```
wget -O ubuntu-orb.png http://fractaldimension.org.uk/ubuntu/dougubuntuorb.png
wget -O start-here.svg http://fractaldimension.org.uk/ubuntu/start-here-orb.svg
```

then 
[CODEgedit newicon.sh[/CODE]
copy paste
> #!/bin/bash
# neworbicon
#  replace the start-here icon with orb
THEME="Human"
function newicon
{
cp ubuntu-orb.png start-here.png
mogrify -resize $1 start-here.png
#sudo mv /usr/share/icons/$THEME/$1/places/start-here.png /usr/share/icons/$THEME/$1/places/start-here-old.png
sudo mv start-here.png /usr/share/icons/$THEME/$1/places/start-here.png
}
newicon 22x22
newicon 24x24
newicon 32x32
newicon 48x48
newicon 16x16
newicon 8x8
#sudo /usr/share/icons/$THEME/scalable/places/start-here.svg usr/share/icons/$THEME/scalable/places/start-here-org.svg
#sudo cp start-here.svg /usr/share/icons/$THEME/scalable/places/start-here.svg
#sudo mv /usr/share/icons/$THEME/icon-theme.cache /usr/share/icons/$THEME/icon-theme.cache.old

```
chmod +x newicon.sh
./newicon.sh
```

this is for Main Menu . change will take place on resize

---

### Post by acelin on 2007-09-16
hmm. that didnt work ...
it said it failed after the newicon code...

---

### Post by dougfractal on 2007-09-16
Sorry. It worked for me.  

It did fail to copy in some directories that did't exist, but the dirs that did exist it was fine.
> 
nautilus  /usr/share/icons/Human/22x22/places/

Are you using Human theme? If not edit the THEME="Human" in the script.

can you post the fail log  
or just resize and place manually.

---

### Post by acelin on 2007-09-16
What do I do once it has opened that file right before you paste in the last code?

---

### Post by dougfractal on 2007-09-16
my spelling sucks.
> 
nautilus /usr/share/icons/Human/22x22/places/

or just use the file browser (nautilus)  to open the directory.

If you see the new icon. then the script worked.
else start again

[COLOR="Gray"]1.download image 
2. rename to  ubuntu-orb.png  (OK I made a typo in my script (ubuntu-orb1.png))[/COLOR]

run script again.

---

### Post by acelin on 2007-09-16
ok- I am really confused... what needs to be changed... please be clearer! I am still new to this...

---

### Post by dougfractal on 2007-09-16
I made some typos which I've corrected.[http://ubuntuforums.org/showpost.php?p=3370849&postcount=6](http://ubuntuforums.org/showpost.php?p=3370849&postcount=6)

> 
**sed -i 's/ubuntu-orb1.png/ubuntu-orb.png/'  newicon.sh **  # this will change ubuntu-orb1.png   to ubuntu-orb.png in the file newicon.sh 
**./newicon.sh**

**or** just gedit newicon.sh
find/replace ubuntu-orb1.png   to ubuntu-orb.png

**or **
follow the corrected post #6


 I also changed my orb png

---

### Post by davem2312 on 2007-09-16
type in 

```
gconf-editor
```

in the terminal, then navigate to apps/panel/objects/... and look through the objects.. there will be a position and object-type.  The object type will be **menu-object**, and position will be number of pixels from left, so a low number if it is on the right hand side of the screen.

Anyway, once you have selected the correct object, check "use custom icon", and then in the "custom icon" field, paste the location of your new image.  For example "/home/user/menu_icon.png"

---

### Post by CowzRule on 2007-09-17
Have a look through the following thread
[http://ubuntuforums.org/showthread.php?t=498890]("http://ubuntuforums.org/showthread.php?t=498890")

---

### Post by acelin on 2007-09-17
Dang- this isnt working...

---

### Post by dougfractal on 2007-09-17
> Dang- this isnt working...


this is my output for a successful change
> ./newicon.sh
mv: cannot move `start-here.png' to `/usr/share/icons/Human/8x8/places/start-here.png': No such file or directory

> ls -l /usr/share/icons/Human/22x22/places/start-here.png
-rw-r--r-- 1 doug doug 1697 2007-09-17 00:59 /usr/share/icons/Human/22x22/places/start-here.png


If you have the new icon in the folder
then all I can think is that you are not using "Human" Theme.

I did move the theme.cache
> THEME="Human" ; sudo mv /usr/share/icons/$THEME/icon-theme.cache /usr/share/icons/$THEME/icon-theme.cache.old

The icons only changed for "Main menu" on panel resize (go to 68, then back to whatever)
and "Menu Bar" on new login.

post the output from ./newicon.sh and the ls -l /usr/share/icons/Human/22x22/places/start-here.png

---

### Post by acelin on 2007-09-17
root@salane-laptop:/home/salane# wget -O ubuntu-orb.png [http://fractaldimension.org.uk/ubuntu/dougubuntuorb.png](http://fractaldimension.org.uk/ubuntu/dougubuntuorb.png)
--18:14:23--  [http://fractaldimension.org.uk/ubuntu/dougubuntuorb.png](http://fractaldimension.org.uk/ubuntu/dougubuntuorb.png)
           => `ubuntu-orb.png'
Resolving fractaldimension.org.uk... 82.165.119.228
Connecting to fractaldimension.org.uk|82.165.119.228|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 77,767 (76K) [image/png]

100%[====================================>] 77,767       112.95K/s             

18:14:24 (112.81 KB/s) - `ubuntu-orb.png' saved [77767/77767]

root@salane-laptop:/home/salane# wget -O start-here.svg [http://fractaldimension.org.uk/ubuntu/start-here-orb.svg](http://fractaldimension.org.uk/ubuntu/start-here-orb.svg)
--18:14:49--  [http://fractaldimension.org.uk/ubuntu/start-here-orb.svg](http://fractaldimension.org.uk/ubuntu/start-here-orb.svg)
           => `start-here.svg'
Resolving fractaldimension.org.uk... 82.165.119.228
Connecting to fractaldimension.org.uk|82.165.119.228|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 29,726 (29K) [image/svg-xml]

100%[====================================>] 29,726        71.94K/s             

18:14:50 (71.90 KB/s) - `start-here.svg' saved [29726/29726]

root@salane-laptop:/home/salane# gedit newicon.sh

(gedit:13043): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
root@salane-laptop:/home/salane# chmod +x newicon.sh
root@salane-laptop:/home/salane# ./newicon.sh
mv: cannot move `start-here.png' to `/usr/share/icons/Truth/22x22/places/start-here.png': No such file or directory
mv: cannot move `start-here.png' to `/usr/share/icons/Truth/24x24/places/start-here.png': No such file or directory
mv: cannot move `start-here.png' to `/usr/share/icons/Truth/32x32/places/start-here.png': No such file or directory
mv: cannot move `start-here.png' to `/usr/share/icons/Truth/48x48/places/start-here.png': No such file or directory
mv: cannot move `start-here.png' to `/usr/share/icons/Truth/16x16/places/start-here.png': No such file or directory
mv: cannot move `start-here.png' to `/usr/share/icons/Truth/8x8/places/start-here.png': No such file or directory
root@salane-laptop:/home/salane# just gedit newicon.sh
bash: just: command not found
root@salane-laptop:/home/salane# find/replace ubuntu-orb1.png to ubuntu-orb.png
bash: find/replace: No such file or directory
root@salane-laptop:/home/salane# 
root@salane-laptop:/ho

---

### Post by dougfractal on 2007-09-17
You are using "Truth" theme
you are copying/paste any old text>    "just gedit newicon.sh
bash: just: command not found
root@salane-laptop:/home/salane# find/replace ubuntu-orb1.png to ubuntu-orb.png
bash: find/replace: No such file or directory
you are running as root. BAD (unless you know what you are doing)

tell me where you got "Truth" from.

---

### Post by acelin on 2007-09-17
Truth is my current theme- gnome look

---

### Post by acelin on 2007-09-17
Can I get a ubuntu studio orb that is really really black instead? And on the Ubuntu Studio theme?

---

### Post by dougfractal on 2007-09-17
[http://www.robertourso.com/?p=16](http://www.robertourso.com/?p=16)

Truth doesn't have the same ubuntu file layout so my script won't work.

Ubuntu Studio theme
[https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromFeisty](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromFeisty)

---

### Post by acelin on 2007-09-17
Could you make one for Ubuntu Studio? I already had that, I was just using Trith at the time- but if I get the orb to work on Studio, I will use that all the time...

Thanks for your help so far..

---

### Post by dougfractal on 2007-09-18
sorry no can do.

---

### Post by acelin on 2007-09-18
Can anyone help? I have seen people chaging it to a start button like xp before-

---

### Post by warduke on 2008-03-09
I was bored and wanted to try my hand at the logo.

[IMG]http://i26.tinypic.com/30athcw.png[/IMG]
[IMG]http://i27.tinypic.com/5mjyp.png[/IMG]

---

### Post by Sonic132 on 2008-03-14
Ok probably a stupid question but I'll ask anyway.
In Windows Vista(curse the name) the orb sticks out some from the taskbar. Anyway of doing that with this one? Or getting the real Win Vista orb to replace?

Also the ubuntu orb you guys made doesn't work on most of the sizes. So I have to use a really BIG size to see it correctly.

I got this code in Terminal after running your script:

```
./newicon.sh: line 8: mogrify: command not found
./newicon.sh: line 8: mogrify: command not found
./newicon.sh: line 8: mogrify: command not found
./newicon.sh: line 8: mogrify: command not found
./newicon.sh: line 8: mogrify: command not found
./newicon.sh: line 8: mogrify: command not found
mv: cannot move `start-here.png' to `/usr/share/icons/Human/8x8/places/start-here.png': No such file or directory

```

---

### Post by Sonic132 on 2008-03-15
:guitar: bumpage!

---

