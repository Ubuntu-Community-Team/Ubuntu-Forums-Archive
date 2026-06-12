---
title: "How to clean up !"
date: 2009-03-06
forum: General Help
---

### Post by 3wells on 2009-03-06
Clean up ubuntu

Worth a repost... I do not have permission to post in other threads?

This is in response to  a question about 'CCLEANER' - It's old and most defiantly not mine! Kudos to Kyle...

QUOTE >>>>>





"Labels: Applications, Clean up ubuntu, Howto DiggIt! Del.icio.us reddit it! Posted by Kyle on Tuesday, September 11, 2007 at 10:43 PM



If your like me and like to do a bit of spring cleaning, or daily cleaning if your a tweak a-holic, these tips will help you clean up your ubuntu installation, enjoy.

Tip #1 - Getting rid of Residual Config packages



In Synaptic Package Manger, there is a built-in feature that gets rid of old Residual Config packages. Residual Config packages are usually dependency packages that are left behind after you uninstall a package from your machine. To use this feature, go to System > Administration > Synaptic Package Manager. On the bottom left hand corner of the window, click the Status button. In the list above the Sections, Status, Search, and Custom buttons, you should see the following text:



Quote:

Installed

Installed (local or obsolete)

Not installed

Residual config

Click on the "Residual config" text. (If the "Residual config dialogue does not appear, that means you do not have any Residual Config packages on your machine and you can skip down to Tip #2.) Do you see the packages that popped up in the window on the right? Those are the Residual Config packages. To get rid of these pests, click on the box to the left of the package name and select "Mark for Complete Removal". After you have done that for all of the Residual Config packages, look at the top of the Synaptic Package Manger window. Do you see the green check mark with the text "Apply" right under it? Click that button, and you'll flush all those Residual Config packages down the toilet!



Tip #2 - Getting rid of partial packages

This is yet another built-in feature, but this time it is not used in Synaptic Package Manager. It is used in the Terminal. To access the Terminal, go to Applications > Accessories > Terminal. Now, in the Terminal, key in the following command (or you can just copy and paste from here):



    sudo apt-get autoclean







Enter your password when prompted and press Enter. See the package names that appeared in the Terminal? Those were partial packages that have just been deleted. Say goodbye! That's it! This command deletes the not-so-fully-downloaded packages that you acquire when a package that is being downloaded is suddenly cancelled. This is my favorite little trick when it comes to getting rid of junk files.



Tip #3 - Getting rid of unnecessary locale data

For this tip, you need to download the "localepurge" package found in Synaptic Package Manager. "localepurge" is just a simple script to recover diskspace wasted for unneeded locale files and localized man pages. It will automagically be invoked upon completion of any apt installation run.



To open Synaptic Package Manager, follow the instructions in Tip #1. After opening up Synaptic Package Manager, click the Sections button on the bottom left hand corner of the window, if it is not already clicked. Next, at the top of the Synaptic Package Manager window, click the Search button. In the search window, key in the following text :



    localepurge



Did the "localepurge" package popup in the package window? It probably did, unless you do not have the correct Repositories. Now, click on the box next to the "localepurge" package name. Click on Mark for Installation. Now click the Apply button at the top of the window and wait for the downloading and installing of the "localepurge" package to finish. Once it is done, a new window should popup that has a bunch of abbreviations on it. for example:



    en

    fr

    po

    sp

    ka

    etc...



You want to select the abbreviation of the language that you speak, or use with Ubuntu, ignoring the capitalized ones. For example, I speak english, so I would select the "en" abbreviation. A french speaker would select the "fr" abbreviation. So on and so forth... Then click next. All done!



Tip #4 - Getting rid of "orphaned" packages - For this tip, you need to download the "deborphan" package found in Synaptic Package Manager. "deborphan" finds "orphaned" packages on your system. It determines which packages have no other packages depending on their installation, and shows you a list of these packages. It is most useful when finding libraries, but it can be used on packages in all sections...



To open Synaptic Package Manager, follow the instructions in Tip #1. After opening up Synaptic Package Manager, click the Sections button on the bottom left hand corner of the window, if it is not already clicked. Next, at the top of the Synaptic Package Manager window, click the Search button. In the search window, key in the following text :



Quote:

deborphan

Did the "deborphan" package popup in the package window? It probably did, unless you do not have the correct Repositories. Now, click on the box next to the "deborphan" package name. Click on Mark for Installation. Now click the Apply button at the top of the window and wait for the downloading and installing of the "deborphan" package to finish. Once that is done, open up the Terminal. Instructions for doing that are located in Tip #2. After you have gotten the Terminal open, key in the following command (or copy and paste from here):



Code:



    sudo deborphan | xargs sudo apt-get -y remove --purge







Enter your password when prompted and press Enter. See the package names that appeared in the Terminal? Those were orphaned packages that have just been deleted. Say goodbye! This is my second favorite way of dealing with junk files.





Tip #5 - Adding a "Find orphaned packages" to Synaptic Package Manager - This is not really much of a tip on how to get rid of junk files. It's more like adding a "deborphan" shortcut to Synaptic Package Manager so that you don't have to use the Terminal to find "orphaned" packages.



Please note: You must have the "deborphan" package installed or else this will not work.



To start this out, open up Synaptic Package Manager with the instructions from Tip #1. Now, at the top of the Synaptic Package Manager window, click the Settings button, followed by the Filters button. In the Filters window, on the bottom left hand corner, push the New button. You can name the new Filter if you like, but it is not necessary. I named mine "Orphaned". With your new Filter selected, in the "Status" tab on the right, click the Deselect All button. Next, check the "Orphaned" option under the "Other" category. Then click the OK button.



To use this new filter, click the Custom button on the bottom left hand corner of the Synaptic Package Manager window. You should see the following text, or something similiar :



Quote:

Broken

Marked Changes

(Whatever you named your "deborphan" Filter)

Package with Debconf

Search Filter

Click on the "(Whatever you named your "deborphan Filter)" text. Do you see the packages that popped up in the window on the right? Those are the "orphaned" packages. To get rid of these buggers, click on the box to the left of the package name and select "Mark for Complete Removal". After you have done that for all of the "orphaned" packages, look at the top of the Synaptic Package Manger window. Do you see the green check mark with the text "Apply" right under it? Click that button, and you'll get rid of all the "orphaned" packages forever (Probably)!"

3

---

### Post by bodhi.zazen on 2009-03-06
What problems are you haveing posting ?

At any rate, for any interested, please see :

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

    [http://ubuntuforums.org/showthread.php?&t=140920](http://ubuntuforums.org/showthread.php?&t=140920)

    [http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html](http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html)

---

