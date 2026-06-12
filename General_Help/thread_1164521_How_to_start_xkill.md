---
title: "How to start xkill?"
date: 2009-05-19
forum: General Help
---

### Post by PerfectReign on 2009-05-19
I am a recent convert to Ubuntu from SUSE/openSUSE. I have used the other distro with KDE for five years before switching over to Ubuntu and finally accepting GNOME.  

In any case, I had a file browser window (actually two of them) that wouldn't respond or close when clicking the x in the top right.

In openSUSE, I'd simply hit CTRL+ALT+ESC to bring up a skull and crossbones to close the window and kill that application.

Trying that in Ubuntu, I didn't get anything. I fired up the browser and read that the program beign called is xkill. The solutions in ubuntu seem to call for hitting alt+f2 to bring up the run dialog and then typing in xkill. 

I'd like to assign CTRL+ALT+ESC to the xkill command. 

I looked at the menu and didn't see xkill in the applications or system menu trees.

---

### Post by baseface on 2009-05-19
have u tried using the shell?
man kill

---

### Post by VCoolio on 2009-05-19
1. There is a panel icon to kill windows. Right click on a panel, add to panel and scroll down to find it. Once put on the panel click the icon, then the bad app. 
2. You can add a keybinding for xkill in system > preferences > key shortcuts. But you can't escape this one, you'll have to click somewhere; the icon you can cancel.

---

### Post by sarang on 2009-05-19
> **VCoolio said:**
> 1. There is a panel icon to kill windows. Right click on a panel, add to panel and scroll down to find it. Once put on the panel click the icon, then the bad app. 
2. You can add a keybinding for xkill in system > preferences > key shortcuts. But you can't escape this one, you'll have to click somewhere; the icon you can cancel.

The applet is called 'Force Quit', btw.

---

### Post by PerfectReign on 2009-05-20
> **baseface said:**
> have u tried using the shell?
man kill

LOL!

I'm trying to get away from using the command line as much as possible. IMO, I used the command line on my Apple II and TRS-80, and should not have to downgrade to it 25+ years later.

As it is, I'm still stuck using the CLI for simple tasks like a password and - I just found out yesterday - for setting up SU as a root override.  Oh, and my Cisco vpnclient still is mired in teh command line.

---

### Post by PerfectReign on 2009-05-20
> **VCoolio said:**
> 1. There is a panel icon to kill windows. Right click on a panel, add to panel and scroll down to find it. Once put on the panel click the icon, then the bad app. 
2. You can add a keybinding for xkill in system > preferences > key shortcuts. But you can't escape this one, you'll have to click somewhere; the icon you can cancel.


Okay, that works for me. I added Force Quit to the bottom panel. I also did the keyboard shortcuts. That works.

I had found this page - [http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/) - discussing gconf editor, but it didn't do anything.

---

### Post by asmoore82 on 2009-05-20
> **PerfectReign said:**
> I had found this page - [http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/) - discussing gconf editor, but it didn't do anything.

This will not work exactly as expected if compiz "Desktop Effects" are enabled.

you can get compizconfig-settings-manager and enable the "Commands" plugin -
it seems to pick up on metacity custom shortcuts fairly automagically,
but it easily has conflicts with other compiz plugins.

I have Ctrl+Alt+Del open System Monitor in both compiz and metacity.
Ctrl+Alt+Esc to xkill works well in metacity but not compiz.

---

### Post by PerfectReign on 2009-05-20
Oh, okay. I didn't even know I had compiz running. (I guess that's the cool window raisng and lowering effect I see.)

I had been trying to get it running on openSUSE/KDE 3.x for some time with no luck.

In any case, I tried out the command now and am able to kill windows.

Thanks all!

---

### Post by rifter on 2010-03-01
> **baseface said:**
> have u tried using the shell?
man kill

Sure you can kill anything with the kill command, but you have to figure out the process and what it is called in ps.

xkill is an X11 application that automagically finds and kills the process chain that leads to a window.  In other words it finds the application that started the window (which is not always obvious) and kills it for you.  It's included on every system that runs X11.

The force quit app works similarly, but for anyone who is looking for xkill, it's at

/usr/bin/xkill

You can add a menu entry for it if you like, the same way that you add any menu item:

Right-click the Applications menu, choose edit Menus
Find a category you want to put xkill in, I put it under Other because for some reason I could not put it under System Tools.

Click "New Item."

Type: Application
Name: Xkill
Command: /usr/bin/xkill

Put whatever you want for Comment; I put:

Comment: kill x11 windows of stuck applications

Click on the little spring in the upper left and choose an icon for it.  This one is decent enough:

/usr/share/icons/Humanity/apps/24/apport.svg

However if you want the skull and crossbones, I found

[http://gnome-look.org/content/show.php?content=74536&PHPSESSID=6](http://gnome-look.org/content/show.php?content=74536&PHPSESSID=6)

It's a 64x64 icon whereas the others in the menu are 48x48, but when you use it in the menu it gets automagically scaled, so no worries.

Just download that using the download link, or whatever icon you want, and once you've saved it to your drive you can copy it as root to 

/usr/share/pixmaps 

(or better yet, make your own directory under that for your custom icons like this), make sure it is owned by root:root and has 644 permissions (that should already happen when you copy it).  Then in the dialog box for picking the icon navigate to the directory you put the icon in, and click open
(or just type the directory name in the text field) and you should see the icon you downloaded there and be able to pick it.

And that should do it. Happy Hacking!

---

