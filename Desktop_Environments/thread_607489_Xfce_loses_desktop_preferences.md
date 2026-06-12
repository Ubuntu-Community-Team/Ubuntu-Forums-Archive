---
title: "Xfce loses desktop preferences"
date: 2007-11-09
forum: Desktop Environments
---

### Post by Ubunthree on 2007-11-09
A few days ago I installed Gutsy, the third Ubuntu installation (after Edgy and Feisty) that I've done on my machine. I like to have both Gnome and Xfce available, so I get the standard Ubuntu disk from on-disk.com and then apt-get the xubuntu-desktop package after installation. Actually I prefer Xfce and use it almost exclusively. I've also experimented with Fluxbox and Openbox just for fun. Anyway it all worked perfectly with Feisty and was working fine with Gutsy as well, until today, when things went a bit squirrelly. 

Problem: Xfce starts up with the plain pinky-beige background color(like the default in Gnome) instead of my desktop preferences (color, background image etc.). Also, when I right- or middle-click on the desktop, the main menu and the workspace pager or whatever it is do not come up. Calling up the Desktop Preferences dialog shows that the "Allow Xfce to manage the desktop" option is deselected, and all of the other controls greyed out. Activating "Allow Xfce..." enables the other options, applies the preferences that I have set there, and enables the desktop menus. It also brings up an "Information" box which says:

[COLOR="DarkSlateGray"]To ensure that Xfce does not manage your desktop the
next time you start Xfce, please be sure to save your
session when logging out. If you are not using the Xfce
Session Manager (xfce4-session), you will need to
manually edit your ~/.config/xfce4/xinitrc file. Details are
available in the documentation provided on [http://xfce.org/](http://xfce.org/).[/COLOR]


The xfce4 folder has several other folders in it, none of which contain the "xinitrc" file. The closest thing to xinitrc that I can find is ~/.config/xfce4-session/xfce4-session.rc (note the different folder). It appears to store the Sessions and Startup settings. Whether it is relevant at all, I don't know, but here is what is currently in it:

[COLOR="DarkSlateGray"][General]
AutoSave=false
PromptOnLogout=false
HibernateButton=false
SuspendButton=false
DisableTcp=true
SessionName=Default
SaveOnExit=false

[Compatibility]
LaunchGnome=true
LaunchKDE=true

[Chooser]
AlwaysDisplay=false

[Splash Screen]
Engine=balou[/COLOR]

It doesn't seem to matter which way the AutoSave control is set.

Checking that "Allow Xfce..."control box gets things working normally as far as I can tell, but every time I reboot the system, or even do a Ctrl/Alt/Backspace to restart the desktop, my preferences are disabled again, and I have to call up the dialog and click the checkbox again.

Maybe at some point in the process I wiped some config file somewhere that it needs? Or is Gnome's presence on the system interfering with Xfce's operation in some way? Any ideas will be appreciated.

Thanks!

---

### Post by Ubunthree on 2007-11-09
And, now a couple of other probably related things:

Choosing "Quit" from the main Xfce menu used to bring up a GUI shutdown menu (Shutdown, restart etc.); now instead it automatically restarts the desktop the same as if I had done Ctrl/Alt/Backspace, and I have to shut down from the login dialog.

When I power up, I don't get the Ubuntu logo with the progress bar any more; now I get a blank black screen until the Nvidia splash comes on. No progress bar during shutdown, either.

And another general question, as long as I'm here: Would Xfce work better in a straight Xubuntu installation than installed alongside Gnome? The two always played nice together with Feisty, though.

Thanks for any advice.

---

### Post by Echow on 2007-11-13
Hey there
Just about your auto restart problem, I had this problem also. You need to go to the "Sessions and startup" option under settings and enable "prompt on logout". I think this might be a bug but im not sure, with this my session doesnt just automatically restart.

For your background colour maybe try this:
[http://xubuntu.wordpress.com/](http://xubuntu.wordpress.com/)
Also check to see under synaptic if xubuntu-splash-startup is loaded.

It sounds like xfdesktop is not loading at startup. Now that you are able to see your chooser again make sure you enable xfdesktop (through terminal) and then when you logout check the "save session for future logins". If this fails to work then try adding xfdesktop under the autostarted applications.

I dont think xfce would make any differences on a xubuntu/ubuntu installation. I do think though that there are a few bugs with xfce but hopefully they will be ironed out in the updates. I have been using xubuntu for a little while, I think my feisty xubuntu was a bit less problem ridden than my gutsy one for some reason. Hope this helps.

---

### Post by Ubunthree on 2007-11-15
Thanks. The "prompt on logout" setting worked. I didn't try the procedure indicated on your linked site, as my situation was a bit different; my loss of background setting was persistent rather than momentary, and reading the thread that it came from ([http://ubuntuforums.org/showthread.php?p=3584409#post3584409](http://ubuntuforums.org/showthread.php?p=3584409#post3584409)) suggested that the issue was something different than what I had. Reading the site did give me a better idea of what to look for on other sites, though. My fiddling has gotten Xfce to start up more or less normally now, although font sizes somehow got screwed up. Window titles, panel buttons and menu, and Firefox were all showing microscopically small characters, though my screen resolution was 1024x768 as always. I've fixed that mostly too, at least enough for me to go back to using Xfce, for the moment anyway.

I still get a blank screen without logo or progress bars at bootup and shutdown, though, whichever environment I'm using.

I like Gnome/Nautilus fine. I just find that Xfce/Thunar runs slightly faster and lets me configure the appearance a bit more the way I like it. It ran smooth as glass with Feisty; Gutsy seems to be more twitchy.

Thanks again!

---

