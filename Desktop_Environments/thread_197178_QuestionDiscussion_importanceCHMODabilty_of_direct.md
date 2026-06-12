---
title: "Question/Discussion: importance/CHMODabilty of directory /opt"
date: 2006-06-15
forum: Desktop Environments
---

### Post by donmiguel on 2006-06-15
Hi dear Ubuntu-Users!

I've been using Ubuntu now since 3 months and i'm getting to know this system better and better. Tough, a thing I break my head about is the directory in the file-system /opt. There i have several "hand-installed" programs like Thunderbird, Skype, Google Earth & others... and well this directory is write-protected for normal users. So i have to start most of these programs with sudo (like: sudo googleearth) because the file in the $PATH redirects to /opt/whatever. 
I am also aware of the fact that it isn't safe nor smart to chmod file-system directories because of evident reasons... but somehow i tink a lot about changin the rights of /opt so that it isnt necessary to sudo these Programs.... is it really important that it is writeprotected?

So much for my concern. I would be very pleased if some experienced users of linux systems could tell me why it wouldnt be that big a deal or just the contrary...

Greets
donmiguel

---

### Post by aysiu on 2006-06-15
You shouldn't need write access to the /opt directory in order to run the programs there without using *sudo*.

Writing and executing are two completely different things.

Root can own a directory. It can be the only user with write access. But usually programs also have read and execute access for regular users, if those programs are installed correctly.

For example, if you used Nanotube's script to install Firefox or if you used the Wiki guide or Automatix, Firefox would live in /opt, but a symlink is created to /usr/bin/firefox, and it's executable for regular users.

Can you post the output of these commands? ```
cd /opt/firefox
ls -al
```

---

### Post by donmiguel on 2006-06-15
yeah right. i formulated a bit wrong.. :) i think i should be able to regulate that.. but another concern is in this case the write permissions of the programm (the unsafe part of the whole problem :)... f.ex. can you delete a search engine of the search bar in the upper right?


EDIT: for this you need this extension: [https://addons.mozilla.org/extensions/moreinfo.php?id=1563](https://addons.mozilla.org/extensions/moreinfo.php?id=1563)

---

### Post by aysiu on 2006-06-15
The search plugins are a two-part deal.

There are the search plugins that come standard--those you won't have write access to, and they live in /opt/firefox/searchplugins

Then there are the ones you manually add. Those live in /home/donmiguel/.mozilla/firefox/*profilename*/searchplugins, and you will have write access to that.

So what I do is usually just delete all the standard ones: ```
sudo rm /opt/firefox/searchplugins/*.gif
sudo rm /opt/firefox/searchplugins/*.src
``` and then just install my own locally.

---

