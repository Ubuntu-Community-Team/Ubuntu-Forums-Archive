---
title: "mising icon for volume in panel"
date: 2006-01-05
forum: Desktop Environments
---

### Post by Mr..Yeti on 2006-01-05
Hi
I upgraded to Breezy using synaptic's smart upgrade. Now when I log on the volume control icon has disappered. 
The applet is still there, and I can still change the volume, but the icon is gone.

Does anyone now how to get the volume control icon back on the panel?

---

### Post by kingsidy on 2006-01-05
i think that you right click on the panel, then click on "add applet" then select volume or something like that

---

### Post by Mr..Yeti on 2006-01-05
Nope, that didn't work :( 
The applet does appear, but the icon is still missing.

---

### Post by schilcha on 2006-01-05
I've had a similar problem with some (incomplete?) icon-themes.  Try to select "Human" in System -> Preferences -> Theme -> Theme Details -> Icons.

Give it a try, although I can't really imaging, why the icon-theme should be broken after an update if it was ok before...

Anyways, 
   good luck!

---

### Post by Mr..Yeti on 2006-01-06
Thanks alot :)
It works now, i set the icon theme i was using to "inherit" gnome's icon theme and the icon has reapeared. Aswell as some icons for other programs.
Thanks alot :)

---

### Post by dcstar on 2006-01-06
[QUOTE=schilcha]I've had a similar problem with some (incomplete?) icon-themes.  Try to select "Human" in System -> Preferences -> Theme -> Theme Details -> Icons.

Give it a try, although I can't really imaging, why the icon-theme should be broken after an update if it was ok before...

Anyways, 
   good luck![/QUOTE]
There is a known bug with a lot of the non-standard themes in Breezy, this problem pops up all the time......           :(

---

### Post by OneSeventeen on 2006-02-22
Just to point out how to do this, simply go to the theme preferences window (System>Preferences>Theme) then click "Theme Details" for the theme you use.  Then click on the icon tab then click on "Go to Theme Folder".

Now go to the folder for the theme you want to edit, and open the "index.theme" file with your favorite text editor. In the line that says "Inherits" add "gnome" to the beginning or end of it.

Save the file, then change your icon set to something else, then change it back to what you just modified.

It should work fine now!  (now if anyone has tips on how to change the sound-icon there, I'd be appreciative)

---

### Post by jcaceres on 2006-03-01
I had the same problem and i resolve it ..
follow the instrunctions ..
You have to know the "icons theme name"  that is un use on your desktop. That you can do it with:

 ls -l $HOME/.icons 
or system --> Administration --> Theme --> Theme Details --> Icons

Then you  execute .. 

cd /usr/share/icons/gnome && tar -cvf $HOME/.icons/<ICON_THEME_NAME>/vol.tar `find ./ -type f -name "*vol*" -print `

Where ICON_THEME_NAME is the current "icons theme name".

then you execute .. 

cd $HOME/.icons/<ICON_THEME_NAME>&& tar -xvf vol.tar

and it's ready ... 

Please send a feedback to know if it works ...

---

