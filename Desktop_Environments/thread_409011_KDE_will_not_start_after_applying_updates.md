---
title: "KDE will not start after applying updates"
date: 2007-04-14
forum: Desktop Environments
---

### Post by vikram on 2007-04-14
Hi I am using Kubuntu 6.10. I applied a few updates and now KDE wont start. The message I get is 
"could not start kdeinit check your installation"

then another dialog box :

error setting interprocess communication could not read network connection list :

/hone/username/.DCOPServer_mc-name_0. 
Please check that the dcopserver program is running.

Note: 

tried reinstalling kdebase. 
installed gnome desktop, removed all kde packages and reinstalled them
changed permissions on home/.kde folder to 777


still the same - login fails and i am redirected back to kdm. i dont think this is an X server config issue since i can log onto GNOME.

Please help !

---

### Post by smurfit on 2007-07-04
I have this same problem.

Did an upgrade now I get the above error.  This is my work machine so any help appreciated.

I have searched on here all yesterday afternoon and this morning, tried a few things that other posts suggested but no good.

Help me please...... :)

---

### Post by sahilbhrany on 2008-03-02
simillar thing happened to me as well
try this  
sudo apt-get remove language-pack-kde-en

[http://ubuntuforums.org/archive/index.php/t-695073.html](http://ubuntuforums.org/archive/index.php/t-695073.html)

---

