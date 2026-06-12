---
title: "gimp"
date: 2006-02-05
forum: Desktop Environments
---

### Post by ESPOiG on 2006-02-05
i installed gimpshop a while ago and started a thread with my problems but now im stuck again

i cant save as xpm format

so i did these things
apt-get remove gimp
dpkg -r gimp
dpkg --purge gimp

then i installed gimp again 
apt-get install gimp

but still it loads as gimpshop

plz anyone help :neutral:

---

### Post by Perfect Storm on 2006-02-05
Is gimpshop named exactly as the same as normal gimp (the package)?
If so you might when uninstall gimpshop remove .gimp-2.2 from your home directory manually.

---

### Post by ESPOiG on 2006-02-05
gimp shop is gimp that is the problem...  i dunno how to unistall it and wen u type gimp in terminal it just runs gimpshop

---

### Post by ESPOiG on 2006-02-05
i removed the .gimp-2.2 directory and it still loads as gimpshop ?

---

### Post by enyaw on 2006-06-16
[QUOTE=Artificial Intelligence]Is gimpshop named exactly as the same as normal gimp (the package)?
If so you might when uninstall gimpshop remove .gimp-2.2 from your home directory manually.[/QUOTE]

When running gimp for the first time, it states a sub-directory of the home directory is created i.e,; .gimp-2-2.  I can't find this sub directory.  Gimp seems to work correctly.  Can you show the way here. :?:

---

### Post by Perfect Storm on 2006-06-16
Fire up nautilus and in the view tab select 'show hidden'. 
or 
ls -a
in the terminal.

---

### Post by enyaw on 2006-06-16
[QUOTE=Artificial Intelligence]Fire up nautilus and in the view tab select 'show hidden'. 
or 
ls -a
in the terminal.[/QUOTE]

Thanks a bunch.  :D   Apparently your intelligence is NOT artificial.   Although, apparently, I remain in the newbie camp.  One other thing:   When I fire up GIimp Help it indicates that Gimp has a Welcome screen; my application does not.  Gimp seems to work just fine.  What gives:?:

---

### Post by Perfect Storm on 2006-06-17
Check if the gimp help package is installed (in synaptic package manager).

---

### Post by enyaw on 2006-06-22
[QUOTE=Artificial Intelligence]Check if the gimp help package is installed (in synaptic package manager).[/QUOTE]

Here's what Synaptic Packager Manager indicates as installed:

gimp
gimp-data
gimp-helpbrowser
gimp-help-common
gimp-help-en
gimp-python
libgimp2.0

There are other esoteric  lib such as libglib2.0-0 which, I don't have a clue as to there connection to gimp.

Thanks for your help.8)

---

### Post by Perfect Storm on 2006-06-22
Install the help-common and gimp-help-en

---

### Post by enyaw on 2006-06-22
[QUOTE=enyaw]Here's what Synaptic Packager Manager indicates as installed:

gimp
gimp-data
gimp-helpbrowser
gimp-help-common
gimp-help-en
gimp-python
libgimp2.0

There are other esoteric  lib such as libglib2.0-0 which, I don't have a clue as to there connection to gimp.

Thanks for your help.8)[/QUOTE]

I did as you suggested; I reinstalled both with no change.  The Gimp seems to work well, so I don't know if it's necessary to have a welcome screen.  However, judging from the various applets shown,  when help is opened it would appear the welcome applet would offer some utility.

Thanks for your help. 8)

---

