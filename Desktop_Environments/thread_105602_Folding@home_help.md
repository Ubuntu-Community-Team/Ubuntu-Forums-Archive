---
title: "Folding@home help?"
date: 2005-12-18
forum: Desktop Environments
---

### Post by ionizd on 2005-12-18
I recently downloaded the F@H executable from the Stanford U. website. I'm having trouble figuring out how to make the program run automatically and without having an open terminal at all times. Please imagine you are speaking to an idiot and go step by step.
Thanks!

---

### Post by ubuntu27 on 2005-12-18
Does any Kubuntu User know this?  I know you do! yeah, you, the oen reading this!! :P

I'm using Ubuntu, so I don't have any idea of Kubuntu...

---

### Post by jaon on 2005-12-19
Hi There!
I'm kind of new to Kubuntu as well, but I've used KDE before and I've used the protein folding program I think you're talking about.  So I'll see if I can help.

Okay, if you want to get something to run each time KDE starts, the easiest way is to put it in a folder called "Autostart".  Autostart is a hidden folder buried in your home directory, and anything you put in there, KDE will automatically open when you log in.

So, to get there, open Konqueror (the file browser) and in the address bar, type in this address:
/home/jason/.kde/Autostart/
replacing "jason" with whatever your username is.
Now this folder will probably be empty, unless you've put something in here already or another program has put something in there already.

Okay, basically, the idea is we need to create a link (a shortcut) to the protein folding file you downloaded (Protein Folding.exe).  So right click in the autostart folder you just opened, hover over "create new" and then click on the "Link to Application" button.

This will bring up a window which lets you enter some information.  The window has several tabs with different options you can choose for making the link.  The first tab you see when you start it up is called "general".  This just lets you choose the name of the link you're making and the icon.  Since the link you're making should open automatically and you'll never actually need to click on it, the name and icon aren't important.  Just call it "folding" and don't worry about changing the default icon.

Now click on the tab named "Application".  This tab has all the details of the application that you want to start up.
Here's what I filled in:

Name: Protein Folding
Description: Something to put my unused megahurtz to good use
Comment: 
Command: "/home/jason/Protein Folding.exe"
Work Path: "/home/jason/ProteinFolding"

For the "command" textbox, you can click the browse button next to it and that will let you find the exe file.  It's essential that you make sure this is right if you want KDE to start the program when you log in.
One thing I noticed is that the program will dump a whole lot of files in the directory it runs in.  For example, if I have the "Protein Folding.exe" file on my desktop, and I run it, it will dump a whole bunch of files on my desktop.  I found this a bit annoying, so what I did is created a folder called "ProteinFolding" in my home directory (or you could put it on your desktop or anywhere).  I want "Protein Folding.exe" to put all of it's files in that folder, and I can do that by setting the work path to the folder I created.  You can click the little icon next to the text box to let you browse your folders until you find the one you want.

Now click okay, and there should be an icon in the autostart folder called "folding.desktop" or something similar.
Just to make sure it works, click it.  If it's done correctly, you shouldn't see any windows pop up or anything.  It should be running in the background though, invisibly.  To check that it is, press Control and Escape at the same time.  This brings up a list of all the programs you have running.  If you have a look through all of these there should be one called "Protein Folding.exe" or something.  That means it's running.

If you really want to be sure it's working you can log out and log back in and check it's working... but i wouldn't bother.

I hope this makes sense...
I'm kind of new to this myself, so I'm not sure if there's an easier way...
If it doesn't work for you, or if you want it to behave slightly differently, post here and hopefully I (or someone else) will be able to help some more.

See ya!

---

