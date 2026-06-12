---
title: "Xubuntu - How to remove Wine menu items"
date: 2006-07-28
forum: Desktop Environments
---

### Post by douga on 2006-07-28
This is a small but annoying problem. I installed some software under Wine, then later ran the uninstaller. However, the menu items for the uninstalled software don't ever seem to go away. They're in a file under my ~/.cache directory that just reappears no matter what I do.

On a related note, the "Other" menu on my desktop menu and on the "Applications" menu seems to have grown to take in every app that's installed. 

Any help in fixing these things would be appreciated.

Thanks.

---

### Post by foxy123 on 2006-07-28
I guess they are in ~/.gnome/apps/Wine Remove desktop files from there and it should be fine.

---

### Post by douga on 2006-07-28
> **foxy123 said:**
> I guess they are in ~/.gnome/apps/Wine Remove desktop files from there and it should be fine.

Thanks. Removing them from there and the files in ~/.cache/xfce4/desktop did the trick.

---

### Post by christina_svats on 2007-09-09
I have the same problem, I have deleted everything that has "wine" in it, but I can't remove it from the menu. 
I can't find this Wine file you are talking about under gnome/apps
Could anybody help?

---

### Post by manicnerd on 2007-09-13
> **christina_svats said:**
> I have the same problem, I have deleted everything that has "wine" in it, but I can't remove it from the menu. 
I can't find this Wine file you are talking about under gnome/apps
Could anybody help?

same deal here....there is no ~/.gnome folder......only ~/.gnome2 or ~/.gnome2_private -- neither have an app folder in them

**EDITED**
i think i found a way to get rid of those entries....

i had a folder located at ~/.local/share/applications/wine/Programs

in the Programs folder were other folders that contained *.desktop files that if i deleted, then they werent in the OTHER folder under the menu....

sorry if this doesnt make sense i'm tired

---

### Post by laxters on 2007-09-19
errrr sry but im really new to ubuntu, can someone plz tell me the steps to remove the wine menus?? thnc

---

### Post by etharis on 2007-12-01
/home/<username>/.local/share/applications/wine/Programs

If you click on places >> home folder

that will open up a browser window of your home directory. Press <Ctrl> + h and that will show all hidden files, look for a folder named .local and you should be able to delete the icons from there.

---

### Post by Jammerdelray on 2007-12-01
What a lifesaver, I was ready to reinstall Ubuntu.

---

### Post by santiagoward2000 on 2007-12-02
> **Jammerdelray said:**
> What a lifesaver, I was ready to reinstall Ubuntu.

Just because of some unnecessary launchers in you Applications menu? Isn't that a little drastic?

---

### Post by Cursim on 2007-12-02
You cab also right-click the xfce button and go to edit menu. Expand whatever submenu the offending apps are under, and right click, delete. I nuked the whole menu and built it all back up the way I wanted using this handly little config utility.

---

### Post by seanc7 on 2007-12-09
Perfect. I just switched to Xubuntu today and this was really bugging me.

It solved it for me, no problems.

---

### Post by bharadwaj on 2007-12-10
you can even edit the main menu items from system->prefrences
though this wouldnt fix the probe permanently like the one told by foxy 123 but it certainly works;)

---

### Post by LunarWolf on 2007-12-18
> **etharis said:**
> /home/<username>/.local/share/applications/wine/Programs

If you click on places >> home folder

that will open up a browser window of your home directory. Press <Ctrl> + h and that will show all hidden files, look for a folder named .local and you should be able to delete the icons from there.

Man Thank you for a forward answer in regards to the lingering menus of uninstalled wine apps (windows based software).

---

### Post by Victormd on 2008-01-14
Thanks, was already driving me crazy and I was getting ready to start a thread! :)

---

### Post by mattyboy11 on 2008-01-31
cheers it worked fine

---

### Post by oprime15 on 2008-02-14
> **etharis said:**
> /home/<username>/.local/share/applications/wine/Programs

If you click on places >> home folder

that will open up a browser window of your home directory. Press <Ctrl> + h and that will show all hidden files, look for a folder named .local and you should be able to delete the icons from there.

This seemed to work fine for me. 

I was having one hell of a time because I could not: "*(Right click) Applications> Edit menus> (select item in right pane) (Right click) delete or press delete*. " And I tried "*System> Preferences> Main Menu> (select item in right pane) (Right click) delete or press delete*."

Neither of those seemed to work. Maybe a bug or something. 

Now I'm having another issue. 

I removed Wine which was removed fine without hitch, The menu items for the installed programs in wine lingered but were removed following the quoted text above to remove them. Now when I re-install Wine I cannot get the nice wine menu under applications...

I'll find a picture...

