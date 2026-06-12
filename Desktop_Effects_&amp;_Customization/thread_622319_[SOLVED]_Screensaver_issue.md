---
title: "[SOLVED] Screensaver issue"
date: 2007-11-24
forum: Desktop Effects &amp; Customization
---

### Post by Cariboo1938 on 2007-11-24
Hi all.
I have installed Xscreensaver and I used 'My Pictures' as Screensaver theme in the /home/owner directory.
I moved the 'My Pictures' to the free directory ( /Misc which is actually a free partition) and now the screensaver does not find the Pictures anymore.
How can I configure or enter the new location of Pictures so that they can be found again?

---

### Post by Cariboo1938 on 2007-11-25
Issue solved!:)

I found this [HOWTO]("http://ubuntuforums.org/showthread.php?t=230576"): Change the destination folder of 'Pictures Folder' for Screensaver (Feisty)

In gnome 2.0 there is a screensaver call for "Pictures folder".
To use this screensaver you have to have a folder named "Pictures" in your /home directory. 
The screensaver will slideshow all pictures in this folder.

To change the folder destination of this screensaver open terminal and type command:
 
```
sudo gedit /usr/share/gnome-screensaver/themes/personal-slideshow.desktop
```

---> Go to line 95 (Exec=slideshow --location=Pictures)

---> Change the name of the destination folder by replacing <Pictures> with what ever you want, for example: 

> /usr/share/pixmaps or /media/win_d/blabla or in my case  /Misc/Pictures 

exit file 'personal-slideshow.desktop'
done

Case closed!:)

---

### Post by Cariboo1938 on 2007-11-25
Issue solved!:)

I found this [HOWTO]("http://ubuntuforums.org/showthread.php?t=230576"): Change the destination folder of 'Pictures Folder' for Screensaver (Feisty)

In gnome 2.0 there is a screensaver call for "Pictures folder".
To use this screensaver you have to have a folder named "Pictures" in your /home directory. 
The screensaver will slideshow all pictures in this folder.

To change the folder destination of this screensaver open terminal and type command:
 
```
sudo gedit /usr/share/gnome-screensaver/themes/personal-slideshow.desktop
```

---> Go to line 95 (Exec=slideshow --location=Pictures)

---> Change the name of the destination folder by replacing <Pictures> with what ever you want, for example: 

> /usr/share/pixmaps or /media/win_d/blabla or in my case  /Misc/Pictures 

exit file 'personal-slideshow.desktop'
done

Case closed!:)

---

