---
title: "How can I see a random picture slide show?"
date: 2006-02-01
forum: Desktop Environments
---

### Post by Laynix on 2006-02-01
Question:  What can I use to display a slide show of random pictures in subfolders?

I switched to Ubuntu from Windows recently, and a feature that I can't seem to find is a random picture slide show.  What I have in mind is the function of the picture slide show screen saver that is in Windows XP.  I want to be able to display pictures that are in subfolders, which are in a main folder (/pictures/dates).  I know that the gThumb Image Viewer displays pictures in a slide show, but they are displayed in order and only from one folder.  I use Gnome.

---

### Post by Dragonbite on 2006-02-01
In the basic Ubuntu install you'll find ```
Application>Graphics>gThumb Image Viewer
```which is relatively lightweight and incorporates slideshow capabilities.

For additional editing possibilities you can look into F-Spot or digikam (for KDE).

---

### Post by matthew on 2006-02-01
[quote=Laynix]What I have in mind is the function of the picture slide show screen saver that is in Windows XP.[/quote]If you just want a screensaver that does this there is one already on your computer. 

--Put the pictures you want to see in a specific folder (i.e. /home/username/slideshow ) and then go to your menu.
--System->Preferences->Screensaver
--scroll down the list and choose the screensaver called GLSlideshow
--then choose the Advanced tab. 
--under Image Manipulation select Choose Random Image and enter the location of the folder you created earlier

Have fun!

---

### Post by Laynix on 2006-02-01
Haha, thank you matthew.  That is all I really wanted, I just didn't realize it was called GLSlideshow.

---

### Post by matthew on 2006-02-01
[quote=Laynix]Haha, thank you matthew. That is all I really wanted, I just didn't realize it was called GLSlideshow.[/quote]I kinda thought so. Enjoy!

---

### Post by daryl256 on 2006-05-09
I'm using Dapper, and it does not seem to have an Advanced Tab in Screensaver.  How do we do this with Dapper?

Thanks,

Daryl

---

### Post by ComplexNumber on 2006-05-09
[quote=daryl256]I'm using Dapper, and it does not seem to have an Advanced Tab in Screensaver.  How do we do this with Dapper?

Thanks,

Daryl[/quote] gqview does. go to preferences in the menu. i think its the 1st or 2nd tab that gives you options to dictate the slideshow order (eg randow, after X amount of seconds, etc)

---

### Post by cripou on 2006-07-18
there's no menu in the screensaver window in Dapper... the only "menu" i see is the list of screensavers... do you have anythong else to try?

---

### Post by shane2peru on 2006-07-21
I have the same problem, using Dapper.  Does anyone know how to configure this??  Why did they change it from Breezy to Dapper???  That is not an upgrade that is a downgrade!?!

Shane

---

### Post by shane2peru on 2006-07-21
ok, found the answer.  Check this post:  [here.]("http://ubuntuforums.org/showthread.php?t=189807&highlight=slow+screensaver")  You will need to uninstall gnome-screensaver as this does not allow configuration, and then set xscreensaver as the screensaver program.

Shane

---

