---
title: "What to do... What to do... ?"
date: 2012-07-31
forum: Desktop Environments
---

### Post by cabatex on 2012-07-31
I have a story pages long about my recent Ubuntu experience.  I don't want to bore any one though.  So here it is...  I completely jacked my desktop.  I had to install Kubuntu to get logged in to a working desktop.  I just want to get back to what I had which was Gnome.  I believe the only way to do this is to start from scratch.  Unless someone has a suggestion on recovery without it.  I don't want to lose everything I have on my system so I will have to make a backup.  The thing is I don't know how to backup without getting all the junk in there that ruined my desktop in the first place.  Can someone point me in the direction of a resolution either a good backup for kubuntu to get back to regular ubuntu via clean install or recovery steps to do the same without fresh install and restore.  Thanks.

---

### Post by randywilharm on 2012-07-31
> **cabatex said:**
> I have a story pages long about my recent Ubuntu experience.  I don't want to bore any one though.  So here it is...  I completely jacked my desktop.  I had to install Kubuntu to get logged in to a working desktop.  I just want to get back to what I had which was Gnome.  I believe the only way to do this is to start from scratch.  Unless someone has a suggestion on recovery without it.  I don't want to lose everything I have on my system so I will have to make a backup.  The thing is I don't know how to backup without getting all the junk in there that ruined my desktop in the first place.  Can someone point me in the direction of a resolution either a good backup for kubuntu to get back to regular ubuntu via clean install or recovery steps to do the same without fresh install and restore.  Thanks.
"the junk in there that ruined my desktop in the first place."

There are **other** explanations for this. Don't assume it was something on your desktop that is causing problems. Sometimes problems happen because of the PC (or video card) you are using.....other than that, you can always reinstall the desktop if this happens again:

sudo apt-get install ubuntu-desktop


This resets the X server:   sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by miegiel on 2012-07-31
@**[COLOR="DarkOrange"]cabatex[/COLOR]**, if you set your file browser (nautulis I presume) to show hidden files, you'll see hidden directories like *.gconf .config .gnome2 .local*, etc. Make sure you don't restore those, though you might want to restore hidden directories like .mozilla for example. Your user settings are stored in these directories. System wide settings are stored in the directories in */var/* (not to be confused with system configuration files in */etc/*).

You could also try deleting some of the gnome related hidden directories in your home directory and booting up again (probably best to do that while running from a liveCD or liveUSB). It might save you the trouble of reinstalling.

---

### Post by cabatex on 2012-08-01
Randy,

I didn't mean its actual junk somebody worked their butt of to design build test and distribute.  I just meant not seeming to work for the purpose I desired.  I did have a hard drive crash after some updates came out a couple weeks back and lost grub.  I added grub to this device and it seems like right after that I started having some desktop troubles and started tweaking the desktop.  I should have had a backup which is on me.  Its good that there is a community of people out here to help people that have issues.  Also I did try to run that ubuntu-desktop before I installed kubuntu but it didn't restore as I had hoped.  Do I need to run the two commands you posted in succession to achieve results?  Thanks

---

### Post by cabatex on 2012-08-01
Would you suggest removing all gnome packages?  I read today that compiz and gnome don't work well together.  I have tried to remove both of these but it didn't seem to help before I installed kubuntu.  Also these hidden gnome files in home... ? Is that at the /home directory or will those be in /home/<username>? and just anything with gnome or something specific?  Thanks.

---

### Post by black veils on 2012-08-01
its** /home/username  **ie. just go to the folder which says your name (from the left pane), and press** Ctrl + H** to show hidden files and folders, these are most of the app configurations, so you should make a backup of your email, web browser, instant messenger and anything else important you want to keep. dont forget to copy your personal files also (documents, pictures etc) !

if you cant get onto your system, use a live cd:

1.  connect a usb flash drive

2.  open the file manager and find your system in the left pane

3.  look for a **home** folder, then your username

4.  copy-paste what you want, to the flash drive.

5.  it will state about not being able to copy symlinks, read and accept accordingly to continue.

---

### Post by cabatex on 2012-08-01
So I decided after some searching to remove Gnome.  After I was using Kubuntu I really liked it.  So I used the command

sudo apt-get --remove purge gnome*

I don't recommend using this without a current backup.  I didn't have issues myself just warning.

Thanks for the help.

---

