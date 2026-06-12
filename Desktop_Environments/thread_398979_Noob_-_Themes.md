---
title: "Noob - Themes"
date: 2007-04-01
forum: Desktop Environments
---

### Post by mshale on 2007-04-01
Hey guys, and gals!

I just downloaded a theme that I can't get installed.  It's called something like Alphacube or something like that.  The file is a .tar.gz, and I don't know what that is, or what to do with it.  Any help? 

Also, what is metacity, and gtk and things like that?  Could someone tell me about any of the stuff on Gnome-Look?

Thanks for all the input!

---

### Post by ComplexNumber on 2007-04-01
a tar.gz is a compression file, just like a zip or rar fle that you may find on windows. 
take the tar.gz package and right click on it, then select 'extract here'. place the extracted contents in .themes in your home directory. note: if you can't see hidden files at the mment, go into the Edit menu in nautilus and select 'preferences'. tick 'show hidden and backup files'.

metacity is a window manager and the theme controls the appearance of the window decorations.

gtk themes alter the shape and colour etc of the various widgets.


what would you like to know about the stuff on gnome-look?

---

### Post by mshale on 2007-04-01
ok, I had tried that before, and the themes didn't shoe up in my themes in system>prefs>themes.  thats why i had to ask.

there are things like splash screens (how do i install them?) and cairo-clock and compiz and beryl themes and things like that.  I would like to know how to install those things, find out what they do and star to mod them to fit me.

Thanks again!

---

### Post by ComplexNumber on 2007-04-01
the reason why is because if you have a look at the metacity theme that you extracted and placed in .themes directory is that that directory contains yet more metacity themes. they need to be extracted


splash screens can be installed by the following:
-place the splash screen somewhere in your home directory
- fire up gconf-editor and go to Edit' in the menu, ehen 'Find. type in "splash" and tcik the 2 tickboxes. look for apps/gnome-session/options/splash-screen. insert the location of where you placed your splash image.

---

### Post by mshale on 2007-04-03
Okiedokie, I did just that, and it doesn't work.  but i know that i put it in the right place because i can go to the logon-customize under system>prefs/admin>Login window and select show splash screen at start up and it works.  Let me make sure i know what the splash screen is.  I have one that is the background of grub when i boot.  then it goes to the ubuntu loading screen with the progress bar.  is that a splash screen?  The one that I'm trying to install is on gnome-look.org  it's you can find it by selecting splash screens>highest rated>(something to do with Fingerprints).  he has install instructions in his post, but they must be incorrect, for I don't get the file mentioned in the install guide when i unpack the download.  Any suggestions?

Thanks!

---

### Post by ComplexNumber on 2007-04-03
admittedly, sometimes its a bit confusing what a "splash screen" is referring to. i usually refer to a splash screen as that  splash screen which is shown immediately after logging in where it shows the various applications and services such as metacity and nautilus loading up. 
i refer to the grub splash screen as the whole of the background immediately after the grub menu where one has selected their operating system. the grub menu(or boot menu) is that where you are given a range of options immediately after the PC has been switched on - eg ubuntu, ubuntu failsafe, windows XP professional, etc.
so basically, it goes from boot menu, then grub splash screen, then login window, then splash screen.

if you're referring to [this,]("http://gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468") that looks like a grub splash screen to me.

---

### Post by mshale on 2007-04-03
Thanks, that helped a bunch!!

---

