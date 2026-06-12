---
title: "Save customized desktop backgroung"
date: 2014-02-12
forum: Desktop Environments
---

### Post by OldGrampa on 2014-02-12
I made a custom color background for my Ubunttu 13.10 desktop.
How do I save this, for when I want to call it up again.
Sometimes I might want another background,
but want to go back to the custom color one.

Tx for any comments.

---

### Post by Dennis N on 2014-02-12
Save the background image in your Pictures folder. You can select any image in that folder as your Desktop background instead of the default backgrounds.

Details:
Right Click on Desktop
Choose Change Desktop Background
Click the drop-down selector on the right that says "wallpapers" and change to "Pictures Folder"
Select your picture
Close the Window

---

### Post by OldGrampa on 2014-05-19
Dennis N:
What I am trying to save, is a custom color I made.
System Settings --> Appearance -->  select the small color rectangle (next to +-), and then choose custom.
Then I made a color that I liked, and made it for my desktop wallpaper.
How might I save this custom color, to a file that I can save in my pictures folder?

---

### Post by grumblebum2 on 2014-05-20
I use a script to reset my background to a favourite pic.
You could do the same to reset to a favourite gradient.
The first part is just an example how to set back to a picture.

Save as **background-reset.sh** and make executable.
```
#!/bin/bash

[COLOR="#808080"]## reset to my pic
#gsettings set org.gnome.desktop.background picture-uri 'file:///home/glen/Pictures/wallpaper/gold-drops.jpg'
#gsettings set org.gnome.desktop.background picture-options zoom[/COLOR]

## reset to my gradient
gsettings set org.gnome.desktop.background color-shading-type [COLOR="#FF8C00"]**vertical**[/COLOR]
gsettings set org.gnome.desktop.background picture-options [COLOR="#FF8C00"]**none**[/COLOR]
gsettings set org.gnome.desktop.background primary-color '[COLOR="#FF8C00"]**#199a108c01f6**[/COLOR]'     #color needs to be quoted 
gsettings set org.gnome.desktop.background secondary-color '[COLOR="#FF8C00"]**#8f8f59590202**[/COLOR]'    #color needs to be quoted
```

Set your gradient background in appearance then use dconf-editor to find [COLOR="#FF8C00"]**your settings**[/COLOR] and adapt the script.
May need to install dconf-editor
or 
run the gsettings **get** command to retrieve via terminal....
```
gsettings get org.gnome.desktop.background color-shading-type
gsettings get org.gnome.desktop.background picture-options
gsettings get org.gnome.desktop.background primary-color
gsettings get org.gnome.desktop.background secondary-color
```


Taking it a bit further you could make the script toggle between a favourite picture and a favourite gradient.
eg
```
#!/bin/bash

ShowPic=$(gsettings get org.gnome.desktop.background picture-options | tr -d "'")

if [ $ShowPic = "none" ]
	then
		## reset to my pic
		gsettings set org.gnome.desktop.background picture-uri '[COLOR="#FF8C00"]**file:///home/glen/Pictures/wallpaper/gold-drops.jpg**[/COLOR]'
		gsettings set org.gnome.desktop.background picture-options [COLOR="#FF8C00"]**zoom**[/COLOR]
	else
		## reset to my gradient
		gsettings set org.gnome.desktop.background color-shading-type [COLOR="#FF8C00"]**vertical**[/COLOR]
		gsettings set org.gnome.desktop.background picture-options [COLOR="#FF8C00"]**none**[/COLOR]
		gsettings set org.gnome.desktop.background primary-color '[COLOR="#FF8C00"]**#199a108c01f6**[/COLOR]'     #color needs to be quoted 
		gsettings set org.gnome.desktop.background secondary-color '[COLOR="#FF8C00"]**#8f8f59590202**[/COLOR]'    #color needs to be quoted\
fi
```
[COLOR="#FF8C00"]**Your settings**[/COLOR]

---

