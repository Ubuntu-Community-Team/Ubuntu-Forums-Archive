---
title: "how to create terminal shortcut auto log into a specific server?"
date: 2011-04-07
forum: Desktop Environments
---

### Post by ckkc on 2011-04-07
Hi all, in windows I can use Putty to create a shortcut which loads a predefined profiles to log into a specific server. How can I do it in Ubuntu? (Instead of click on the terminal icon to open it, type ssh ..... ) Thanks in advanced.

---

### Post by zarthon on 2011-04-07
> **ckkc said:**
> Hi all, in windows I can use Putty to create a shortcut which loads a predefined profiles to log into a specific server. How can I do it in Ubuntu? (Instead of click on the terminal icon to open it, type ssh ..... ) Thanks in advanced.

You can create a profile in Gnome Terminal
Open a terminal and go to Edit -> Profiles
Click New Profile.  In the dialog click the Title and Command tab.
Under command select the check box: "Run a custom command instead of my shell.
In the Custom command field enter the shh command that you use to connect or create a script file and then enter the path to the script here.
Some people like to have a script that then gives a menu of systems in the terminal that way they do not need to create a profile for every system they want to easily log into. 

I would not put your password in either of these places. Leave it out and be prompted when you open the window or tab with the profile.

If you have a profile for each system you can use the other profile settings to create a custom look as reminder of what system you are using.

For information on the syntax of ssh type "man ssh" into a gnome terminal window.


Creating a launch icon on the gnome Panel
To create a launch icon on the gnome Panel ctrl+mouse drag the icon for gnome terminal (called "terminal") to the panel if one is not there already.
You can ctrl+mouse drag to create a duplicate of the shortcut if it's there. 
Edit the command to look like
gnome-terminal --window-with-profile=PROFILENAME

Change the Icon to some other graphic you will know is your remote system.

An alternative would be to just create the shortcut on the launch bar and use

--command=STRING
Where the string would be the ssh command

This is not as nice though. The profile gives you the choice to open the remote session from the gnome terminal menu. You will also loose the reminder and pleasantry of choosing between mauve on pale kaki, or Malibu blue on sandy-beach with sea foam green highlights. 
The default colors in gnome terminal are torturous so regardless of what you do, tweak the profile colors ! This is also where you can make terminal windows transparent with compiz enabled.

If tweaking colors is too time consuming you can use color codes from a web page / css, or google "color schemes"

---

### Post by ckkc on 2011-04-07
> **zarthon said:**
> You can create a profile in Gnome Terminal
Open a terminal and go to Edit -> Profiles
Click New Profile.  In the dialog click the Title and Command tab.
Under command select the check box: "Run a custom command instead of my shell.
In the Custom command field enter the shh command that you use to connect or create a script file and then enter the path to the script here.
Some people like to have a script that then gives a menu of systems in the terminal that way they do not need to create a profile for every system they want to easily log into. 

I would not put your password in either of these places. Leave it out and be prompted when you open the window or tab with the profile. If you want to login with one click look into using a public key instead of a password to authenticate. 

If you have a profile for each system you can use the other profile settings to create a custom look as reminder of what system you are using.

Beautiful! Thanks zarthon.

---

