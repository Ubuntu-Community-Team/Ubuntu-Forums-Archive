---
title: "Having trouble installing Flash on 8.04 64 bit"
date: 2008-12-11
forum: General Help
---

### Post by CompSciSTL on 2008-12-11
I have a Wubi installation of Ubuntu 8.04 64-bit.  I tried to install Flash as described in post #14 of this link:

[http://ubuntuforums.org/showthread.php?t=999313&highlight=Flash+support+for+64-bit&page=2](http://ubuntuforums.org/showthread.php?t=999313&highlight=Flash+support+for+64-bit&page=2)

Unfortunately when I try to move the .so file from the desktop folder where it currently resides to the /usr/lib/mozilla/plugins folder, I get an error saying that I don't have the necessary permissions.  I'm a little puzzled as to why this is happening.  I looked at the permissions for my username in the Users and Groups menu, and I have about everything checked.  Do I need to adjust permissions somewhere?

Has anyone else experienced problems on a Wubi Installation of 8.04 64-bit?

---

### Post by Jammanuser on 2008-12-11
> **CompSciSTL said:**
> I have a Wubi installation of Ubuntu 8.04 64-bit.  I tried to install Flash as described in post #14 of this link:

[http://ubuntuforums.org/showthread.php?t=999313&highlight=Flash+support+for+64-bit&page=2](http://ubuntuforums.org/showthread.php?t=999313&highlight=Flash+support+for+64-bit&page=2)

Unfortunately when I try to move the .so file from the desktop folder where it currently resides to the /usr/lib/mozilla/plugins folder, I get an error saying that I don't have the necessary permissions.  I'm a little puzzled as to why this is happening.  I looked at the permissions for my username in the Users and Groups menu, and I have about everything checked.  Do I need to adjust permissions somewhere?

Has anyone else experienced problems on a Wubi Installation of 8.04 64-bit?

hmm...it sounds like u need sudo (root user) permissions to save to the folder! to open up the file browser as a root user, type this in a terminal:

```
gksu nautilus
```

Good luck! :guitar:

Jam Man

):P

---

### Post by CompSciSTL on 2008-12-12
Hmm...I transfered the .so file to /usr/lib/mozilla/plugins, but nothing is happening.  Do I need to do something else with it once the file is at that location?  :-k

---

### Post by Therion on 2008-12-12
Let's make this real simple.  

Shut down Firefox.

Fire up a Terminal.

Copy and Paste the following commands one at a time:

```
wget http://queleimporta.com/downloads/flash10_en.sh
```
```
sudo bash ./flash10_en.sh
```
Answer the prompts, restart Firefox and... Voila!  You're done.

---

### Post by CompSciSTL on 2008-12-12
WOOHOO!  It worked! Thank you very much!  =D>=D>=D>

---

