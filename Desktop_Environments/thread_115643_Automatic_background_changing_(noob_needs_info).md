---
title: "Automatic background changing (noob needs info)"
date: 2006-01-11
forum: Desktop Environments
---

### Post by DonQuixote on 2006-01-11
KDE has a neat little feature in its configuration app that will change the background every x number of minutes...

Does Gnome have a simular feature?  If not, is it possible to run the KDE configuration app in Gnome?

I tried installing the gnome-control-center using Synaptic, however I did not see any changes to my menus.  Do I need to add it manually?  If so, how is that done?

I appoligize for all the questions, however, the searches that I performed turned up nothing that seemed applicable to my situation.

I'm hoping that this will help others (if it's answered!)

Thanks!

John

---

### Post by Dr. Nick on 2006-01-11
I  used to use a script made by "poptones" I will paste it here. Their are a few elements that need to be modified to get it to work for you. Put all of your pictures in a single folder and then put the path in the red blank.

Create a new file on your desktop and copy/paste the below to it and save as *whatever*.sh. Right click it go to properties and make it exectuable, then double click it and it shoud change. This can be automateed using cron, but I have never done so.

```
 #!/bin/bash
WALLPAPERS=[COLOR=Red]~/wallpapers[/COLOR]

# find the identity of the current wallpaper...
# get the name...
THISONE=`gconftool-2 -g /desktop/gnome/background/picture_filename`

# Chop off the path
THISONE=${THISONE##*/}

# locate the filename by index in this directory
THISONE=`ls -1 $WALLPAPERS | grep -n $THISONE`

# make the grep string into a valid number
THISONE=0${THISONE%%:*}

# get a directory list
ALIST=( `ls -1 $WALLPAPERS` )

# get the number of lines in that list
RANGE=${#ALIST[@]}

# programmers trick to make a 'while' loop that runs at least once...
lastnum=1
number=1

while [[ "$lastnum" -eq "$number" ]]; do
# Now randomize until we have a new number that is not the same as the old one...
    let lastnum=$THISONE
    let "number = $RANDOM + $lastnum"
    let "number = $number % $RANGE"
done

# Set wallpaper to selection indexed by new "number"
gconftool-2 -t string -s /desktop/gnome/background/picture_filename $WALLPAPERS/${ALIST[$number]}
```

---

### Post by DonQuixote on 2006-01-16
Dr. Nick,

Thanks so much!  This works great!

John

---

### Post by DonQuixote on 2006-01-31
Hey,

I have a question about this script.  How could I modify it so that it changes the wallpaper on each of my desktops individually?

Thanks!

John

---

### Post by Dr. Nick on 2006-01-31
[quote=DonQuixote]Hey,

I have a question about this script.  How could I modify it so that it changes the wallpaper on each of my desktops individually?

Thanks!

John[/quote]

