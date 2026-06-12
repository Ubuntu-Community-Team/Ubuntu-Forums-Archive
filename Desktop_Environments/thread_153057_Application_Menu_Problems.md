---
title: "Application Menu Problems"
date: 2006-03-31
forum: Desktop Environments
---

### Post by neogeek on 2006-03-31
My Applications menu is giving me some problems. 
First, the Accessories folder became a sub-folder in the Accesbility folder. I used the Applications Menu Editor to put the Accessories folder back to the main "Applications" sub-tree but when I clicked on the Applications Menu, still the same problem. I am using SMEG 0.7.5-0ubuntu2 version.

Secondly, my "Add Applications" link is gone from the Systems Tool. Anyway to get it back?

This is not the first I have experienced the Applications Menu failed to function properly. I downloaded Kubuntu and the whole Applications Menu just disappeared. So I use ubuntu and this is happening again, although not as bad.
Is this a bug?

Would appreciate any help.

neogeek
](*,)

---

### Post by Tiede on 2006-04-06
Posting to say that I am having the exact same problem. I wanted to move some icons around in my menu because the alphabetical wasn't right for me, and  I misktakenly moved the "Sound and Video" and the "System tools" icon inside another menu item. They bacame sub-menus of this item (Games) and they won't show up in the application menu no longer. They will show up as sub-menus in any other place, but they never appear in the main menu, no matter what I try. I cannot recall which version of smeg I am using (I am not on ubuntu right now, since it [ won't let me go wireless!!!! ](http://ubuntuforums.org/showthread.php?t=147648)) but I can say that my breezy os is up-to-date with all updates! :D
Anyone knows a fix. Personally I think this is a very serious bug that slipped through. I am going to check on malone, but I cannot file a bug. (No internet for me to download a debug version of smeg since I currently only have wireless access :( )
I do hope someone else maybe able to file a bug... Thanks to anyone who does.

---

### Post by Tiede on 2006-04-06
found it! But it does not look too promising :(
[https://launchpad.net/distros/ubuntu/+source/gnome-menus/+bug/26524](https://launchpad.net/distros/ubuntu/+source/gnome-menus/+bug/26524)
Anyone got a workaround, in the mean time?

---

### Post by MJ50 on 2006-04-13
I have a similar problem.
Trying to rename a folder and application names under "Applications-->Debian"
It sorta works on its own.  Although I made correct changes, new names are applied partially. :(

---

### Post by I_Like_Pie on 2006-06-19
I have had a very similar problem along the same line.  I was customizing my application menus via Alacarte and I accidently re-named my Multimedia (Audio and Video) folder as a 'null' value...I hit escape with nothing listen in the name field.  
 
By doing this I can no longer access my Multimedia programs from the Applications bar.  I go to Add/Remove programs and I can see the 'null' with all of my programs in it, but I can no longer select, or even see, it in the Alacarte menu.
 
Does anyone know where I go to replace the 'null' value with a name so that I can actually launch my multimedia files?

---

### Post by Alfredo on 2006-06-25
It seems the only way to quickly correct the problem is to create a new entry in the main manus (Application, System, Preferences...) and configure it with the same parameters of the original "Add/Remove..." link that you can find in Alacarte.
I hope it could be helpful....

[QUOTE=neogeek]My Applications menu is giving me some problems. 
First, the Accessories folder became a sub-folder in the Accesbility folder. I used the Applications Menu Editor to put the Accessories folder back to the main "Applications" sub-tree but when I clicked on the Applications Menu, still the same problem. I am using SMEG 0.7.5-0ubuntu2 version.

Secondly, my "Add Applications" link is gone from the Systems Tool. Anyway to get it back?

This is not the first I have experienced the Applications Menu failed to function properly. I downloaded Kubuntu and the whole Applications Menu just disappeared. So I use ubuntu and this is happening again, although not as bad.
Is this a bug?

Would appreciate any help.

neogeek
](*,)[/QUOTE]

---

### Post by readingboy on 2006-07-27
You might want to try renaming the directory ~/.local/share/applications. That will set all of your menu items back to their defaults before you changed them with Alacarte. 

FYI, The desktop files here represent the changes in the menu items you made with Alacarte. They supercede the master desktop files in /usr/share/applications and /usr/share/gnome/apps. 

Hope this helps.

---

