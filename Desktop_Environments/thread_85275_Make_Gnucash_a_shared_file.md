---
title: "Make Gnucash a shared file?"
date: 2005-11-02
forum: Desktop Environments
---

### Post by Darrin on 2005-11-02
I have a login for my wife and I. I recently installed Gnucash and created an application menu for it. I had to recreate it again on my wifes login. It doesnt seem to share the same database. I want to set it up so whatever I enter in on gnucash it will show up on her gnucash also and the other way around. How is this done?
Thanks

---

### Post by sethmahoney on 2005-11-03
Log into your account, open up Home in nautilus, right-click on your Gnucash file, go into permissions, and set it to allow her to have permsision to read and edit the file.  Log out, log into her account, open up Gnucash, and then set it to automatically open the file /home/YourUserName/YourGnucashFile (where "YourUserName" and "YourGnucashFile" are replaced with your user name and your Gnucash filename, respectively).  You should now be sharing the same Gnucash file.  Hope this helps!

---

### Post by Darrin on 2005-11-04
I have a gnucash file in /usr/lib/gnucash. I go to set the permissions of this file for others to read,write, and execute? or is there another file withing the gnucash file I need to change?
Thanks

Edit: I also noticed I have a gnucash file in /usr/share. Im confused as to which one to mess with?

---

### Post by SickTwist on 2005-11-04
To view your home folder, click on "Places" --> "Home Folder". You only need to share the folder/file in which you saved your account information. When you first ran gnucash, did it ask you where to save the file and what to name it?

EDIT:

I just ran gnucash and noticed it stores information in "~/.gnucash". Here are the commands to execute from a terminal to share this between you and your wife:
```
chmod o+x ~
chmod -R o+rwx ~/.gnucash
sudo ln -sf ~/.gnucash /home/your_wife's_username
```

Try that out and let us know if it works.

---

### Post by Darrin on 2005-11-04
I dont see anything Gnucash related in my home folder. I dont hav anything entered in gnucash yet either so maybe I didnt create a directory for a save file yet?

---

### Post by SickTwist on 2005-11-04
That could be it. Most programs store each user's preferences and data in his/her home folder. Sometimes it is in a hidden file or directory (any filename that starts with a period is hidden). To view hidden files, start nautilus ("Places" --> "Home Folder") and click "Show Hidden Files" under the "View" menu.

---

### Post by Darrin on 2005-11-05
I tried your suggestion. Heres the response in the terminal I get.
```
ln: `/home/staci/.gnucash': cannot overwrite directory
```
Any other thoughts?

---

### Post by Darrin on 2005-11-05
I got it working. I just right clicked on my folder where I keep my saved gnucash data. Changed ther permissions for others to read,write,execute.  It works now. We now share the same data. 
Thanks :)

---