If you mean virtual desktops then I think you are out of luck :( I dont see a way to have different backgrounds on each of the 4 virtual desktops, so you cant use a script to automate something you can not do manually. 

I could be wrong on that though since I havent looked that deep into it right now, but my first guess would be that it cant be done at this time. 

If anyone has any furter info on the matter it would be nice though, I dont have much knowledge of writing scripts, I can really only edit parts of those written by others when I can understand the logic they used

---

### Post by aysiu on 2006-01-31
Isn't there some program in Synaptic called *chbg* that does this in Gnome?

---

### Post by Dr. Nick on 2006-02-03
[quote=aysiu]Isn't there some program in Synaptic called *chbg* that does this in Gnome?[/quote]

Their is, I installed it and it looks like an old gtk1 app, didnt seem to work right for me, though I didnt try real hard.

---

### Post by twisted_steel on 2006-02-03
I haven't tried it, but it looks like there is some app that changes the background as you change workspace, as there doesn't seem to be a way to have a unique wallpaper for each workspace.

See [http://www.gnomefiles.org/app.php?soft_id=104]("http://http://www.gnomefiles.org/app.php?soft_id=104").

---

### Post by chadk on 2006-12-20
I have been using this for a long time now but when I upgraded to edgy it stopped working.  Now I get this error (using an unmodified script as supplied above)
```

/home/username/wallpapers/.randomwallpaper: 18: Syntax error: "(" unexpected

```

---

### Post by chadk on 2006-12-23
I'm getting tired of the same background all the time and don't fancy changing it myself... can someone tell me what might cause this error? (see above post)  I've removed everything from the directory that wasn't an image file.  None of the files have any strange punctuation or anything...

---

### Post by DonQuixote on 2006-12-23
Chadk,

I'm still running Dapper, but I tried a utility I found in Synaptic called "Wallpaper-tray" and aside from a few bugs that I vaguely remember, it works fine for me.

John

---

### Post by chadk on 2006-12-23
Thanks Don!  Lol, simple solution...!  Problem though, it doesn't work with Edgy (it's in the repos but it doesn't function correctly)
```

 wallpaper-tray

(wp_tray:11622): libglade-WARNING **: could not find signal handler 'on_button_close_pressed'.

(wp_tray:11622): libglade-WARNING **: could not find signal handler 'on_button_apply_pressed'.

(wp_tray:11622): libglade-WARNING **: could not find signal handler 'on_button_add_dir_pressed'.

(wp_tray:11622): libglade-WARNING **: could not find signal handler 'on_button_rem_dir_pressed'.

```

Can't click any buttons, can't add wallpaper directories, can't close program using CLOSE button.  Oh well.

---

### Post by AndrewB on 2006-12-27
I've been trying to find a way in gnome to charge my backgrounds. I found this out in the wild [background switcher]("http://wallpapoz.akbarhome.com/").

 I'm not sure if it's elegant, but it allows setting a different background in each work space. Random switching and adjustable cycling time....It's gpl, it works in EDGY!:-D .
It's easy to install, though according to the notes, it'll run from its own folder.

Andrew

---

### Post by shawnhcorey on 2007-03-18
> **Dr. Nick said:**
> I  used to use a script made by "poptones" I will paste it here. Their are a few elements that need to be modified to get it to work for you. Put all of your pictures in a single folder and then put the path in the red blank.

Create a new file on your desktop and copy/paste the below to it and save as *whatever*.sh. Right click it go to properties and make it exectuable, then double click it and it shoud change. This can be automateed using cron, but I have never done so.

There is a bug in your code. The variable $lastnum goes from 1 to $RANGE but $number goes from 0 to $RANGE-1. Below is the corrected version.

```

#!/bin/bash
WALLPAPERS=~/info/backgrounds

# find the identity of the current wallpaper...
# get the name...
THISONE=`gconftool-2 -g /desktop/gnome/background/picture_filename`

# Chop off the path
THISONE=${THISONE##*/}

# locate the filename by index in this directory
THISONE=`ls -1 $WALLPAPERS | grep -n $THISONE`

# make the grep string into a valid number
THISONE=0${THISONE%%:*}

# get a directory list
ALIST=( `ls -1 $WALLPAPERS` )

# get the number of lines in that list
RANGE=${#ALIST[@]}

# programmers trick to make a 'while' loop that runs at least once...
lastnum=1
number=1

while [[ "$lastnum" -eq "$number" ]]; do
# Now randomize until we have a new number that is not the same as the old one...
    let "lastnum=$THISONE - 1"
    let "number = $RANDOM + $lastnum"
    let "number = $number % $RANGE"
done

# Set wallpaper to selection indexed by new "number"
gconftool-2 -t string -s /desktop/gnome/background/picture_filename $WALLPAPERS/${ALIST[$number]}

```

---

### Post by leoscuro on 2007-05-01
Hello, has any found any soution to this running under Feisty?

---

### Post by addux on 2007-11-23
I can't seem to get this script to work, and from what i can see my version of gnome stores its background information in a file located at ~/.gnome2/backgrounds.xml.  I could be wrong though.  Are there any scripts that use this file.  Any help is much appreciated. 

Thx in advance

---

