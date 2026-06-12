---
title: "How to install Gush..."
date: 2005-09-02
forum: Desktop Environments
---

### Post by deiri87 on 2005-09-02
I am trying to install Gush, but being a total noob to the linux world, I'm having troubles.

This is the site where Gush is hosted..
[http://2entwine.com/](http://2entwine.com/)

I wasn't able to find it in the Synaptic, so I think I have to install Gush manually...but I don't know where to start after I downloaded it.  I click on 'install-gush' and nothing happens.  

Please teach me how to install Gush, so I can become more familiar using Linux and doing things the Linux-way.   :grin: 

Thanks!

---

### Post by f1dave on 2005-09-02
in a console, type sudo ./install-gush in the gush install directory.

That will start the install process, which is pretty easy to follow.

---

### Post by f1dave on 2005-09-02
Just as a follow up, whilst it was easy to install I could not get gush to work on my system. However, this could be because I have a number of custom packages installed. Let me know if it works for you.

---

### Post by deiri87 on 2005-09-02
yeah...

I thought I was doing something wrong, but maybe we're in the same situation (though, I highly doubt it)

I finished the installation process and installed it in /usr/bin directory..

I launch the desktop icon and it asks me to choose which firefox profile to use.  I try selecting '2entwine_gush" profile but it says it's already in use.  So i quit firefox and even when I select that as the profile, nothing happens.

---

### Post by deiri87 on 2005-09-02
okay, maybe I should try installing again...and to uninstall it says i need to delete all the gush files, which were installed in /usr/bin.

so now i need some permissions through the terminal to delete all the files.. 

right now, when i click on the Gush icon on the desktop, I just get the animated icon next to the cursor showing that it's loading (when i don't see anything starting up)

---

### Post by f1dave on 2005-09-02
right, thats similar to what i had.

as for permissions, that's where sudo comes in.

sudo rm filename
sudo rm -r dirname

---

