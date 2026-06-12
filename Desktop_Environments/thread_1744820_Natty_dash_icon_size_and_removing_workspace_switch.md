---
title: "Natty: dash icon size and removing workspace switcher"
date: 2011-04-30
forum: Desktop Environments
---

### Post by chicgeek on 2011-04-30
Hi all! I did my best to search for any solutions but came up empty-handed.

**Is it possible to reduce the size of the dash icons in Natty?**
They are unnecessarily massive for my taste. Please note that I am not talking about the launcher icons which can be resized in Tweak.

**Is it possible to remove the workspace switcher icon from the launcher? [[solved]("http://ubuntuforums.org/showpost.php?p=10760228&postcount=6")]**
I've removed the places icons as per [this thread]("http://ubuntuforums.org/showthread.php?t=1734534") and wouldn't mind removing this icon as well.

Cheers,

---

### Post by nnard1616 on 2011-04-30
Install compiz:

sudo apt-get install compizconfig-settings-manager

Open Unity-Launcher (the ubuntu icon in top left of screen) and search for compizconfig settings manager.

Scroll down to the "Desktop" section, and select "Ubuntu Unity Plugin".  Next, click on the "Experimental" tab and then adjust the "Launcher icon size" slider until you get the size that you want.


Not sure how to remove the Workspace Switcher icon, unfortunately.

---

### Post by nourathar on 2011-04-30
+1 !
I think the dash needs some easy customization options and the icon size is ridiculous.

@nnard1616 you're describing how to change the launcher icon size, not the dash icon size...

---

### Post by nnard1616 on 2011-04-30
Here's a site for more useful stuff:

[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

---

### Post by chicgeek on 2011-04-30
> **nnard1616 said:**
> Here's a site for more useful stuff:

[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

None of which answers either of my queries, nnard... (Actually, that post links to the thread I referred to for removing the places icons as a source. Not very useful, I'm afraid.)

Thanks for reading my whole post, nourathar. :) I'll keep searching and checking here in case someone sorts something out.

---

### Post by Version Dependency on 2011-05-02
I have found a way to get the Workspace Switcher icon to no longer appear in the Unity launcher.  

First, open up a terminal and open gnome-panel by typing:
```
gnome-panel
```This launches the old gnome panel.  Your gnome   panel should have a Workspace Switcher on it, probably in a 2 X 2 grid   pattern.  (If you don't have a Workspace Switcher on the gnome-panel,   right-click on the panel and add it.)  Now right-click on the Workspace   Switcher on the gnome-panel and select Preferences.  Change the columns   to 1 and the rows to 4.  Now log out of Unity...then log back in.  The   switcher on the launcher will be gone. 

Now your desktop wall will be in a 1 X 4 grid, up to down...rather than   side to side.  But this all I've found to work.  Changing to a 4 X 1   grid side to side will not remove the launcher switcher.  

NOTE: To get the Unity launcher switcher back, simply open the   gnome-panel in terminal again, and go back to a 2 X 2 grid.  Logout and   log back in.

---

### Post by Krytarik on 2011-05-02
You can also just change the setup of the workspaces here:
"CompizConfig Settings Manager -> General Options -> Desktop Size" ;-)

Greetings.

---

### Post by bbrabender on 2011-05-03
I agree with all of you that the icons for dash are way too big. I could use it without my glass and be fine.

---

### Post by brucelyk2 on 2011-05-03
[SIZE=4]the dash icons are so big they won't all fit[/SIZE].[SIZE=4]  I only see six and I know there are more.[/SIZE] 
Please

---

### Post by chicgeek on 2011-05-07
> **Version Dependency said:**
> I have found a way to get the Workspace Switcher icon to no longer appear in the Unity launcher.  Worked like a charm!!  Thank you. Marked as a solution in my original post.

Anyone else have thoughts on changing the size of the dash icons?

---

### Post by bigsmitty64 on 2011-05-08
This is the answer I got over at [askubuntu]("http://askubuntu.com/questions/40547/can-i-change-the-icon-size-in-dash")  regarding changing icon size in the dash, from Jorge Castro who works for Canonical on 
the Ubuntu Community Team.

[B]"The icon size is hard coded in 11.04, so this is currently not possible."

[/B]

---

### Post by chicgeek on 2011-05-08
> **bigsmitty64 said:**
> This is the answer I got over at [askubuntu]("http://askubuntu.com/questions/40547/can-i-change-the-icon-size-in-dash")  regarding changing icon size in the dash, from Jorge Castro who works for Canonical on 
the Ubuntu Community Team.

[B]"The icon size is hard coded in 11.04, so this is currently not possible."

[/B]
Thank you!  That is a downright shame and a bit of an embarrassment for Canonical, really. But it's at least good to get a definitive answer... for the mean time. :)

---

### Post by bigsmitty64 on 2011-05-09
Perhaps a light at the end of the tunnel though?  He did say **"currently"** not possible. :D 
I'm sticking with classic desktop for now. The whole unity layout feels too "mobile...app....touch screenish to me :(

---

### Post by quimkaos on 2011-05-14
lol... **"The icon size is hard coded in 11.04, so this is currently not possible."**

they must think we all have really poor sight !
with this inability to change configurations in unity i'm going to continue using ubuntu classic...
tho the idea is good it needs more development...

this is not "Your PC, your way"...

---

### Post by shayc on 2011-11-19
For Ubuntu 11.10: 
Open CompizConfig (you might need to install that from the Ubuntu Software Center as is it not installed by default)
Go to Desktop -> Expo 
Uncheck Expo (Disable Expo)

This will eliminate multiple spaces as well as the related bar button

---

