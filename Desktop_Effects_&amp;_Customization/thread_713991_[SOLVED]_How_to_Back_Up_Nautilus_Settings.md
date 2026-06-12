---
title: "[SOLVED] How to Back Up Nautilus Settings"
date: 2008-03-03
forum: Desktop Effects &amp; Customization
---

### Post by mrallaire on 2008-03-03
Hello, I’m new to Linux, and loving every minute of it.  Is there a way to back up settings in Nautilus?  I’ve created new icons for my files and directories, manually positioned files and directories, custom resized some files, and have each directory set to different magnifications.  I need to reformat my hard drive and reinstall Ubuntu, and I don’t want to have to change all the settings again.  I also wanted to copy all these settings to a new user on my computer, so guests have limited access to my files, but can still access my files with the same look and feel that I can.  Furthermore, my dad has a read-only copy of all my files on his computer, and it would also be nice to display them the same way without manually reconfiguring them.  I’ve had to reconfigure the settings manually five times now, and wonder if there is an easier way.  

I’m using a Dell Inspiron 1501 with Ubuntu’s Gutsy Gibbon.

---

### Post by mrallaire on 2008-06-28
Okay, so almost 4 months latter I figured the problem out on my own.  I'm getting better at Ubuntu and Linux.  

You absolutely can back up your nautilus folder/file settings, here is how:

There is a hidden nautilus directory that contains a number of .xml files located at: /home/yourusername/.nautilus/metafiles/file:%2F%2F%2F*.xml These files keep track of your icon locations, custom icons, and position.
One file is created for every directory you have that has custom settings.
You can edit these files with a text editor.
You can make a back-up copy of these files and paste them to restore your  settings as desired.  This is ideal if you are reformating your hard drive and reinstalling Ubuntu, or if your little brother moves your icons around.  

You can also make changes to the files.  If you make a change, make sure you save the file, then in the terminal type "killall nautilus" to quickly restart it.  This is ideal to perfectly line up your icons, as this is done numerically instead of with a mouse.  Make sure you back up your files before altering them.

I hope you find this useful.

---

