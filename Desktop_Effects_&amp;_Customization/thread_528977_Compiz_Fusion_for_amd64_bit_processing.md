---
title: "Compiz Fusion for amd64 bit processing?"
date: 2007-08-18
forum: Desktop Effects &amp; Customization
---

### Post by volksolwagen57 on 2007-08-18
None of the how-tos I've tried work. They either break apt-get or have this weird update redundancy that does not go away. Which repositories just work? Which how-to is tried and true? Thanks for your help in advance

---

### Post by Ub1476 on 2007-08-18
I have AMD64 Nvidia Geforce 7900 GS, and this works: [Link]("http://www.compiz.org/Compiz_and_Copmiz_Fusion_GIT_Ubuntu_Repository#amd64")

Before you install, remember to delete the .compizconfig in your home directory (ctrl+h to show hidden files) and do a "sudo apt-get autoremove" after you removed compiz core. Maybe a apt-get clean too just to be safe. Also reinstall Emerald (using the reps from the guide) and finally start compiz with: alt+F2 "compiz --replace".

At least if I don't do all those stuff, compiz wont be successfully installed somehow..

---

### Post by volksolwagen57 on 2007-08-20
thanks for your response but i get this error:
> volksolwagen@core2duo:~$ KEY=DD800CD9; sudo gpg --keyserver subkeys.pgp.net --recv $KEY && sudo gpg --export --armor $KEY | sudo apt-key add -
gpg: WARNING: unsafe ownership on configuration file `/home/volksolwagen/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
volksolwagen@core2duo:~$ 

I figure I need to add this key in sudo, in fact all of my installs are done in sudo and I'd like to keep it that way. Is there a way I can add this key, that is, an alternate way?
thanks for your help.

---

### Post by volksolwagen57 on 2007-08-20
or maybe it's that autoremove did not, for some reason, remove all the orphaned files and that this add key does not have permission to overwrite the filename that holds the key number already? what's the deal? thanks for listening.

---

### Post by wolf08 on 2007-08-21
> **volksolwagen57 said:**
> thanks for your response but i get this error:

I figure I need to add this key in sudo, in fact all of my installs are done in sudo and I'd like to keep it that way. Is there a way I can add this key, that is, an alternate way?
thanks for your help.

You do NOT need to add the key to gpg in sudo. Only to apt-key.

try this:

```
KEY=DD800CD9; gpg --keyserver subkeys.pgp.net --recv $KEY && gpg --export --armor $KEY | sudo apt-key add 
```

---

