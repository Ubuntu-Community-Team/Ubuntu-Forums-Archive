---
title: "Gnome menu &amp; installed games"
date: 2005-02-20
forum: Gaming &amp; Leisure
---

### Post by keyshawn on 2005-02-20
hey,
  
 I installed quite a few games [bzflag among others] via apt-get and I can't get them on the games panel in the gnome start menu. 
 Usually whenever else I installed other apps from there, I had no problems getting them into the gnome menu automatically, with no work on my part \\:D/ 
  However, this time around is a bit more difficult. 
 I'm not exactly sure what information I should post here for you to help troubleshoot, but feel free to ask, and I'll do my best to provide it :) 
  
  Thanks,
  keyshawn.
 
 PS - yes, I did do the basic log out and restart; that didn't do anything..

---

### Post by kassetra on 2005-02-20
Ok, sometimes apps don't go into the menus, so here is how you add apps to your menu:
   
 1. You need to change the permissions so that you can edit your own menus whenever you want (this is a one-time change, mostly), so first, open a terminal:
   Applications->System Tools->Terminal
   2. Type this in (substitute your usr name)
    ```
sudo chown -R username /usr/share/applications
``` 
   and press enter.
   3. Ok, let's add your applications.  Open a nautilus window:
   Computer->Home
   4. Type this in the location bar:
    ```
applications:///
``` 
   5. Double click (or single click if that is the way you have nautilus set up) on Games
   6. Right click anywhere in natilus window and then left click on "Create Launcher"
   7. Now, fill in this information:
    ```
Name: The name of the application/game, ie, "BZ Flag"
```
 ```
Command: Put in the command to run the game, 
 most likely "bzflag" but you can browse or test your theory in the terminal.
```
  ```
Icon: when you click here, it will take you into 
 /usr/share/pixmaps to locate the icon for your new launcher, 
 you can also browse all over your system to find an icon if you want.
```
   8. Click ok 
   
   Now when you open your Applications menu, you will see your new game launcher.  :)  Do the same for anything else you want in the menu that does not show up... 
   
   caveat: sometimes you'll need to log out and log back in to see your items in the menu.

---

### Post by keyshawn on 2005-02-25
Thanks for the info, I'll try that out.

This sounds like it would appear to be too frustrating for a typical desktop user..... 
:/ 

[I'm not trying to flame, Laborious tasks like the ones described above need to automated before Ubuntu and/or linux in general would become a player in the desktop world....which isn't ubuntu's goal ?!]

---

### Post by jsgotangco on 2005-02-26
well most of these "games" and other apps aren't really packaged directly for gnome, hence they don't really install those stuff on the menu (same goes for KDE btw). You will notice this especially for gnome and kde optimized games. Also, I don't think the developers of 'bzflag' or any other linux game out there would fix their install scripts for every distro on the planet. Now I'm not sure about bzflag being part of Ubuntu's official package, but if it did, then they probably didn't optimize the thing at all to have the script to install the launcher on the gnome menus.  All the stuff I installed at [www.gnomefiles.org](www.gnomefiles.org) do create launcher menus though even if they were not pre-packaged for ubuntu.

PS: Adding launcher entries in GNOME are much easier now compared to old versions.

---

### Post by Lord C on 2005-03-08
[QUOTE=kassetra]Ok, sometimes apps don't go into the menus, so here is how you add apps to your menu:
   
 1. You need to change the permissions so that you can edit your own menus whenever you want (this is a one-time change, mostly), so first, open a terminal:
   Applications->System Tools->Terminal
   2. Type this in (substitute your usr name)
    ```
sudo chown -R username /usr/share/applications
``` 
   and press enter.
   3. Ok, let's add your applications.  Open a nautilus window:
   Computer->Home
   4. Type this in the location bar:
    ```
applications:///
``` 
   5. Double click (or single click if that is the way you have nautilus set up) on Games
   6. Right click anywhere in natilus window and then left click on "Create Launcher"
   7. Now, fill in this information:
    ```
Name: The name of the application/game, ie, "BZ Flag"
```
 ```
Command: Put in the command to run the game, 
 most likely "bzflag" but you can browse or test your theory in the terminal.
```
  ```
Icon: when you click here, it will take you into 
 /usr/share/pixmaps to locate the icon for your new launcher, 
 you can also browse all over your system to find an icon if you want.
```
   8. Click ok 
   
   Now when you open your Applications menu, you will see your new game launcher.  :)  Do the same for anything else you want in the menu that does not show up... 
   
   caveat: sometimes you'll need to log out and log back in to see your items in the menu.[/QUOTE]
 I get as far as step 4, then when trying to view applications:/// I just get an error.

'applications:///' Is not a valid location.

---

### Post by Dylanby on 2005-03-09
I gave an example in this [thread](http://ubuntuforums.org/showthread.php?t=10986)  too (see post #4).

---

