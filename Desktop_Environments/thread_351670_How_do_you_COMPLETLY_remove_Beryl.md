---
title: "How do you COMPLETLY remove Beryl?"
date: 2007-02-02
forum: Desktop Environments
---

### Post by eooon on 2007-02-02
I have tried uninstalling packages from synaptec, but when i reinstall beryl after that it still has my old settings.

My old settings were totaly screwed after the update yesterday and I cant figure out how to get it back to "standard". Beryl is working and all that, but when i "flip the cube" to another workspace it still has all the programs from other workspace on the bottom panel...

So, how do you do a complete Beryl erase (including settings) OR how do you completly reset Beryl settings?

---

### Post by jgeewax on 2007-02-02
Have you tried 

sudo aptitude remove --purge (all beryl packages)

This thread ([http://www.ubuntuforums.org/showthread.php?t=345069](http://www.ubuntuforums.org/showthread.php?t=345069)) says :

sudo aptitude purge beryl
sudo aptitude purge emerald

Hope that helps,

JJG

---

### Post by Suzan on 2007-02-02
Simply rename or delete the .beryl folder in your home-directory.

If you don't do that, you can delete an reinstall beryl as often you wish, it will ever had your old settings.
Same as in most of all other programms.

---

### Post by eooon on 2007-02-02
I have done the purge beryl and emerald, but i cant see the .beryl folder you are talking about and it doesnt show up when i search for it. (However, 170files show up)

---

### Post by miseljt on 2007-02-02
When you go to your /home folder, press ctrl + h. all of the profile .(whatever) folders are hidden.

---

### Post by Suzan on 2007-02-02
Ah ok, it seems, you are very new to Ubuntu.

The most programms store their settings, that a user made, in a folder or document in your home-directory. Most of these are hidden files. You can recognize a hidden folder on the dot at the beginning. For example:

.beryl

Open nautilus, go to settings, mark the option "show hidden files". (Or similar, I don't have an english Ubuntu) Now you can see alle the dot-files and folders in your home-directory.

---

### Post by eooon on 2007-02-02
Thanks, i got it now.

Yes i am very new to linux (like 2 days) and when you mentioned the home dir i went into /home and did ls -a. I had to go into /home/username before i saw the .beryl files.

I removed them and reinstalled Beryl and I now got the standard settings i was after.

Thanks for the help!

---

