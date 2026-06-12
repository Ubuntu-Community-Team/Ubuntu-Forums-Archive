---
title: "Menu Entry Deleted"
date: 2010-08-20
forum: Desktop Environments
---

### Post by rykel on 2010-08-20
Hi, I accidentally deleted the Menu entry for Desktop Drapes and despite purging and reinstalling the program, the Menu entry is GONE.

May I know how I can restore the item and - more importantly - if this is an issue that ought to be addressed in an upgrade? (ie. Menu entries should be restored too with reinstallation)

---

### Post by dagdeniz on 2010-08-20
I haven't got it well, do you mean the entry in the main menu for the application?
Then press alt+f2, run alacarte, add new entry for any application you want. 
Do you mean an entry called "menu" in the application? 
Then show hidden files in Nautilus, look for a directory or file called ".desktop-draper" or something like that and look into ".config" directory and delete anything you find about desktop draper. Generally those files and folders are your configuration files for an application and unlike general configuration which are not located in your home directory, they are not purged upon uninstallation.

---

### Post by rykel on 2010-08-20
> **dagdeniz said:**
> I haven't got it well, do you mean the entry in the main menu for the application?
Then press alt+f2, run alacarte, add new entry for any application you want. 
Do you mean an entry called "menu" in the application? 
Then show hidden files in Nautilus, look for a directory or file called ".desktop-draper" or something like that and look into ".config" directory and delete anything you find about desktop draper. Generally those files and folders are your configuration files for an application and unlike general configuration which are not located in your home directory, they are not purged upon uninstallation.


Hi, thanks for offering to help! I meant #1 - the entry in the main menu for the Desktop Drapes application. I wish to restore the orginal entry that was created when I installed Desktop Drapes. I know that I can manually recreate the entry, but I would like to avoid that hassle.

---

### Post by earthpigg on 2010-08-20
if reinstalling didn't re-generate the menu, try uninstalling it through synaptic with the 'completely remove' or 'completely uninstall' or whatever it is box checked, and then reinstalling it afterwards.

it would probably end up being less work to manually recreate it, as the poster above me described.

---

### Post by Capt_Scribble on 2010-08-21
I'm having this same problem with the game gnome-mahjongg. I completely uninstalled with synaptic, reinstalled, and still no menu entry. I did recreate it manually, but finding the correct file to execute and the original icon can be very frustrating.

---

### Post by earthpigg on 2010-08-21
/usr/games/mahjongg

and

drapes --tray

---

### Post by Capt_Scribble on 2010-08-21
Thanks, but I already recreated the launcher and that doesn't solve the original problem. My point was that manually recreating the launchers is a hassle. Is it not reappearing automatically because of an old entry somewhere? And what does "--tray" do? I think rykel is right, this issue should be addressed in future releases. Otherwise people will think the installer isn't working.

---

### Post by rcayea on 2010-08-21
Maybe this will help...


 
If you deleted from your Applications menu then look in home folder -> .config/menus/applications.menu (.config is a hidden folder, when in home folder go Ctrl+h if not visible 

Example program is Wine. You should see an entry like this (i added the capital letters to the word, Deleted to make it stick out:

Code:
```
</Menu>
	<Menu>
		<Name>wine-wine</Name>
		[COLOR="Red"]<DELETED/>[/COLOR]
	</Menu>
</Menu>
```
Remove what's capitalized and colored in red(again it won't be in your file, I just capitalized it to stick out), and save

---

### Post by Capt_Scribble on 2010-08-21
Thanks, that's the file I was looking for! I'll share what I did because it was a little different. I was trying to make my own .desktop file in /usr/share/applications and it ended up making a mess.

I looked in my applications.menu file and saw it was only *excluded* instead of *deleted*, so it should have still showed up in the Main Menu editor:
```
<Menu>
        <Name>Games</Name>
        <AppDir>/home/username/.local/share/applications</AppDir>
        <Exclude>
            <Filename>mahjongg.desktop</Filename>
        </Exclude>
</Menu>
```So I changed it to this:
```
<Menu>
        <Name>Games</Name>
        <AppDir>/home/username/.local/share/applications</AppDir>
        <Include>
            <Filename>mahjongg.desktop</Filename>
        </Include>
    </Menu>
```Nothing happened. I also checked for mahjongg.desktop in /usr/share/applications just to make sure it was there. Then I looked at my personal mahjongg.desktop file in /home/username/.local/share/applications with gedit and noticed it was all messed up.

So my fix was to delete the .desktop file in /home/username/.local/share/applications, uninstall the app, reinstall the app.

Anyway, I think the Main Menu editor could use an option to view deleted entries so people don't have to dig around in their config files.

---

### Post by Gaygerbil on 2010-08-21
Just a word of advice if you delete a command for a program or app you can easily readd it by typing the command again (i.e. for mahjongg or w/e you wanna readd) just type 'mahjongg' in command when you create a new item. Ubuntu will automatically find the icon for you.

This works for most programs and apps on Ubuntu because most of the time the command for the program/app is simply just its name! : D

Something I really admire about Linux is that it keeps things simple but very customizable.

---

### Post by rykel on 2010-08-22
> **Capt_Scribble said:**
> Thanks, but I already recreated the launcher and that doesn't solve the original problem. My point was that manually recreating the launchers is a hassle. Is it not reappearing automatically because of an old entry somewhere? And what does "--tray" do? I think rykel is right, this issue should be addressed in future releases. Otherwise people will think the installer isn't working.

Hi, "--tray" gives an error msg - **Sorry unknow argument: --tray**

But no big deal, the Desktop Drapes program still runs properly.

---

