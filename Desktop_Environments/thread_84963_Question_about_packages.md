---
title: "Question about packages"
date: 2005-11-01
forum: Desktop Environments
---

### Post by escobar on 2005-11-01
I recently re-installed Kubuntu Hoary due to issues I've had with Breezy. I've enabled all the extra repos per the Ubuntu Guide, including the backports. 

I have had difficulty with Firefox and Java. Concerning Firefox, the version available is 1.0.7, but requires a bunch of gnome libraries to install. My memory is a little fuzzy so I don't recall this being required, though I could be wrong. Is this normal? I'd like to avoid having to install the gnome libraries if possible. 

Also where'd Java go? Searching for either 'j2re, or 'j2se' yields no results. I haven't found w32codecs either but I installed them from the mplayer website so no biggie, just curious as to why so much stuff appears to be gone.

Other than that, I'm happy to be back with Hoary. After using Breezy it feels a little dated but I'll live. Thanks.

---

### Post by Alexander Kirillov on 2005-11-01
[QUOTE=escobar]I recently re-installed Kubuntu Hoary due to issues I've had with Breezy. I've enabled all the extra repos per the Ubuntu Guide, including the backports. 

I have had difficulty with Firefox and Java. Concerning Firefox, the version available is 1.0.7, but requires a bunch of gnome libraries to install. My memory is a little fuzzy so I don't recall this being required, though I could be wrong. Is this normal? I'd like to avoid having to install the gnome libraries if possible. 

Also where'd Java go? Searching for either 'j2re, or 'j2se' yields no results. I haven't found w32codecs either but I installed them from the mplayer website so no biggie, just curious as to why so much stuff appears to be gone.

Other than that, I'm happy to be back with Hoary. After using Breezy it feels a little dated but I'll live. Thanks.[/QUOTE]


Ubuntuguide is outdated. The backports project is now official - and all unofficial mirrors may stop. However, official ones do not have "extras" - but some mirrors do. See discussions in  this forum 
[http://ubuntuforums.org/forumdisplay.php?f=82](http://ubuntuforums.org/forumdisplay.php?f=82)

---

### Post by escobar on 2005-11-01
[QUOTE=Alexander Kirillov]Ubuntuguide is outdated. The backports project is now official - and all unofficial mirrors may stop. However, official ones do not have "extras" - but some mirrors do. See discussions in  this forum 
[http://ubuntuforums.org/forumdisplay.php?f=82](http://ubuntuforums.org/forumdisplay.php?f=82)[/QUOTE]

I see, so I'll add some backport mirrors to get Java. I actually do have the official backport added to my sources list. About the firefox part of my question, anyone know? Thanks for your response.

---

### Post by Alexander Kirillov on 2005-11-02
[QUOTE=escobar]I see, so I'll add some backport mirrors to get Java. I actually do have the official backport added to my sources list. About the firefox part of my question, anyone know? Thanks for your response.[/QUOTE]
I use GNOME, so this is not an issue for me. 

Firefox definitely needs gtk packages (this is what it uses for GUI); I guess GNOME packages are used for things like file open/save dialog. 


In general,  there should be no problems with installing GNOME pacakges even if you use KDE as you DE.

---

