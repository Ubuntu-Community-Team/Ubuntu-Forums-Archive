---
title: "Doom 3 And Quake 4 Help!!!!!!!!!!!!1"
date: 2007-04-22
forum: Gaming &amp; Leisure
---

### Post by metalblitz84 on 2007-04-22
I am having trouble instalilng these in linux. I am logged in as root and have saved all the necessary files from the cd into the base folders. when I download the installer and go into the terminal and type the command "sudo sh doom3-linux-1.3.1302.x86.run", it says it can't open it. When I myself actually click on the installer from the text editor, it says "Could not open the file /usr/local/games/doom3/d…-linux-1.3.1.1304.x86.run.". How do I fix this and get the games installed on this. I'm going nuts trying to figure it out. Any help would be greatly appreciated. Thanx!!!!!!!!!!!!!!!!!!!1

---

### Post by aidanr on 2007-04-22
is it executable? right click -> properties -> permissions

---

### Post by lakersforce on 2007-04-22
> **metalblitz84 said:**
> I am logged in as root and have saved all the necessary files from the cd into the base folders

Logging in as root is a big no-no. And you say you use sudo? That should not be neccesary when you are logged in as root. I see that you have saved your *.run files in /usr/local/games/doom3/? That's an odd place to save them.

Log out. Log in as your normal user. Save the the *.run files to your /home/username/ folder. Run the files with a "sh <your filename here>.run" and copy the required content from your original cd's to the appropiate places (it is described how-to and what in the readme files).

---

### Post by metalblitz84 on 2007-04-22
I clicked on allow "executing files as programs"...now what?

---

