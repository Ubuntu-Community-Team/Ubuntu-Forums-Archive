---
title: "A few general questions about Kubuntu"
date: 2005-07-04
forum: Desktop Environments
---

### Post by arcanistherogue on 2005-07-04
I upgraded with apt-get install from ubuntu, and would like to know how to: 

- make the text on the desktop smaller
- Add a trash Icon, a system Icon, and a home folder icon to my desktop.  (i didnt have these in Ubuntu, so they aren't there)
- Make it so you need to double click to open folders and whatnot.

Thanks to anyone you helps :)

---

### Post by sonny on 2005-07-04
The exact location of all that I don't know... but I recommend you to go to the control center and search for those options (the only thing I know is htat they're there), wich will be nice since you might get some more options you'd like to change.

---

### Post by thagame on 2005-07-04
ok lets do this step by step. for desktop fonts go to control center (K menu > Control Center) appearance and themes, fonts , and change the Desktop fonts section. for trash can hit system (icon next to K button) hit Home folder, then desktop. theres a file called trash.desktop  right click it and hit open with... and in the Open With: put kwrite. now near the top it will say hidden=true  change true to false (Hidden=false) then reset kde (alt + ctrl + backspace) or logout. 
and finally. go back in control center, Peripherals > Mouse. right there in the middle you should see Icons section. click next to Double-click to open files and folders.

hope this helps. and remember you probably have to log out then in to make any changes work.

---

### Post by SGC on 2005-07-04
To change the desktop font:
Control center -> Appreance & Themes -> Fonts
Then click on the "choose..." button besides "Desktop"

To open files and folders with double click:
Control center > Peripherals > Mouse
And choose "Double click to open files and folders (select icons on first click)"

You can find a shortcut for the trash and the home folders here:
/usr/share/apps/systemview
Just drag the icons to the desktop

---

### Post by t2kburl on 2005-07-04
to add a desktop icon for your Home directory ...

go to /home/<yourusername>/desktop/    right click in an open area and select Create New > Link To Location (URL)   when the browse window opens type:

Home

as the title and type:

/home/<yourusername>/

in as the URL

This will create a generic desktop icon titled Home
To get the proper Home Icon, just right click the generic new Icon on the desktop and select properties. Click on the Icon to choose a new one. I think the proper icon is under applications and titled kth_home  ...  look around ...  you'll see it

---

### Post by arcanistherogue on 2005-07-04
Oh sweet, the home thing and double click worked.  The only thing that didnt work was the Trash bin.  I didn't find any file for that... Perhaps I should do it through Gnome, and then just drag the icon onto my desktop.  

Well anyway, I found some more things I want to know...

-How do I make the Icons bigger on the desktop?
-How do I change the Icon name color to white?

Thanks alot for everyones help.

---

### Post by arcanistherogue on 2005-07-05
I actually just found the color, I was fooling around with teh configuration of the desktop.

---

### Post by codejunkie on 2005-07-05
the trash icon should be in your Desktop folder but you have to click on view show hidden files.
or you could open up /usr/share/apps/systemview/ and copy the files and paste them in /home/username/Desktop hope this helps.

---

### Post by godzero on 2005-07-05
desktop icon size:

control center, Appearance & Themes, icons, advanced tab, desktop/file manager, choose size from drop down.

---

