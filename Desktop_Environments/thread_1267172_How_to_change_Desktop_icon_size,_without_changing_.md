---
title: "How to change Desktop icon size, without changing global icon size in Nautilus ?"
date: 2009-09-15
forum: Desktop Environments
---

### Post by sunchiqua on 2009-09-15
Is it possible to change the size of Desktop icons, without changing global icon size in Nautilus preferences ( icon view ) ? I would like to decrease the size of my desktop icons, while keeping Nautilus icon view @ 100%.

Any suggestions/ideas ?

---

### Post by VCoolio on 2009-09-15
Open gconf-editor, navigate to apps > nautilus > desktop > icon_view and see if the value for default_zoom_level does anything you like. I don't know the possible values, but try 'small' or 'low' or see if google has any help.

Edit: ([here you go]("http://ubuntuforums.org/archive/index.php/t-497027.html")):
smallest = 25%
smaller = 50%
small = 75%
standard = 100%
large = 150%
larger = 200%
largest = 400%

---

### Post by dumblebee100 on 2009-09-15
> **sunchiqua said:**
> Is it possible to change the size of Desktop icons, without changing global icon size in Nautilus preferences ( icon view ) ? I would like to decrease the size of my desktop icons, while keeping Nautilus icon view @ 100%.

Any suggestions/ideas ?

I have done something like that ..

it all depends on your icon theme ...

the settings of nautilus zoom just zooms everything like icon size ,,icon name ...and items count  if u enable it ...so over all the icon grid gets larger and larger by zooming in nautilus ..

I think u want to keep everything constant and just increase or decrease the icon size ...

I can answer you if u give me details of ur colour theme ...if possible provide me the index.theme file of your icon them ...I will look into the file and tell you how to do it ..

because some are not possible to edit while some are possible to edit ..its more like trial and error method ..so gimme details 

I will try it on my system and then post your solution 

right now I have something like u want ...I have hydroxygen icon theme ...

I have nautilus zoom level to 100% but I have icons which are bigger than usually is ..I mean the icons which should appear for 150% but for 100% zoom itself ..
I made this because I see my monitor from long distance so differentiating between script ..text file ..tar.gz and tar.bz2 would be lot helpful when we have big icons and reaming things are as it is 

just see my screenshot and tell me if u want like this ..
here nautilus is 100% zoom level but I have icons for 150% zoom level

---

### Post by sunchiqua on 2009-09-15
> **VCoolio said:**
> Open gconf-editor, navigate to apps > nautilus > desktop > icon_view and see if the value for default_zoom_level does anything you like. I don't know the possible values, but try 'small' or 'low' or see if google has any help.

Edit: ([here you go]("http://ubuntuforums.org/archive/index.php/t-497027.html")):
smallest = 25%
smaller = 50%
small = 75%
standard = 100%
large = 150%
larger = 200%
largest = 400%

I can't seem to find anything related to icons under nautilus/desktop in gconf-editor.

> **dumblebee100 said:**
> I have done something like that ..

it all depends on your icon theme ...

the settings of nautilus zoom just zooms everything like icon size ,,icon name ...and items count  if u enable it ...so over all the icon grid gets larger and larger by zooming in nautilus ..

I think u want to keep everything constant and just increase or decrease the icon size ...

I can answer you if u give me details of ur colour theme ...if possible provide me the index.theme file of your icon them ...I will look into the file and tell you how to do it ..

because some are not possible to edit while some are possible to edit ..its more like trial and error method ..so gimme details 

I will try it on my system and then post your solution 

right now I have something like u want ...I have hydroxygen icon theme ...

I have nautilus zoom level to 100% but I have icons which are bigger than usually is ..I mean the icons which should appear for 150% but for 100% zoom itself ..
I made this because I see my monitor from long distance so differentiating between script ..text file ..tar.gz and tar.bz2 would be lot helpful when we have big icons and reaming things are as it is 

just see my screenshot and tell me if u want like this ..
here nautilus is 100% zoom level but I have icons for 150% zoom level

