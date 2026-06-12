---
title: "Desktop theme"
date: 2012-01-05
forum: Desktop Environments
---

### Post by fronow on 2012-01-05
Hey how do you make a theme for the desktop I don't like color  orange but greens good. :) 
yes I am a nub so what I haven't been on a linux for a month 
:(

---

### Post by oldos2er on 2012-01-05
Moved to Desktop Environments.

Are you asking how to create a theme, or install one? 
[http://blog.sudobits.com/2011/06/16/best-gnome-3-shell-themes/](http://blog.sudobits.com/2011/06/16/best-gnome-3-shell-themes/)

---

### Post by wvcaudill2 on 2012-01-05
> **oldos2er said:**
> Moved to Desktop Environments.

Are you asking how to create a theme, or install one? 
[http://blog.sudobits.com/2011/06/16/best-gnome-3-shell-themes/](http://blog.sudobits.com/2011/06/16/best-gnome-3-shell-themes/)

Could you briefly explain how to install a theme? I've been looking for a howto guide, but I can't find one for the life of me!

By the way, I've installed the Gnome tweaks tool, but I dont know where to put my downloaded theme folders.

---

### Post by Frogs Hair on 2012-01-05
(Installing Downloaded Themes / Icons)

Download and extract the packages .

Install the Gnome Tweak Tool / advanced settings from the software center for making theme selections.  

(Single User) Create a .themes and .icons folder in home / hidden folders . Use Ctrl + H to open the hidden folder option in Nautilus .

(All Users) Use gksudo nautilus to open the file system and navigate to   usr / share / themes or icons .

Place the folders in either location making theme selections using Advanced Settings . Logout - in may be required .

---

### Post by cortman on 2012-01-05
Or another way to install themes, using Gnome-tweak...

Download zipped theme file.

If the theme is a .gz or .bz2 or .7z unzip and rezip as a .zip file. For some reason Gnome-tweak only seems to recognize .zip files.

Open Gnome-tweak, select to browse for a theme, and select the theme.zip file.

Works great for me.

---

### Post by oldos2er on 2012-01-05
> **wvcaudill2 said:**
> Could you briefly explain how to install a theme? 

Looks like Frogs Hair answered your question; I don't use Gnome myself.

---

### Post by wvcaudill2 on 2012-01-05
> **Frogs Hair said:**
> (Installing Downloaded Themes / Icons)

Download and extract the packages .

Install the Gnome Tweak Tool / advanced settings from the software center for making theme selections.  

(Single User) Create a .themes and .icons folder in home / hidden folders . Use Ctrl + H to open the hidden folder option in Nautilus .

(All Users) Use gksudo nautilus to open the file system and navigate to   usr / share / themes or icons .

Place the folders in either location making theme selections using Advanced Settings . Logout - in may be required .

I followed these steps exactly, however, my theme does not show up under the Advanced Settings. By the way, the option for "Shell Themes" is not available and there is an orange triangle icon beside it. Is this normal?

Lastly, I noticed when I went to login, that there were different sessions(?) I could choose from now.
There was : Ubuntu, Ubuntu 2D, Gnome, and Gnome Classic
Why/how did this happen? And I should be using the Ubuntu one, right?

---

### Post by wvcaudill2 on 2012-01-05
> **cortman said:**
> Or another way to install themes, using Gnome-tweak...

Download zipped theme file.

If the theme is a .gz or .bz2 or .7z unzip and rezip as a .zip file. For some reason Gnome-tweak only seems to recognize .zip files.

Open Gnome-tweak, select to browse for a theme, and select the theme.zip file.

Works great for me.

Where is the option to browse for a theme? I can't find it!

---

### Post by cortman on 2012-01-06
> **wvcaudill2 said:**
> Where is the option to browse for a theme? I can't find it!

Under the "theme" tab, at the top where it says Shell theme, there's a button next to the drop down menu that will let you browse for themes.

---

### Post by wvcaudill2 on 2012-01-06
> **cortman said:**
> Under the "theme" tab, at the top where it says Shell theme, there's a button next to the drop down menu that will let you browse for themes.

This is not available to me. Am I missing something extra?

---

### Post by Frogs Hair on 2012-01-06
> **wvcaudill2 said:**
> I followed these steps exactly, however, my theme does not show up under the Advanced Settings. By the way, the option for "Shell Themes" is not available and there is an orange triangle icon beside it. Is this normal?

Lastly, I noticed when I went to login, that there were different sessions(?) I could choose from now.
There was : Ubuntu, Ubuntu 2D, Gnome, and Gnome Classic
Why/how did this happen? And I should be using the Ubuntu one, right?

Make sure you are using GTK 3 themes , _GTK 2 themes will not work_ . The Gnome shell theme tab is not available in Unity . See the themes at the link .[http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=159cd0117b52349ffa74cebc97de0182](http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=159cd0117b52349ffa74cebc97de0182)

If the GTK 3 themes don't appear try to restart and check all folders to make sure the themes are fully extracted .

---

### Post by wvcaudill2 on 2012-01-06
I got it working now, thanks!

One last question, some themes have a Splash theme. Where/how do I install this?

---

### Post by Frogs Hair on 2012-01-06
I have not installed splash themes in 11.10 , so do a forum / web search and make sure that any instructions are specific to 11.10 / Gnome 3  . Instructions for previous release may cause problems .

---

### Post by cortman on 2012-01-06
Looks like Shell theme has an unhappy sign next to it. Do you have the user-theme extension enabled in Shell Extensions?

---

### Post by wvcaudill2 on 2012-01-06
> **cortman said:**
> Looks like Shell theme has an unhappy sign next to it. Do you have the user-theme extension enabled in Shell Extensions?

I dont think so . . .

---

### Post by cortman on 2012-01-06
> **wvcaudill2 said:**
> I dont think so . . .

That would explain it. If you enable the extension you can do it the way I gave.
But it looks like Frogs Hair's way worked great.

---

### Post by Frogs Hair on 2012-01-06
> **cortman said:**
> That would explain it. If you enable the extension you can do it the way I gave.
But it looks like Frogs Hair's way worked great.

I use the Gnome Shell as well as Unity and having the user themes extension installed / enabled does not allow me to browse with the shell tab in Unity . :confused:

---

### Post by cortman on 2012-01-07
> **Frogs Hair said:**
> I use the Gnome Shell as well as Unity and having the user themes extension installed / enabled does not allow me to browse with the shell tab in Unity . :confused:

Unhappiness. I've been using Unity on my VBoxes a bit, mainly because I have yet to get Gnome-shell working in a VBox.

---

### Post by fronow on 2012-01-08
how to make one

---

### Post by fronow on 2012-01-08
wow i have no file called .Themes so how will i change my theme

---

### Post by Frogs Hair on 2012-01-08
Open the home folder , press Crtl + H or from view on the application menu select show hidden folders .  Select File from the application menu create two new folders titled .themes and .icons . 

The . will hide the folders . If themes or icons are installed in the file system , usr/share/themes or icons the folders are already there and will not include the dot .

---

### Post by fronow on 2012-01-10
hey could the .themes be under the unity folder

---

