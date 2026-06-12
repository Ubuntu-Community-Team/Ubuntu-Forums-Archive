---
title: "Icons vanish in desktop widget"
date: 2010-10-16
forum: Desktop Environments
---

### Post by simon.robert on 2010-10-16
Hi, I have done a clean install of 10.10 and then restored all settings and data from backup.

In the desktop display widget all the applications I have are still there, but for some of them, thunderbird, googleearth, the icon is not displayed except breifly when the app is mouse clicked.

I have tried reselecting the icon, deleting the link and re making it, but with no results.

The only thing that works is selecting an icon for a different app and using that. If I do this the icon remains in view. Doing this and then switching back to the original icon does not work.

Any ideas please
   Simon

---

### Post by kio_http on 2010-10-16
Screenshots please as I don't quite understand what you meen by disappearing icons.

---

### Post by simon.robert on 2010-10-16
as you can see from the screen shot the desktop widget has the places for the applications and the text, if you hover over were the icon should be the box will hightlight and the description will appear.

Thunderbird and googleearth apear blank, calibre shows as a question mark. On all three when I click to run them the proper icon is visible very breifly.

Simon

---

### Post by simon.robert on 2010-10-16
you can see in this one that the box is highlighted, behaviour is normal except no icon!

---

### Post by kio_http on 2010-10-16
Try removing the icons. And in the Kickoff launcher (start menu) right click on the items e.g googleearth and click add to desktop.

---

### Post by kio_http on 2010-10-16
Which version of KDE's settings have you backed up. i.e Which version of KDE were you running on your previous release of Kubuntu?

I'm guessing the present one is KDEv 4.5.1 on Kubuntu 10.10?

---

### Post by simon.robert on 2010-10-16
I have tried deleting the app from the desktop widget and setting it up again.

If I go to the app on the menu and right click the only option is "add to favourites". What is the "kickoff launcher"?

The kde versions are whatever it was for 10.04 and then whatever it is for 10.10.

---

### Post by kio_http on 2010-10-16
You know, KDE in 10.04 was v 4.4.2 and in 10.10 it is v. 4.5.1.

The way they save configuration files is different. For this reason, I would suggest you reset KDE to default settings by deleting its configuration folder.

To do this:
Open Konsole

Type:
```
rm -rf .kde
```
press enter

Then

Logout and Login

Or

Press ALT + F2
Type
```
kquitapp plasma-desktop
```
Enter
Then again ALT + F2
```
plasma-desktop
```

After this you will have to readjust KDE settings you changed like desktop composition, wallpaper etc.
Other files such as documents, desktop contents etc will stay.

---

### Post by simon.robert on 2010-10-16
removing the kde config files will delete a lot of things I want to keep. If this is some sort of mismatch between kde versions why do most of the icons work? Also why does everything else held in the .kde files work if there is some sort of incompatibility?

If there is some way of removing the desktop widget settings I'm OK to do that. Removing .kde deletes many things.

And yes, I do know how to do a rm -rf thank you. I am after helpful sugestions, rather than "nuke the entire system and then set it up again".

Thanks
  Simon

---

### Post by kio_http on 2010-10-17
> **simon.robert said:**
> removing the kde config files will delete a lot of things I want to keep. If this is some sort of mismatch between kde versions why do most of the icons work? Also why does everything else held in the .kde files work if there is some sort of incompatibility?

If there is some way of removing the desktop widget settings I'm OK to do that. Removing .kde deletes many things.

And yes, I do know how to do a rm -rf thank you. I am after helpful sugestions, rather than "nuke the entire system and then set it up again".

Thanks
  Simon

Right.

One issue can be icon cache has been broken.
Second issue can be the directory where the icon of those applications has changed or the icon filename has changed.

And yes there is a way to remove only desktop widget settings, I will tell you the config file for that later when I boot Kubuntu. I am on OS X now unfortunately. 

Try closing the desktop folder plasmoid, switching to folder view desktop settings and the switching back to default desktop containment settings. 

(Right click on Desktop Configure Desktop) I think.

---

### Post by simon.robert on 2010-10-18
just tried switching to folder view and back, but no difference.

Don't think it is links as the icons do show up when the app is activated and do work if replaced by a different icon.

Simon

---

### Post by kio_http on 2010-10-19
> **simon.robert said:**
> just tried switching to folder view and back, but no difference.

Don't think it is links as the icons do show up when the app is activated and do work if replaced by a different icon.

Simon

The files concerning KDE Plasmoids/Widget settings are

1. /home/USERNAME/.kde/share/config/plasma-appletsrc
2. /home/USERNAME/.kde/share/config/plasma-desktop-appletsrc
3. /home/USERNAME/.kde/share/config/plasma-desktoprc

Like I had the strange issue of my screen becoming full of lines on logon after an upgrade and the solution was to delete .kde and start fresh. Since I did not have many settings changed (just wallpaper and themes, I did this [OperaLink saves bookmarks]) Also the KDE team does improve performance sometimes with default setting changes.

---