The problem is not the quality of icons, but the fact that I can't set separate zoom levels for desktop and file browser ( Nautilus ).

---

### Post by dumblebee100 on 2009-09-15
desktop is not a different thing in gnome 

its just the part of nautilus 

the desktop is totally dependent on nautilus 

preferences in nautilus changes desktop things 

at present you cant seperate the desktop with nautilus

---

### Post by sunchiqua on 2009-09-15
> **dumblebee100 said:**
> desktop is not a different thing in gnome 

its just the part of nautilus 

the desktop is totally dependent on nautilus 

preferences in nautilus changes desktop things 

at present you cant seperate the desktop with nautilus

I know - if there would be a separate place where I could customize my desktop icons, instead of doing it in Nautilus, I would not ask this :)

---

### Post by dumblebee100 on 2009-09-15
at present there is nothing like that

---

### Post by Minsky on 2010-05-29
Dumblebee, just on the off chance that you're still monitoring this thread, could you explain how you increased the size of your icons whilst still maintaining the default zoom level, as this is exactly what I'd like to do as well. I'm also using the Hydroxygen icon set. Hope you or anyone else looking in can help. Thanks.

---

### Post by dumblebee100 on 2010-05-29
@minsky

I found a solution for your case 

with some simple editing in the index.theme file you can accomplish such thing( I mean zoomed icons for default size like 72x72 pixel icons for zoom level 100% ..by default the theme gives only 48x48 icons for zoom level 100%) 

I would like to tell the key advantages by doing this

1)you will be able to distinguish the file even from far ..or just by a glance ( in my view icons play a vital role in distinguishing the filetypes so I tested on hydroxygen because its most customizable icon set available out there)
2)easy pin pointing your files over the mess of files
3)bigger icons for same icon grid

disadvantages
1)you cannot access the 48x48 pixel icons anymore( because we are displaying 72x72 icons instead of 48x48 ) ...ofcourse you can change the theme.index if you want them back but I dont see any use because bigger icons won my heart
2)when you are in 100% zoom level things would be good ( I mean bigger icons and everything seems just perfect ) but when you decrease the zoom level like 66% then the theme should display the 32x32 icons ..so the sudden difference from 72x72 icons to 32x32 may be a little difficult for some people ( but in my case I never change any view or zoom level so it works perfect for me)

for some technical information as from my point of view and testing 
I have tested only hydroxygen ( with success) and some other ( without much success) I dont know if the same sizes applies for the zoom levels in other icon themes so its up to you when you try different icon themes because every icon theme has different procedure to do such things and some dont even support

128x128 is for 200 and 400% zoom levels
72x72 is for 150% zoom
48x48 is for 100% zoom
32x32 is not taking part in displaying stuff 
24x24 is for 66% zoom
22x22 is for 50% zoom
16x16 is for 33% zoom

so after this hack our icons are same size for 100% zoom and 150% zoom because we are using same 72x72 pixel icons for both zoom levels ..just like 200% and 400%

I would like to give you my index.theme 
I have altered only places and mimetypes because I was interested only in bigger icons for folders and other filetypes but if you are interested in other areas like (emotes,actions,apps,categories,devices,devices,emblems,mimetypes,places,status )  you can change as per your wish ..but better make a backup before hacking 

