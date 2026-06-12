---
title: "Change the Ubuntu menu icon"
date: 2007-08-23
forum: Desktop Effects &amp; Customization
---

### Post by Godmanliving on 2007-08-23
After looking through the similar posts, I have none to be helpful in assisting me with changing my Ubuntu Menu icon to the one included in my Wii Theme download.  Anyone assist me with changing the icon right next to the applications or the one that is the full menu to the icon i have?  Its in a svg format.

---

### Post by arist0tle on 2007-08-23
Go to System tools and open up the configuration editor. Then go to Apps->panel->objects. Its one of the objects (object_0, object_1, etc.)...it varies. Click the "use_custom_icon" checkbox then go up to "custom_icon". Right click "custom_icon" and the then click "edit key". enter the path of the icon that you want to use. Hope this helps.

---

### Post by Godmanliving on 2007-08-23
Alright so everyone here has the right to shoot me.  I have read that same thing three other times but i was making it more difficult and not understanding that object_zero was a single object with the custom icon button in it. I thought each of the fields in object zero represented an object and was trying to change the wrong one.   Thank you for your help.

---

### Post by Godmanliving on 2007-08-23
Odd but it didn't save my settings.  Any ideas?  Everytime I log in ive been getting an error something along the lines of $home/something cannont have something about permissions and its inability to save sessions. Would that possibly be a cause or am i missing something again?

---

### Post by arist0tle on 2007-08-24
don't worry about making things more complicated than they are...that's like my motto or something, lol!!! But it works most of the time being a CS student and all. Anyway, did you change anything else while you were in the configuration editor. i am guessing that you accidently changed the permissions of your home folder (/home/your_name). Check that (push Ctrl-L,  enter /home and right click on your folder and go to permissions... sorry if you know this stuff already). Peace

---

### Post by arist0tle on 2007-08-24
properties->permissions that is :)

---

### Post by BLTicklemonster on 2007-08-31
I can't find a configuration editor in gutsy tribe 4

---

### Post by the architect on 2007-09-03
I've had a lot of trouble with this one too...
The simple way to do this without changing any system settings is: 
First you have to create home/username/.icons/iconthemename/scalable/places
Place your custom icon in that folder and rename it to: gnome-main-menu.svg

Then you have to edit your index.theme: 
sudo gedit ~/.icons/iconthemename/index.theme

If you're using a system icon theme:
sudo gedit /usr/share/icons/iconthemename/index.theme

Add ",scalable/places" to the end of the line "Directories=scalable/apps,scalable/filesystems,scalable/mimetypes,scalable/devices,scalable/emblems,scalable/stock"

and finally at the very end of the file add:

[scalable/places]
MinSize=1
Size=48
MaxSize=128
Context=Places
Type=scalable

Then press alt+F2 and enter "killall gnome-panel", or restart.

Hope this helps

---

