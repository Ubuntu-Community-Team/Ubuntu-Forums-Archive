---
title: "K9Copy and XDVDShrink"
date: 2005-11-20
forum: Desktop Environments
---

### Post by Stambo00 on 2005-11-20
Could I anyone please direct me on how to install either/or these two applications under ubuntu breezy.

---

### Post by Drain on 2005-11-20
[QUOTE=Stambo00]Could I anyone please direct me on how to install either/or these two applications under ubuntu breezy.[/QUOTE]

I just installed xDVDShrink by following [this thread]("http://www.ubuntuforums.org/showthread.php?t=5904&page=2&").  However, it looks like the links from that forum thread don't work as they should - you can click [here]("http://dvdshrink.sourceforge.net/") for the Sourceforge.net page. 

To summarize:
Use the console command "sudo apt-get install" (Or Adept, or Synaptic) to get the following packages: transcode dvdauthor mjpegtools subtitleripper gocr dvd+rw_tools mkisofs libgtk2-perl

Download the latest .tar.gz file from sourceforge.net [here]("http://sourceforge.net/project/showfiles.php?group_id=133818"). (The link from the previous forum thread pointed to an old version of the project)

Unzip the .tar.gz file to your home directory, change directory to it, and type "sudo ./install.sh" . It should check to see if you have all the previous packages installed, and will give you an error message if you don't. 

if all goes according to plan, you should be able to type "xdvdshrink.pl" at the prompt, and you'll have a fairly nice (and unfortunately poorly documented) program with which you can shrink dvds. 

I just got this going the other night, so if you have any good results, I'd like to hear about it. Good luck!

---

### Post by Stambo00 on 2005-11-20
I can't install "dvd+rw_tools" because it doesnt exist in my repositories. What repositories should I be adding to install it?

---

### Post by kitpierce on 2006-03-09
I got xDVDshrink up and running, but was only able to run it in a terminal, which isn't altogether a bad thing.  It works well, but when I open the folder the program created I have no ISO file.  Instead I have the following types of files - AC3, M2V, CHAP, TXT, INFO and a folder named BUILD.  How on earth am I supposed to turn that into a burned backup DVD?  Please help...

BTW, I am running Kubuntu, but I am thinking this is more a file type issue than an OS issue.

---

### Post by StefanoCole on 2006-03-10
> I can't install "dvd+rw_tools" because it doesnt exist in my repositories

Stambo00, the correct package name is "dvd+rw-tools".
You can find it in the main repository!

Stefano

---

