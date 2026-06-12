---
title: "How to add more apps into the Unity Launcher"
date: 2015-04-20
forum: Desktop Environments
---

### Post by flaymond on 2015-04-20
Hello guys, I decided to add 2 DE in my PC, well my choice is Unity and XFCE because both are elegant and fast (thanks to minimal Unity, no bloat softwares :D). Well I think I will stick with Unity since I need to access app very easily, and the Launcher is the thing I want. Well my question is, is there anyway I can add applications into the launcher without run-and-lock it? By that, using configuration settings like .desktop(in this case, it's the launcher). Thanks for help!


* Another question : I don't understand, if flavors other than Ubuntu use the same base of ubuntu, then why, they only supported for 3 years?

** More question: I can't open trash in Unity launcher, but in file manager...it's working. The errors is - Error when getting information for file '/home/user/trash': No such file or directory. It's also output 'Failed to execute default file manager'. Is this something wrong with default application? The settings is brought from Xubuntu session, and the preffered file manager is pcmanfm. How can I access the trash icon in the launcher?

---

### Post by dino99 on 2015-04-20
> **InterProg said:**
> I don't understand, if flavors other than Ubuntu use the same base of ubuntu, then why, they only supported for 3 years?

Because Time has no 'stop' button, and changes/upgrades are done again & again, old releases cant be maintained past the designed version life. Other ubuntu flavors are either 'old' mimics (ubuntu-mate based on gnome2) or lightweighted version (Lubuntu) or based on other DE (xubuntu (xfce) /kubuntu (kde)/...)

---

### Post by deadflowr on 2015-04-20
You should still be able to drag n drop launchers from the dash menu to the launcher.
You just can't drag and drop from the dash to the desktop area, anymore.
D'n'd from the dash can be done without ever running the app.

---

### Post by flaymond on 2015-04-20
[QUOTE=deadflowr]D'n'd from the dash can be done without ever running the app.[/QUOTE]

Can I drag it from file manager? Dash is the main feature I hate.

---

### Post by deadflowr on 2015-04-21
> **InterProg said:**
> Can I drag it from file manager? Dash is the main feature I hate.

Don't remember about trusty, but you can in vivid and precise.
i see no reason it won't work in trusty.
Simply go to /usr/share/applications or where ever else you have .desktop launcher files and drag it to the launcher.
A space will/should open where you try adding the launcher. Drop it into the opened up space.

---

### Post by flaymond on 2015-04-21
Thanks it's working! :D

* I tried find /usr/share/applications/program.desktop using file manager, but it doesn't work somehow.
* I tried other alternative by locating .desktop file using ```
 locate firefox
```.
* It ping me the location of the firefox.desktop
* I cd to the directory using terminal
* and open file manager with it
* Done! Just drag and drop the .desktop in there. :D

---

### Post by deadflowr on 2015-04-22
Forgot to mention that Nautilus shows the desktop items in /usr/share/applications as the launchers, as is.
So while the file would be called something like firefox.desktop, it shows simply as firefox, with the firefox icon.
The entire folder is, mostly, desktop launchers. A few exceptions, like bamf.index.
So, basically, you can drag any of the launchers from there to the launcher.

Two things about the launcher in that folder, or any .desktop file for that matter,
One, if you wanted to look at the files script/desktop entry, as it where, you need to open a text editor and either drag the file into the text window or use the text editor's Open dialog to open the file, because,
Two, clicking on the launcher will launch the app. And there would be no option for right click > open with, only open; which means run.
If that makes any sense.

---

### Post by CantankRus on 2015-04-22
If you're using the unity launcher you may as well use the dash instead of searching for desktop files in /usr/share/applications.
You don't have to use all the features of the dash.
eg I disable online search and remove most of the lens and scopes and disable suggestions.
Still useful to search for files and apps and view recent.
Notice in pic, only Home, Applications and Files lenses are shown.
In the Home lens all I see now are recently used applications and files and if you don't even 
want to see that use the privacy settings to turn off recording.

---

