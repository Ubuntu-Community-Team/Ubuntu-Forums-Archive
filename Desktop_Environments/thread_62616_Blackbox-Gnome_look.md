---
title: "Blackbox-Gnome/ look"
date: 2005-09-05
forum: Desktop Environments
---

### Post by served on 2005-09-05
How can i make blackbox look similar to Gnome? There should be list on programs and some kind of menu. I dont like to operate that much with console, so i'd like to get a view what is similar to gnome or Windows.

---

### Post by DJ_Max on 2005-09-05
[http://www.boxwhore.org/modules/wfdownloads/viewcat.php?cid=8](http://www.boxwhore.org/modules/wfdownloads/viewcat.php?cid=8)

---

### Post by served on 2005-09-06
Ok! But how can i use themes, i downloaded theme file named: megaspace0.701.tar.gz

How to install or use it?

---

### Post by DJ_Max on 2005-09-06
Try uncompressing it, and see if there's a INSTALL and/or README file.

---

### Post by served on 2005-09-07
now i have a new guestion. I log on in the Gnome session. Im am the only user and administrator, but i cant change files and so one...  :???:  How can i be a administartor and do what ever i like? I even cant correctly edit my mp3 player files pcs my PC says that i dont have a premission :???:

---

### Post by served on 2005-09-07
DAMN IT!!!!! WHAt a F****k i have to do??? I log on session - Gnome
 I checked im administrator there is no more users, but still none
Now i do next. computer - filesystem- right click properties- premissions. Then down there is a line "You are not the owner you cant change these premissions" ???? Like what a f***ck hwo is the owner then? I build my PC and installed ubuntu on it and now it says me that  :???:

---

### Post by varunus on 2005-09-07
OK, served.  No need to yell at Ubuntu.  Its actually doing this on purpose.  Ubuntu HAS no administrator account by default.  This account is called 'root'; it has access to everything.  You, however, are an admin user; you can use the sudo command with *your* password to temporarily become root.

But why are you changing permissions in the filesystem directory anyway?  Please stay inside your home folder, unless you really know what you're doing...You can seriously screw some stuff up, which is why you're restricted like this.  Just tell me what you're trying to do, and i'll show you how to do it with sudo.

---

### Post by served on 2005-09-07
Now thats more like it. 

Im trying to copy blackbox Theme files to the right folders. Im reading it from the blackbox install toc. It says 
" Copy the style files from the styles/ directory in this archive to the
place you usually keep your styles (most likely ~/.blackbox/styles)."

File location is /home/ardi/Desktop/MegaSpace-0.70-1/styles/MegaSpace
i want to copy it to the /usr/share/blackbox/styles folder.

Then i guess i can make other files by my own.

But if i enter to BlackBox mannager then how can i enable skins? Wright now i can see only a blank gray skreen and nothing else. Then with right click i can open the console. What next?

---

### Post by varunus on 2005-09-08
> 
File location is /home/ardi/Desktop/MegaSpace-0.70-1/styles/MegaSpace
i want to copy it to the /usr/share/blackbox/styles folder.

OK, to copy the file like this, there are two methods.

Command line:
sudo cp -R /home/ardi/Desktop/MegaSpace-0.70-1/styles/MegaSpace /usr/share/blackbox/styles/

Then enter your password.
The sudo is to become admin for this command, the -R is to copy recursively (copy all folders)

Easier way, with GUI:

go Applications->Run Application
type "gksudo nautilus" into the command box
Enter your password.

This is a "root file browser".  You can do anything from this file browser.  DO NOT move, rename, or change permissions on most filesystem files, it will mess up your system.  Just use it to drag and drop the style folder to where you want it.

I know almost nothing about blackbox...you'll have to look into that yourself.  (google is your friend.)

---

