---
title: "Quistion before updating Gnome"
date: 2006-03-16
forum: Desktop Environments
---

### Post by Patrick on 2006-03-16
Hello,

The new version of Gnome is there:p  , but becasue i'm a big N00B , i wanted to ask if there are some things i need to take care of before i update to the new version?? Are ther some steps to take?

---

### Post by Blairboy on 2006-03-16
Which version are you running now?

---

### Post by backupdevice on 2006-03-16
Woeps. i did something wrong with updating my password, so i had to make a new profile. So i'm the new alias of PATRICK

The Gnomeversion i use now is the one thats deliverd with Breezy

---

### Post by Klejs on 2006-03-16
If I were you I would either upgrade to Dapper or wait til Dapper is released, you will find an new version of our beloved Gnome there :D

---

### Post by backupdevice on 2006-03-16
mkay, that would be the smartest thing to do. 

Any idea when the final version of dapper will be released?

---

### Post by Blairboy on 2006-03-16
Yeah, dapper's coming out in april which will contain gnome 2.14.  It's not that long now :D.  If you really want dapper with gnome 2.14 now, just do this:

quoting tseliot

If you want Dapper you have to install Breezy

Then type:

sudo gedit /etc/apt/sources.list

Replace the word "Breezy" (all of them) with the word "Dapper"

Make sure you haven't any backport enabled (they are disabled by default)

Save the file and exit.

Type:

sudo apt-get update

sudo apt-get dist-upgrade

When it finishes you have to restart your computer and you will have your Dapper

---

### Post by backupdevice on 2006-03-16
Ok, then i will wait :) 

thx for the repleys guys!! \\:D/

---

