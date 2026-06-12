---
title: "How to install program?  (Sunbird calendar 0.9)"
date: 2009-04-13
forum: General Help
---

### Post by JEBB on 2009-04-13
On my Dell Mini 9 Ubuntu 8.04's Add/Remove only installs version 0.7 of the Sunbird calendar.  I want to download and install the current version, 0.9.  How do I go about that?  Thanks.

---

### Post by tjwoosta on 2009-04-13
[http://www.mozilla.org/projects/calendar/sunbird/]("http://www.mozilla.org/projects/calendar/sunbird/")

download the linux version

unpack

click sunbird executable

---

### Post by JEBB on 2009-04-13
My goal is to replace version 0.7 with version 0.9.  

I downloaded the installer, double clicked on it, hit the extract button and now I have on my desktop, in addition to the .tar.gz box icon, a folder named sunbird.  Now what do I do?  Thanks.

By the way, on doing a search, I found several other sunbird folders.

---

### Post by tjwoosta on 2009-04-13
you simply go into the folder named sunbird and double click on the executable file named sunbird


there is no install process

you simply extract the .tar.gz and run the executable to open sunbird


you can put the folder wherever you want then create a launcer on your desktop or wherever that points to it


as for removing your old sunbird version you can just remove it through synaptic package manager

---

### Post by JEBB on 2009-04-13
There are four files that are executables.  Two of the files have in their name sunbird.  Then one named only 'sunbird'  is, inlist view, listed as a shell script and did nothing when I double clicked on it.  The one labled sunbird-bin is listed as an executable and did start the program, so I have to assume it is what you called the executable.    

In which folder are programs usually placed?  I would like to have the ability get the new sunbird version listed in the Applications menu.  The old version is currently listed there.

---

### Post by Johnny19734 on 2009-04-13
Here you go Bro,

From now on look for .deb files. Stands for Debian.(Which is the back bone of UBBY) Just double click and your done!

[http://www.getdeb.net/app/Sunbird](http://www.getdeb.net/app/Sunbird) 

Pe@ce - JJ

---

### Post by crossedout on 2009-04-14
> There are four files that are executables. Two of the files have in their name sunbird. Then one named only 'sunbird' is, inlist view, listed as a shell script and did nothing when I double clicked on it. The one labled sunbird-bin is listed as an executable and did start the program, so I have to assume it is what you called the executable.
Choose the sunbird within the main 'Sunbird' directory.

> In which folder are programs usually placed?
Generally, I like to place programs in /opt.  But that's just me.

> I would like to have the ability get the new sunbird version listed in the Applications menu. The old version is currently listed there.
Right-click the main menu to edit menus and navigate to where Sunbird .7 is located.  You can either edit it or uncheck it to remove it from the main menu.  If you choose to uncheck it, you will need to select 'New Item'.
Type = Application
Name = Sunbird 0.9
Command = Location/Where/Sunbird/IsLocated
Example: /opt/sunbird/sunbird
Comment = Sunbird Calendar Program (optional & not necessary)
Addtionally, click the icon to set your icon to the traditional Mozilla Sunbird icon.  In the above example it is located in /opt/sunbird/icons

Good Luck!
-Xout

---

### Post by JEBB on 2009-04-14
I used Add/Remove to remove Sunbird 0.7 and then, following Johnny's suggestion I tried to install the deb file but I got this error message:  dependency is not satisfiable: libgtk2.0-0

Now what do I do?  

Thanks.

---

### Post by Johnny19734 on 2009-04-14
Goto Synaptic packge manager and add that dependency(System\Administration\Synaptic packge manager)then try again. :)

---

### Post by Johnny19734 on 2009-04-14
[IMG]http://www.debianadmin.com/images/syn/1.png[/IMG]

---

### Post by JEBB on 2009-04-15
Sunbird 0.9 does not show up in the lists.  It appears to not be in the Ubuntu collections.  But I have it on my desktop already decompressed.  Please look at my questions again.  

I don't understand what you are telling me to do: add a dependency.   

Thanks

---

### Post by JEBB on 2009-04-15
I went to Synaptic Package Manager and searched for libgtk2.0-0 and it turned up two items that I checked and installed.  Upon double clicking the .deb package it gave me the same error message:  dependency is not satisfiable: libgtk2.0-0.

---

### Post by Johnny19734 on 2009-04-15
Not Sure, make sure you have all updates installed. Make sure the old Sunbird Calander is removed(Look in Synaptic and make sure there isn't any remains of the old one.) Other than that I really dont know. I'll do some research. You as well. Google the error message.

---

### Post by wmichaelb on 2011-07-20
Thanks for this post! Lightning currently won't run on AMD64 Thunderbird 3.1.11, so I was caught in a box. One last step: Sunbird automagically inserts a sunbird folder into /.mozilla, so one must finally change ownership to be able to create a userfile:

sudo chown -R yourusername /home/yourusername/.mozilla/sunbird

and then everything works. My biggest reason for preferring Sunbird/Lightning is the FG plugin, which uniquely among calendar programs allows one to change the size of the fonts to something reasonable for my aged eyes. I delayed upgrading from 9.04 for that reason primarily.

Have a great day!

---

### Post by SeijiSensei on 2011-07-20
64-bit builds here: 
[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/contrib/linux-x86_64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/contrib/linux-x86_64/)

---