```
[Icon Theme]
Name=hydroxygen
Comment=The most complete and self-customizable iconset ever made.
Inherits=gnome, hicolor
Example=x-directory-normal

Directories=16x16/emotes,16x16/actions,16x16/apps,16x16/categories,16x16/devices,16x16/devices,16x16/emblems,16x16/mimetypes,16x16/places,16x16/status,22x22/emotes,22x22/actions,22x22/apps,22x22/categories,22x22/devices,22x22/devices,22x22/emblems,22x22/mimetypes,22x22/places,22x22/status,24x24/emotes,24x24/actions,24x24/apps,24x24/categories,24x24/devices,24x24/devices,24x24/emblems,24x24/mimetypes,24x24/places,24x24/status,32x32/emotes,32x32/actions,32x32/apps,32x32/categories,32x32/devices,32x32/devices,32x32/emblems,32x32/mimetypes,32x32/places,32x32/status,48x48/emotes,48x48/actions,48x48/apps,48x48/categories,48x48/devices,48x48/devices,48x48/emblems,72x72/mimetypes,72x72/places,48x48/status,128x128/emotes,128x128/actions,128x128/apps,128x128/categories,128x128/devices,128x128/devices,128x128/emblems,128x128/mimetypes,128x128/places,128x128/status,72x72/emotes,72x72/actions,72x72/apps,72x72/categories,72x72/devices,72x72/emblems,72x72/mimetypes,72x72/places,72x72/status,16x16/stock,22x22/stock,24x24/stock,32x32/stock,48x48/stock,72x72/stock,128x128/stock

[16x16/emotes]
Size=16
Context=Stock
Type=Fixed

[16x16/stock]
Size=16
Context=Stock
Type=Fixed

[16x16/actions]
Size=16
Context=Actions
Type=Fixed

[16x16/apps]
Size=16
Context=Applications
Type=Fixed

[16x16/categories]
Size=16
Context=Categories
Type=Fixed

[16x16/devices]
Size=16
Context=Devices
Type=Fixed

[16x16/emblems]
Size=16
Context=Emblems
Type=Fixed

[16x16/mimetypes]
Size=16
Context=MimeTypes
Type=Fixed

[16x16/places]
Size=16
Context=Places
Type=Fixed

[16x16/status]
Size=16
Context=Status
Type=Fixed

[22x22/emotes]
Size=22
Context=Stock
Type=Fixed

[22x22/stock]
Size=22
Context=Stock
Type=Fixed

[22x22/actions]
Size=22
Context=Actions
Type=Fixed

[22x22/apps]
Size=22
Context=Applications
Type=Fixed

[22x22/categories]
Size=22
Context=Categories
Type=Fixed

[22x22/devices]
Size=22
Context=Devices
Type=Fixed

[22x22/emblems]
Size=22
Context=Emblems
Type=Fixed

[22x22/mimetypes]
Size=22
Context=MimeTypes
Type=Fixed

[22x22/places]
Size=22
Context=Places
Type=Fixed

[22x22/status]
Size=22
Context=Status
Type=Fixed

[24x24/emotes]
Size=24
Context=Stock
Type=Fixed

[24x24/stock]
Size=24
Context=Stock
Type=Fixed

[24x24/actions]
Size=24
Context=Actions
Type=Fixed

[24x24/apps]
Size=24
Context=Applications
Type=Fixed

[24x24/categories]
Size=24
Context=Categories
Type=Fixed

[24x24/devices]
Size=24
Context=Devices
Type=Fixed

[24x24/emblems]
Size=24
Context=Emblems
Type=Fixed

[24x24/mimetypes]
Size=24
Context=MimeTypes
Type=Fixed

[24x24/places]
Size=24
Context=Places
Type=Fixed

[24x24/status]
Size=24
Context=Status
Type=Fixed

[32x32/emotes]
Size=32
Context=Stock
Type=Fixed

[32x32/stock]
Size=32
Context=Stock
Type=Fixed

[32x32/actions]
Size=32
Context=Actions
Type=Fixed

[32x32/apps]
Size=32
Context=Applications
Type=Fixed

[32x32/status]
Size=32
Context=Status
Type=Fixed

[32x32/categories]
Size=32
Context=Categories
Type=Fixed

[32x32/devices]
Size=32
Context=Devices
Type=Fixed

[32x32/emblems]
Size=32
Context=Emblems
Type=Fixed

[32x32/mimetypes]
Size=32
Context=MimeTypes
Type=Fixed

[32x32/places]
Size=32
Context=Places
Type=Fixed

[32x32/status]
Size=32
Context=Status
Type=Fixed

[48x48/actions]
Size=48
Context=Actions
Type=Fixed

[48x48/stock]
Size=48
Context=Stock
Type=Fixed

[48x48/apps]
Size=48
Context=Applications
Type=Fixed

[48x48/categories]
Size=48
Context=Categories
Type=Fixed

[48x48/devices]
Size=48
Context=Devices
Type=Fixed

[48x48/emblems]
Size=48
Context=Emblems
Type=Fixed

[48x48/emotes]
Size=48
Context=Emotes
Type=Fixed

[48x48/mimetypes]
Size=48
Context=MimeTypes
Type=Fixed

[48x48/places]
Size=48
Context=Places
Type=Fixed

[48x48/status]
Size=48
Context=Status
Type=Fixed

[72x72/actions]
Size=72
Context=Actions
Type=Fixed

[72x72/stock]
Size=72
Context=Stock
Type=Fixed

[72x72/apps]
Size=72
Context=Applications
Type=Fixed

[72x72/categories]
Size=72
Context=Categories
Type=Fixed

[72x72/devices]
Size=72
Context=Devices
Type=Fixed

[72x72/emblems]
Size=72
Context=Emblems
Type=Fixed

[72x72/emotes]
Size=72
Context=Emotes
Type=Fixed

[72x72/mimetypes]
Size=72
Context=MimeTypes
Type=Fixed

[72x72/places]
Size=72
Context=Places
Type=Fixed

[72x72/status]
Size=72
Context=Status
Type=Fixed

[128x128/actions]
Size=128
Context=Actions
Type=Fixed

[128x128/apps]
Size=128
Context=Applications
Type=Fixed

[128x128/categories]
Size=128
Context=Categories
Type=Fixed

[128x128/devices]
Size=128
Context=Devices
Type=Fixed

[128x128/emblems]
Size=128
Context=Emblems
Type=Fixed

[128x128/emotes]
Size=128
Context=Emotes
Type=Fixed

[128x128/mimetypes]
Size=128
Context=MimeTypes
Type=Fixed

[128x128/places]
Size=128
Context=Places
Type=Fixed

[128x128/status]
Size=128
Context=Status
Type=Fixed

[128x128/stock]
Size=128
Context=Stock
Type=Fixed
```

