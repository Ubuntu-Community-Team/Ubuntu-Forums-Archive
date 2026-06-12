---
title: "Rehash Maybe? World of Warcraft in Linux"
date: 2007-03-16
forum: Gaming &amp; Leisure
---

### Post by Stormweaver on 2007-03-16
Ok I know this must have been hit several times but I have read so much information I don't know what to go with.

I have a AMD 64 bit Proc.

Running Ubuntu Desktop.

GeForce 6600 GT Vid Card.

Nvidia installed - Doing good so far.

I want to play WoW from this new system, on those specs.  What do I need to do?? Please understand I am new and learning :)

Thank you for any information in advance.

Stormweaver

---

### Post by Peter1234123 on 2007-03-16
Well, what you need is WINE, which you can DL from [www.winehq.com](www.winehq.com) then you click on Download WINE, on the left of the screen, it will give you an option to DL for Ubuntu, do that, then install it, as it shows you. Then rip your files from a preinstalled copy of WoW, or install it with wine, to install it you would copy all the files into the wine folder, under Windows, System 32 and open up a terminal (assuming you are root, I believe it is needed) and type "wine installer.exe", and install it, to the System 32 directory. If you do not have root permissions type "sudo wine installer.exe" if you copied the preinstalled files, copy them to the System32 directory, and type "wine wow.exe" or "sudo wine wow.exe". This should work, btw, get all the MS fonts.

---

### Post by Skia_42 on 2007-03-16
There is a great tutorial by Sammi on installing World of Warcraft [here.]("http://ubuntuforums.org/showthread.php?t=312482&highlight=howto+WoW")

---

### Post by Stormweaver on 2007-03-16
Ok - I am lost ----


I started to follow the tutorial and at step 2 started getting errors about the files not being in repository.. so I checked on their site and followed the link to find out that I have to run a hack to install the 32 bit software on the 64 bit hardware, I got no problem with doing that only the people writing up the hack left alot of info out so here is a cut n paste of that and I need someone to advise me.

---------------------------------

This is a quick hack to install the 32-bit Ubuntu Wine package onto AMD-64 until a working 64 bit package can be made available in the APT repository.

Instructions:

First, you need several 32-bit libraries like ia32libs and lib32asound2 (if you're using ALSA). Install these with apt-get or synaptics.

Then, download the Wine package. You want the latest version available for either dapper or edgy, depending on which one you're using. New versions are released about twice a month.

Save the file to your desktop.

Open a terminal. You may have to edit the command to reflect the version number of the .deb you downloaded. You will need to have the various ia32-libs packages installed already.

cd ~/Desktop 
sudo dpkg --force-architecture -i wine_*_i386.deb

You can delete the .deb file from your desktop when you're done.

UbuntuAMD64 (last edited 2007-03-13 14:09:21 by pD95469ED)

-----------------------------------------------------

Now they say I need several libarys to do this such as the two listed but they don't list whats needed... So before I screw things up here... What do I do now????  This is kinda griping at this point only cause its late here, I've been on this since 7A building this system and installing everything only to not get to enjoy my hobby tonight.  So I am asking if anyone can please help me here, to understand what to do next?


Stormweaver

---

### Post by Stormweaver on 2007-03-17
Giving this a bump in hopes someone will answer today!

Stormweaver

---

### Post by ptesone on 2007-03-17
Dude, I  had the same problem- using a 64bit edgy. . .

found the solution here:
[http://wiki.winehq.org/UbuntuAMD64]("http://wiki.winehq.org/UbuntuAMD64")

once I got wine installed everything went fine WOW works great. . .too bad my account expires in 3 days!

---

