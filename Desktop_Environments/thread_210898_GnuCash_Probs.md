---
title: "GnuCash Probs"
date: 2006-07-07
forum: Desktop Environments
---

### Post by nabberuk on 2006-07-07
i've installed gnucash by using the following command;

sudo apt-get install gnucash

now when i go to start it from applications>office>gnucash i get the message at the bottom saying "starting gnucash" but then it just dissapears and nothing else happens. the program doesnt start. anyone have any suggestions as to why this is happening.

many thanks

---

### Post by neighborlee on 2006-07-07
> **nabberuk said:**
> i've installed gnucash by using the following command;

sudo apt-get install gnucash

now when i go to start it from applications>office>gnucash i get the message at the bottom saying "starting gnucash" but then it just dissapears and nothing else happens. the program doesnt start. anyone have any suggestions as to why this is happening.

many thanks

start it from the command line ( applications > accessories > terminal) by entering:
prompt> gnucash

and check for errors. .

cheers
nl

---

### Post by wpshooter on 2006-07-07
I believe that application is on the synaptic downloader/installer.  I believe if it is, that is where I would have done the installation from.

---

### Post by computerease on 2006-07-07
Gnucash can indeed be installed from Synaptic.  Make sure all of the options for the various repositories are enabled.  Gnucash is in a Universe section.  Once all the repositories are activated (there are a number of discussions telling one how to add universe and multiverse to the available community maintained sites) a search for Gnucash will bring up the choices for installation.  If Gnucash is marked as installed (its box will be colored [Color apparently depends on desktop theme] rather than open and/or empty.  If it is listed as installed, right-click on the item and select reinstall.  Then select apply.  If you have to add repositories, be sure to click on Reload after you've finished so that your lists will update.

---

### Post by nabberuk on 2006-07-08
i get the following error when trying to run from the terminal;

gnucash-bin: error while loading shared libraries: libgsf-gnome-1.so.113: cannot open shared object file: No such file or directory


many thanks

---

### Post by rahelvey on 2006-07-08
i nstalled gnucash both ways terminal and synaptic and findly found it located in usr/bin copied the file to desktop and added a launcher and icon now i am quite happy with it.

---

### Post by nabberuk on 2006-07-08
it addedd a shortcut to applications > office when i installed it via apt-get and add/remove. it just wont start.

---

### Post by moaxey on 2006-07-18
I get this error when launching from the terminal

> gnucash-bin: error while loading shared libraries: libgsf-gnome-1.so.113: cannot open shared object file: No such file or directory

:confused:

---

### Post by VirtuAlex on 2006-07-18
Have you tried installing libgsf?```
sudo apt-get install libgsf-gnome-1-113
```

---

### Post by nabberuk on 2006-07-20
once i installed the above libs it past that error, but then i got another.

gnucash-bin: error while loading shared libraries: libgnutls.so.11: cannot open shared object file: No such file or directory

i already had libgnutls12 installed, but i think gnucasg requires what i can only describe as the older version > libgnutls11

so after another apt-get install libgnutls11 if finally starts, even if it is moaning, but meh.

many thanks for the above help!

---

### Post by VirtuAlex on 2006-07-22
Now when you enjoyed resolving dependencies for older version it is time to try Gnucash 2.0.
Have fun.

---