check out the difference from the screenshots 
snapshot4.png is before the hack and snapshot3.png is after the hack

---

### Post by Minsky on 2010-05-29
Dumblebee, thank you for replying so quickly, I've tried the hack and it has worked a treat. I've been experimenting since I last posted and discovered the same effect can also be accomplished if you substitute a larger icon into the 48x48 Places folder, but yours is the more elegant solution. I've still got a problem that's puzzling me, if you change the icon image via the Properties dialogue, for example changing the Documents folder icon in the Home directory to a custom image, the icon reverts back to the 48x48 size. I have no idea why this is happening, I've tried altering the icon sizes in index.theme, as well as placing larger icons in the Places folder but I'm not having any joy. Any ideas why this is happening would be well appreciated but in any case thanks for supplying a copy of your index.theme and for helping me out.

---

### Post by dumblebee100 on 2010-05-30
why don't you send me your index.theme file so that I can look into it and feel your use case 

do you want something like this 
having a larger icon like 128x128 icon just for one folder and remaining with 72x72 for zoom level 100% 

tell me that if the custom image is which size 

as far as my understanding 
I have selected other image which is 128x128 for the 72x72 icon ...the image resize as like 48x48 ...I guess its because the 128x128 icon is not able to fit in the icon grid provided for 100% zoom level 

and other thing ..when I selected a 32x32 image for the same folder then the image actually gets blurred and the theme is trying to show the icon as like other icons ..I mean 72x72 

when we are selecting any custom image then the theme is trying to fit the icon into the grid perfectly I mean to look as 48x48 and the custom image is changing its size only if we increase the zoom level ...a 24x24 icon gets blurred at higher zoom levels and 72x72 or 128x128 remains better at higher zoom levels ....so size of the image is least interested in our case .....all that matters is the default size of custom image is set to the zoom level of the nautilus 

it means if you select any custom image of any size then the theme is resizing the image for 100% zoom level that means 48x48

