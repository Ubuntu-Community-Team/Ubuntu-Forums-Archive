---
title: "File Drawer(Nautilus) Does Not Display Alphabetically in 14.04 Gnome Metacity"
date: 2015-04-22
forum: Desktop Environments
---

### Post by mark bower on 2015-04-22
The File Drawer(Nautilus) will not display the home directory correctly.  This is, when I open Nautilus to display the Home folders with Preferences set to List,Folders First mode, the home folders will not display alphabetically.  See snap shot below.  However, all other directories on another backup HD, USB, or sub-directories in the home folder can be made to display alphabetically.

Any suggestions?

[http://ubuntuforums.org/attachment.php?attachmentid=261459&d=1429675440&thumb=1&stc=1](http://ubuntuforums.org/attachment.php?attachmentid=261459&d=1429675440&thumb=1&stc=1)

---

### Post by dino99 on 2015-04-22
That png show 1 file and a few folders, sorted by date, as expected. You have set your pref to display file(s) first, then folders.

---

### Post by deadflowr on 2015-04-22
> **9d9 said:**
> That png show 1 file and a few folders, sorted by date, as expected. You have set your pref to display file(s) first, then folders.
+1 it sorted by the Modified selection.
Click on the Name field to sort by alphabet.

Though, I don't see any file, only folders.

---

### Post by mark bower on 2015-04-22
My home directory display is "frozen" in List,Name,Folders First mode by file modification date order, while sub-directories can be displayed in list mode in either in alpha or modification date order.  Via Synaptic, I uninstalled Nautilus(not compete removal) and reinstalled with no change - still frozen.  

So I am looking for an easy solution to get the /Home directory to display folders alphabetically when in List Mode?  Setting Preferences does not do the trick.

---

### Post by mc4man on 2015-04-22
Don't use metacity & your last post has no pic but maybe try this. List view works a bit differently than icon.
So - 
open nautilus (Files) > Edit > Preferences > Default View > Arrange Items > choose "By Name"
Close preferences
Close then open nautilus at your  home folder > View > Reset View to Defaults

---

### Post by mark bower on 2015-04-22
@mc4man
I went thru the sequence you suggested and no change, ie, folders in Home will not arrange alphabetically - they are alphabetical in all sub-folders.  Ironically, tragically, I messed with Nautilus on another computer with 12.04 and now that Home will not display alphabetically while the sub-folders are compliant to the Name ordering.  And if I select to show hidden files/folders in Home, then all entries are still tied to Modification Date, which results in folders being mixed with files, not folders 1st!  If I click on the ascending/decending arrow for Modification Date, the folders are responsive and adjust accordingly.

IT IS OBVIOUS THAT THE HOME "FOLDERS NEED to be DELINKED FROM THEIR MODIFICATION DATE".  Removing Date Modified from column display makes no difference.

You suggest not using Metacity?  Why not, or what would you recommend to match the Gnome Classic desktop?  I do not know the difference between Gnome Classic, Metacity or Compiz.

---

### Post by mc4man on 2015-04-22
I didn't suggest not using metacity,  only that I don't use it in case it's some issue there that's not in an ubuntu session (unity/compiz.

If you go to icon view are they arranged by name?
As far as in* list view *then don't know, as mentioned Edit > preferences... only alters the Default setting, it doesn't change the current method of arranging files. 
(list view only uses what is set as the default on a per folder basis

---

### Post by mark bower on 2015-04-22
I had always used what I knew as Gnome Classic, but when I did the install on 14.04, voila, a choice between Metacity or Compiz?

The icon view in Home is also displayed in the incorrect order for Name.  And the icon view in the sub-folders display alphabetically.  The problem resides with the Home directory, and of course, the one used the most.

---

### Post by mc4man on 2015-04-22
Well I have a 2nd install of 14.04 I use for testing things so installed gnome-session-flashback & logged into a gnome session (metacity session
It works as intended & described using the cog icon in nautilus for Preferences & the down arrow for View menu.

So in icon view changes in the View menu are immediate, (Name, Size, Type, Mod) & in list view by changing the Default in Preferences  menu, then using the Reset View .. in View menu.

Maybe try this - This* should* give you a fresh dconf at orig defaults for everything that uses dconf so don't do if an issue for you, if you're ok with that  - 

Open nautilus > .config/dconf  (.config is a hidden folder
Inside is a file named user
Delete that file & **immediately** go ctrl+alt+F1
login & then go sudo reboot

---

### Post by mark bower on 2015-04-22
@mc4man

I appreciate your effort and hanging in with me.  

But before trying your idea, let me describe an easily observed malfunction.  I have preferences set to list,name,sort folders before files.  I am able to get **Home icons displayed correctly(alphabetically)**. Then I click on the "View Items as List" icon, seen as 3 parallel bars.  The display goes to list mode but the **files lose their alpha order and revert to the file modification date order**.  The List folder order display clearly should be alphabetical as seen in the Icon folder display order; this is just a one click choice change?  

The problem is similarly duplicated by toggling between Ctrl+1 and Ctrl+2.     /Home icon **alphabetically** ordered folders folders go to list **modification dates** ordered folders.

Does this tell us anything for which I could make a simple change?  And again, all but /Home seem to behave properly with Nautilus.

---

### Post by mc4man on 2015-04-22
When you are in list view - 
Go Cog icon > Preferences > Views > Arrange by: set to Name
Close that menu, then - 
View menu > Reset View to Defaults

If that doesn't set list view back to Name/alpha .. then do the deal about deleting user file, ect. 
(logging in to a tty is simple, type username, press enter on keyboard, type in password, press enter on key.., type in sudo reboot press enter..

---

### Post by CantankRus on 2015-04-22
If you arrange files/folders by clicking on "modified" in list view then that folder will
arrange as "modified" in the list view no matter the setting in preferences. 
The preference setting doesn't override what you manually change to in a given folder for each view.
Icon view and list view can also have different arrange settings for the same folder.

Open your home folder in list view, click on "Name" in the  top bar to arrange by name.
Close.

Reset your preference in dconf via terminal (default is by name)...
```
gsettings reset org.gnome.nautilus.preferences default-sort-order
```
Open Files in list view and home should be organized by "name" as indicated by the small triangle.

---

### Post by mark bower on 2015-04-23
Solved.  When the home folders are displayed in list mode, clicking on the column heading titled NAME toggles the order to alphabetical - that simple.  (Toggling again, and the list order makes no sense that I can observe, and not tied to modification dates, but no matter for my needs.) I never would have thought to click on the column heading to make a change, driven instead to use the drop down menus via the icons.  This method was not intuitive for me.

@pc4man.  Thank you for your suggestion on how to solve the problem by a digging a bit deeper, I'm sure it would have worked - I did play with going to the virtual screens and logging back in - yes, easy to do.

@CantankRus.  Thank you.  You put me onto the solution I needed with ```
Open your home folder in list view, click on "Name" in the top bar to arrange by name.
```

Challenging, but life is good with Ubuntu again.

---