Here we go... I want to reinstall Wine and get this back in my menu:
[[IMG]http://img212.imageshack.us/img212/2121/89246046ka1.th.png[/IMG]](http://img212.imageshack.us/my.php?image=89246046ka1.png)

Minus the utorrent icon of course. Just the menu: *"Applications> Wine> Programs / Browse C:/ Drive / Configure Wine / Uninstall Wine Software"*

I tried using the synaptic packet manager to completely remove the program and all traces and re-installing it but I still can't get that nice menu back. All I get in the menu following a reinstall is 

Browse C:/ Drive
Configure Wine
Notepad
Uninstall Wine Software

All lumped into my "Other" menu, and when I try to move them in the Edit Menus, all I see is a single program icon called Wine Windows Emulator...

Dammit. Now going back into "*Applications> Other*" they all just disappeared. 

I just removed wine completely for the fourth or fifth time.

Anyone know what is going on here?

---

### Post by oprime15 on 2008-02-25
Bump

Still need some help.

---

### Post by chlee on 2008-02-27
i was playing with wine32 to play a game. didnt work so well.. oh well, no biggie. i uninstall wine32, but the menu stays! and the game was still listed. hmmmm..  so, on to .gnome and i find nothing about wine or the game. okay, so on to .local and there it was! the menu was gone! hurray! 

from reading this thread i also learned i can play with the wine menu in main menu. cool.. didnt even check for that. i look and guess what i see..? wine and the game! all i had done was remove it from the displayed side the hard way. 

so the point here is, "thats messed up!"
:P

side note: i have wine64 installed now, because.. why not? it works smooth as butter.  the menu inluded browse drive, config, and uninstall apps.. like someone asked about above. but guess whats still hangin out ..? any ideas?


as far the quote below, ive had the problem once before .. where the menu item would move around in the applications list. some time in other, so times in games.. etc. i just restarted and it just started working correcty. beats me.


:P





> **oprime15 said:**
> This seemed to work fine for me. 

I was having one hell of a time because I could not: "*(Right click) Applications> Edit menus> (select item in right pane) (Right click) delete or press delete*. " And I tried "*System> Preferences> Main Menu> (select item in right pane) (Right click) delete or press delete*."

Neither of those seemed to work. Maybe a bug or something. 

Now I'm having another issue. 

I removed Wine which was removed fine without hitch, The menu items for the installed programs in wine lingered but were removed following the quoted text above to remove them. Now when I re-install Wine I cannot get the nice wine menu under applications...

I'll find a picture...

Here we go... I want to reinstall Wine and get this back in my menu:
[[IMG]http://img212.imageshack.us/img212/2121/89246046ka1.th.png[/IMG]](http://img212.imageshack.us/my.php?image=89246046ka1.png)

Minus the utorrent icon of course. Just the menu: *"Applications> Wine> Programs / Browse C:/ Drive / Configure Wine / Uninstall Wine Software"*

I tried using the synaptic packet manager to completely remove the program and all traces and re-installing it but I still can't get that nice menu back. All I get in the menu following a reinstall is 

Browse C:/ Drive
Configure Wine
Notepad
Uninstall Wine Software

All lumped into my "Other" menu, and when I try to move them in the Edit Menus, all I see is a single program icon called Wine Windows Emulator...

Dammit. Now going back into "*Applications> Other*" they all just disappeared. 

I just removed wine completely for the fourth or fifth time.

Anyone know what is going on here?

---

### Post by firmit on 2008-04-28
Generally, when you uninstall an application such as wine, you only remove the binaries/source. The configuration files is left behind. Which is a good thing if you ever were to re-install your OS and your settings are kept on a separate /home partition.

Now, when uninstalling wine - you should also delete the following:
~/.wine
~/.local/share/applications/wine

Also, you should remove the files (if any):
```
$ ls /usr/share/applications/wine*
```

When you later do a re-install of wine, and (as the OP is actually about) want to tweak the Xfce-menu, you should copy the application-specific instance from /usr/share/application to ~/.local/share/application. The files located in this location is prefered when the menu is generated. 

Example:
The Wine-notepad gets placed under *Other* upon a new wine-install with Xfce-menu. Actually all the applications you install too....
```
$ cp /usr/share/application/wine-notepad.desktop ~/.local/share/application
```
Edit the Category instance to "Category=Wine" as the "Wine-Programs-Accessories" do not work with the Xfce-menu. 

**NB**: to update the menu: 
```
$ touch ~/.config/xfce4/desktop/menu.xml
```
as the "xfdesktop --reload" does not do the trick. Your menu should now be up-to-date.

Something should really be done with the menu-editing in Xfce!

---

### Post by Isakmo on 2008-07-22
I'm with Jammerdelray... I was planning on reinstalling Ubuntu completely until I found this thread...

Thanks for the information!!

---