why dont you try svg images ..as they can fit into any zoom levels ..I guess Im out of options ...but its late night for me here ..so I will work on it some other time when I have free time

---

### Post by Minsky on 2010-05-31
Hi Dumblebee, here is my index.theme:-

```

[Icon Theme]
Name=hydroxygen
Comment=The most complete and self-customizable iconset ever made.
Inherits=gnome, hicolor
Example=x-directory-normal

Directories=16x16/emotes,16x16/actions,16x16/apps,16x16/categories,16x16/devices,16x16/devices,16x16/emblems,16x16/mimetypes,16x16/places,16x16/status,22x22/emotes,22x22/actions,22x22/apps,22x22/categories,22x22/devices,22x22/devices,22x22/emblems,22x22/mimetypes,22x22/places,22x22/status,24x24/emotes,24x24/actions,24x24/apps,24x24/categories,24x24/devices,24x24/devices,24x24/emblems,24x24/mimetypes,24x24/places,24x24/status,32x32/emotes,32x32/actions,32x32/apps,32x32/categories,32x32/devices,32x32/devices,32x32/emblems,32x32/mimetypes,32x32/places,32x32/status,48x48/emotes,48x48/actions,48x48/apps,48x48/categories,48x48/devices,48x48/devices,48x48/emblems,48x48/mimetypes,72x72/places,48x48/status,128x128/emotes,128x128/actions,128x128/apps,128x128/categories,128x128/devices,128x128/devices,128x128/emblems,128x128/mimetypes,128x128/places,128x128/status,72x72/emotes,72x72/actions,72x72/apps,72x72/categories,72x72/devices,72x72/emblems,72x72/mimetypes,72x72/places,72x72/status,16x16/stock,22x22/stock,24x24/stock,32x32/stock,48x48/stock,72x72/stock,128x128/stock

[16x16/emotes]
Size=16
Context=Stock
Type=Fixed

[16x16/stock]
Size=16
Context=Stock
Type=Fixed

[16x16/actions]
Size=16
Context=Actions
Type=Fixed

[16x16/apps]
Size=16
Context=Applications
Type=Fixed

[16x16/categories]
Size=16
Context=Categories
Type=Fixed

[16x16/devices]
Size=16
Context=Devices
Type=Fixed

[16x16/emblems]
Size=16
Context=Emblems
Type=Fixed

[16x16/mimetypes]
Size=16
Context=MimeTypes
Type=Fixed

[16x16/places]
Size=16
Context=Places
Type=Fixed

[16x16/status]
Size=16
Context=Status
Type=Fixed

[22x22/emotes]
Size=22
Context=Stock
Type=Fixed

[22x22/stock]
Size=22
Context=Stock
Type=Fixed

[22x22/actions]
Size=22
Context=Actions
Type=Fixed

[22x22/apps]
Size=22
Context=Applications
Type=Fixed

[22x22/categories]
Size=22
Context=Categories
Type=Fixed

[22x22/devices]
Size=22
Context=Devices
Type=Fixed

[22x22/emblems]
Size=22
Context=Emblems
Type=Fixed

[22x22/mimetypes]
Size=22
Context=MimeTypes
Type=Fixed

[22x22/places]
Size=22
Context=Places
Type=Fixed

[22x22/status]
Size=22
Context=Status
Type=Fixed

[24x24/emotes]
Size=22
Context=Stock
Type=Fixed

[24x24/stock]
Size=24
Context=Stock
Type=Fixed

[24x24/actions]
Size=24
Context=Actions
Type=Fixed

[24x24/apps]
Size=24
Context=Applications
Type=Fixed

[24x24/categories]
Size=24
Context=Categories
Type=Fixed

[24x24/devices]
Size=24
Context=Devices
Type=Fixed

[24x24/emblems]
Size=24
Context=Emblems
Type=Fixed

[24x24/mimetypes]
Size=24
Context=MimeTypes
Type=Fixed

[24x24/places]
Size=24
Context=Places
Type=Fixed

[24x24/status]
Size=24
Context=Status
Type=Fixed

[32x32/emotes]
Size=22
Context=Stock
Type=Fixed

[32x32/stock]
Size=32
Context=Stock
Type=Fixed

[32x32/actions]
Size=32
Context=Actions
Type=Fixed

[32x32/apps]
Size=32
Context=Applications
Type=Fixed

[32x32/status]
Size=32
Context=Status
Type=Fixed

Size=32
Context=Status
Type=Fixed

[32x32/categories]
Size=32
Context=Categories
Type=Fixed

[32x32/devices]
Size=32
Context=Devices
Type=Fixed

[32x32/emblems]
Size=32
Context=Emblems
Type=Fixed

[32x32/mimetypes]
Size=32
Context=MimeTypes
Type=Fixed

[32x32/places]
Size=32
Context=Places
Type=Fixed

[48x48/actions]
Size=48
Context=Actions
Type=Fixed

[48x48/stock]
Size=48
Context=Stock
Type=Fixed

[48x48/apps]
Size=48
Context=Applications
Type=Fixed

[48x48/categories]
Size=48
Context=Categories
Type=Fixed

[48x48/devices]
Size=48
Context=Devices
Type=Fixed

[48x48/emblems]
Size=48
Context=Emblems
Type=Fixed

[48x48/emotes]
Size=48
Context=Emotes
Type=Fixed

[48x48/mimetypes]
Size=48
Context=MimeTypes
Type=Fixed

[48x48/places]
Size=72
Context=Places
Type=Fixed

[48x48/status]
Size=48
Context=Status
Type=Fixed

[72x72/actions]
Size=72
Context=Actions
Type=Fixed

[72x72/stock]
Size=72
Context=Stock
Type=Fixed

[72x72/apps]
Size=72
Context=Applications
Type=Fixed

[72x72/categories]
Size=72
Context=Categories
Type=Fixed

[72x72/devices]
Size=72
Context=Devices
Type=Fixed

[72x72/emblems]
Size=72
Context=Emblems
Type=Fixed

[72x72/emotes]
Size=72
Context=Emotes
Type=Fixed

[72x72/mimetypes]
Size=72
Context=MimeTypes
Type=Fixed

[72x72/places]
Size=72
Context=Places
Type=Fixed

[72x72/status]
Size=72
Context=Status
Type=Fixed

[128x128/actions]
Size=128
Context=Actions
Type=Fixed

[128x128/apps]
Size=128
Context=Applications
Type=Fixed

[128x128/categories]
Size=128
Context=Categories
Type=Fixed

[128x128/devices]
Size=128
Context=Devices
Type=Fixed

[128x128/emblems]
Size=128
Context=Emblems
Type=Fixed

[128x128/emotes]
Size=128
Context=Emotes
Type=Fixed

[128x128/mimetypes]
Size=128
Context=MimeTypes
Type=Fixed

[128x128/places]
Size=128
Context=Places
Type=Fixed

[128x128/status]
Size=128
Context=Status
Type=Fixed

[128x128/stock]
Size=128
Context=Stock
Type=Fixed

[Desktop Entry]
Name[en_GB]=index.theme
```

I've altered the 48x48 settings in each category to 72x72 and I've also experimented with using svg images for the icons but with no success, the icons just revert back to the 48x48 size. Like you said, the Properties window could be resizing the images to the standard 48x48 size to fit the grid for the 100% view and I can't see a way around this. If you have any luck, please let me know. Many thanks.

---

### Post by Minsky on 2010-06-01
I've found a workaround that solves my problem Dumblebee. As I've discovered, replacing a folder icon with a custom image automatically resizes the icon to suit the zoom level associated with the current directory. One method to get around this, after applying the custom image to the icon, is to highlight the icon and go to Edit>Stretch Icon... and resize the icon manually. Not an entirely elegant solution as you have to resize each custom icon individually but it works. Please let me know if you can come up with a better solution and thanks for helping me achieve what I wanted.

---

### Post by bumdictator on 2010-09-21
I found out how to change ur Desktop Icon Size... if ur using 10.04 just right click on ur icon - "Resize Icon"
:)

---

