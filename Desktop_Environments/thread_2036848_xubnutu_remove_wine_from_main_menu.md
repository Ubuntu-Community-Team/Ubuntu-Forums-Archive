---
title: "xubnutu: remove wine from main menu"
date: 2012-08-03
forum: Desktop Environments
---

### Post by seul on 2012-08-03
After picasa/wine installation, I have wine as the top entry in my main menu.

I want to move it to another place in the menu, but it does not show up in settings->main menu (alacarte).

Googling returns mostly posts of people who uninstalled wine but still had the menu entry. I want to keep wine and the menu entry, but would just like to move it to the accessories-category if possible. If not, I still want to keep wine but remove just the menu entry.

Thanks for your help.

---

### Post by stanciugabriel on 2012-08-03
Did you tried to right-click the menu?
If it works ( it works on XFCE4.10 ), the go click the 'Properties' link .
It will show open a window. Search for 'Edit the menu' in it. When ( if ) you find it, click it.

Click the 'Restore' button. ( the bad thing is that will destroy any modification you made on the menu ) You are going to need to confirm the action.

Wait a little bit.

If it worked, you got the Wine menu back under the system.
If not, I don't know more than what I said here.

Good luck! :D

---

### Post by seul on 2012-08-03
Thanks a lot, stanciugabriel. I made a lot of modifications to my menu, so before resorting to your suggestion, I'll wait to see if another solution pops up. But it's good to know to have something to try!

Cheers!

---

### Post by black veils on 2012-08-04
open the Terminal, enter:

gksudo nautilus

or whichever file manager you will be
using, this will give you privileges to edit
those files.

then go to:

/usr/share/applications

dont delete anything, just right-click and
open files with a text editor. you want to modify the line beginning "category", eg: 

System; 

Settings;

Utility;

Office;

there will be several wine entries in your menu to move, and if it is a folder, you need to edit every item in it. 

to hide a menu entry,add the line: 

NoDisplay=true

---

### Post by seul on 2012-08-04
Cheers Black Veils, your help is greatly appreciated. The technique is a bit tedious, but the effect is mint. I moved everything to where I wanted it now, only one problem remains:

I have Wine -> Programs -> Picasa 3 and in there
* Configure Picasa Photo Viewer
* Picasa 3
* Uninstall

I cannot find .desktop files to edit for these three. Any idea where to look? Thanks again!


And in case someone else comes here with a similar problem:

I found working through the terminal much more convenient. Somehow Nautilus did not display the ».desktop« endings of the files and on right click I could not choose a programme to open them with. So I went for

```
cd /usr/share/applications/

ls
```

and then

```
sudo kate /usr/share/applications/<fielname>.desktop
```

Also note that some of the .desktop-files have different names from what appears in the menu (»Configure Wine« -> »wine-winecfg.desktop« for instance).

---

### Post by black veils on 2012-08-04
that's strange, there is another main location these files get stored, but I really doubt they will be there: 

/home/yourusername/.local/share/applications

you could try also looking in the wine folder in home, or any other picasa folder. 

maybe look through the normal place again, just in case you missed it!

---

### Post by seul on 2012-08-05
> **black veils said:**
> there is another main location these files get stored, but I really doubt they will be there: 

/home/yourusername/.local/share/applications

There is a Picasa.desktop file in there, however, it has no category set and if I give it »System« it indeed appears under System, yet does not go away under wine.

> **black veils said:**
> you could try also looking in the wine folder in home, or any other picasa folder. 


There is something in 

~/.wine/dosdevices/c:/users/Public/Start Menu/Programs/Picasa 3

unfortunately they are .lnk-files, not .desktop. But their names correspond exactly to the menu entries. Opening them with kate give me a lot of gibberish. When I try to copy and paste I only get a single »L« from a lot of trinangles and the occasional word and windows .exe-path.

> **black veils said:**
>  
maybe look through the normal place again, just in case you missed it!

I did a search for »picasa« on what is returned by 
ls /usr/share/applications and there is nothing.

---

