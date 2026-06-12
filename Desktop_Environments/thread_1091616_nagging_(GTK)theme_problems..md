---
title: "nagging (GTK)theme problems."
date: 2009-03-09
forum: Desktop Environments
---

### Post by nightrider.36 on 2009-03-09
Hello all,

I've looked everywhere I can for a solution and I'm out of options.  I'm using Ubuntu 8.10.

There have been a few themes that return the following message when I drag them to the *Appearance Preferences* dialog box.

**"This theme will no look as intended because the required GTK+ theme engine is not installed."**

I've edited the "gtkrc" file and filled in "pixmap" where the quotes were empty thinking that maybe that would work--it was suggested on another post. ```
{ engine "_pixmap_" {yadda-yadda}}
```, does nothing even after I restart, warm and cold. I've also tried looking for these so-called, GTK engines and no dice...  I never used to have this problem with *any* theme I installed in the past. It seems to be an issue in 8.10--or at least, that's how it seems.

Also, where are the themes stored? I can't find those either.  I can't delete the malfunctioning theme because I get a message, **Installation for them "XXXXXX" failed. Can't move directory over directory**.

I could at least navigate to the folder and physically remove it. 

Thanks.

---

### Post by paullinux on 2009-03-09
> **nightrider.36 said:**
> Hello all,

I've looked everywhere I can for a solution and I'm out of options.  I'm using Ubuntu 8.10.

There have been a few themes that return the following message when I drag them to the *Appearance Preferences* dialog box.

**"This theme will no look as intended because the required GTK+ theme engine is not installed."**

I've edited the "gtkrc" file and filled in "pixmap" where the quotes were empty thinking that maybe that would work--it was suggested on another post. ```
{ engine "_pixmap_" {yadda-yadda}}
```, does nothing even after I restart, warm and cold. I've also tried looking for these so-called, GTK engines and no dice...  I never used to have this problem with *any* theme I installed in the past. It seems to be an issue in 8.10--or at least, that's how it seems.

Also, where are the themes stored? I can't find those either.  I can't delete the malfunctioning theme because I get a message, **Installation for them "XXXXXX" failed. Can't move directory over directory**.

I could at least navigate to the folder and physically remove it. 

Thanks.

Open Nautilus (the filebrowser), under 'view' check 'show hidden files'.  In your home-directory you will find the '.themes' file (notice the dot!!) .  In that file you will find all the themes that are installed.  Just remove the unwanted files.  

You may have to start the appearance-window again- sometimes even twice - before the theme is disappeared...

As to why you get the message in the first place I have no clue - I have the same problem here - but this is a workable solution.  ;)

---

### Post by CowzRule on 2009-03-09
Try installing these 2 engines
```
sudo apt-get install gtk2-engines-murrine gtk2-engines-pixbuf
```
and try installing your theme again. If you still get the error, try and find what engine the theme uses and seach through synaptic package manager.
The 2 engines I suggested you install seem to be the most popular.
Hope this helps.

---

