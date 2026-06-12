---
title: "GDM2 not changing login screen Ubuntu Lucid 10.04 (64-bit)"
date: 2010-06-27
forum: Desktop Environments
---

### Post by Meharisian on 2010-06-27
After 2 days of trying, failing, trying, and failing again... installing  gdm2 and still not having any luck with changing the wallpaper on the login screen on my computer (see below for specs)... I have now,  FINALLY, been able to use the login screen I want! :D Hope this is useful for those newbies like me struggling with this problem...

Here's how I did it (with some help from different threads on these  forums that are all over the place, non seeming to have complete answers)... if anyone knows a better way  please let me know, and for the benefit of others (I'm not as much a seasoned user, yet)...

First (thanks to philinux for sharing this [here]("http://swiss.ubuntuforums.org/showpost.php?p=9352873&postcount=3")), make sure you have gdm2 installed, you can do this by entering  this code in terminal (Applications > Accessories >  Terminal), _**make sure you do it one line at a time**_:[INDENT]sudo add-apt-repository ppa:gdm2setup/gdm2setup
 sudo apt-get update
 sudo apt-get install python-gdm2setup
[/INDENT]Then, you can run GDM2 from **System > Administration > Login (GDM2Setup)**


However, this is where my problem started... when I went into the **Wallpaper** tab and tried to select a wallpaper, it would not let me change it and sometimes the window that opened allowing me to choose from images in my system would just be blank...
...somewhere on the forums (sorry, forgot where), someone said to run GDM2 by using the below code in Terminal:[INDENT]gksu gdm2setup

[/INDENT]This didn't help at first, but I noticed in terminal it showed an error saying that the below directory doesn't exist:[INDENT]usr/share/images/xsplash/bg.jpg

[/INDENT]I browsed to that location in my filesystem but couldn't make any changes or add the folder, I found the images folder but there was no xsplash folder in there... to be able to create this folder you need to put the below code into the Terminal:[INDENT]gksu nautilus

[/INDENT]For newbies please note: This (running things as 'gksu' instead of using the 'sudo' command is NOT RECOMMENDED usually, running anything 'gksu' and making a mistake can cause problems in your system so please be careful however you shouldn't encounter problems if you follow these instructions to the letter.



Now, after you typed in the above **gksu nautilus**, a file browser window will open, if you now browse to the **usr/share/images/** directory and right click on the blank space in the folder window, it would now allow you to create folders or copy files. You need to create the folder called **xsplash** in this images folder.


Once you have done this, do not close this window, browse inside this same window to the location where you have saved the image you want as the background image and copy it, browse back to the usr/share/images/ folder and paste this image in the xsplash folder you created.


Rename your image to 'bg.jpg' (you need to ensure it is in jpg format for this to work, by the way).


Close your file browser and terminal... reboot or log off to log back in again and it should be working! :)


- **Meharisian**

*"Waste no more time arguing what a good man should be, be one." - Marcus Aurelius*


**My PC Specs:**
Intel i5 750 Quad Core 2.66 GHz
3 GB DDR3 RAM
1 TB HDD dual boot 45% Windows 7 and 45% Ubuntu 10.04 Lucid 64-bit (rest 10% misc storage + swap)

---

