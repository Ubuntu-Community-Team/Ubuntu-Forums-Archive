---
title: "Cosmos wallpaper changer"
date: 2011-10-26
forum: Desktop Environments
---

### Post by makitso on 2011-10-26
I use cosmos on my 11.04 system.  Is it available on 11.10 or from a ppa somewhere?   I use the Gnome 3 shell.

---

### Post by Rodney9 on 2011-10-27
I have not heard of or can find Cosmos Wallpaper changer, the best I've come across for gnome is DesktopNova

---

### Post by Erik1984 on 2011-10-27
> **Rodney9 said:**
> I have not heard of or can find Cosmos Wallpaper changer, the best I've come across for gnome is DesktopNova

Cosmos is not a program but a wallpaper slideshow you can set as background in 11.04.

here is the cosmos folder from 11.04: [http://ubuntuone.com/0O9Io6Cv2PDcwUOEybufAa](http://ubuntuone.com/0O9Io6Cv2PDcwUOEybufAa)

Just put this in your home and change the paths of the images in the file "background-1.xml" to their proper location. Then set that xml file as background.

---

### Post by makitso on 2011-10-27
Thanks Euroman.  Based on your comments I was able to find the article below that provided more detail on this.

[http://www.linuxjournal.com/content/create-custom-transitioning-background-your-gnome-228-desktop](http://www.linuxjournal.com/content/create-custom-transitioning-background-your-gnome-228-desktop)

However, under Gnome 3, I can't find a filter to add a .xml background that is not .jpg.  The filter option does not appear to be in 11.10.

---

### Post by makitso on 2011-10-27
Ok, I was able to get it to work under 11.10/Gnome 3.  But, it's kind of odd.

There is one folder in /usr/share/backgrounds named contest.  I copied the cosmos .xml file to this folder and then copied all the .jpg image files to /usr/share/backgrounds and changed the .xml file to point to them.

What did not work was having another folder in /usr/share/backgounds named cosmos -- apparently G3 is hardwired to only have one folder?
What did not work was having the .jpg image files in the sub folder named contest.

---

