---
title: "flash videos not playing"
date: 2009-05-10
forum: General Help
---

### Post by AtomicQtip on 2009-05-10
On some websites the video will not load it is just  an open space on the page and no matter what i do it will not load. Anyone have any ideas as to why this is happening? I never had any problems with it until i installed the newest version of ubuntu.

---

### Post by Crafty Kisses on 2009-05-10
We need more information than that. What sites are you trying to visit that won't work? Are you on 64-bit Ubuntu or 32-bit Ubuntu? Do you have the following package installed?
```
ubuntu-restricted-extras
```
I'm guessing you do since you said it worked before, but we need some more information as I stated above.

---

### Post by wpshooter on 2009-05-10
When you say you installed the latest version of Ubuntu, did you upgrade from an older version or did you install new version from scratch ?

---

### Post by Miles_Prower on 2009-05-10
aw, I hate that mess. I'll go youtube or some wobsite with a flash video and all that renders is a solid-color rectangle. Sound might play. Bunk. If it's the same problem I'm having, you can point firefox to the desired website, then quit firefox (making sure to save all open tabs), then restart firefox. For some reason, when firefox starts, it plays whatever flash vids are in the open tabs flawlessly. I dont' get it, but it works, i guess...

---

### Post by wpshooter on 2009-05-10
> **Miles_Prower said:**
> aw, I hate that mess. I'll go youtube or some wobsite with a flash video and all that renders is a solid-color rectangle. Sound might play. Bunk. If it's the same problem I'm having, you can point firefox to the desired website, then quit firefox (making sure to save all open tabs), then restart firefox. For some reason, when firefox starts, it plays whatever flash vids are in the open tabs flawlessly. I dont' get it, but it works, i guess...

Mine works perfectly under version 9.04.  

My "guess" is that they do not have Adobe FlashPlayer installed **_correctly_**, note I said correctly.

---

### Post by AtomicQtip on 2009-05-10
> **wpshooter said:**
> Mine works perfectly under version 9.04.  

My "guess" is that they do not have Adobe FlashPlayer installed **_correctly_**, note I said correctly.

Care to enlighten me on the **_correct_** method of installing it?


Fresh install of Ubuntu 9.04 32 bit and i have the ubuntu-resticted-extras package installed.

---

### Post by wpshooter on 2009-05-10
> **AtomicQtip said:**
> Care to enlighten me on the **_correct_** method of installing it?


Fresh install of Ubuntu 9.04 32 bit and i have the ubuntu-resticted-extras package installed.

Certainly.

In my experience it is best in this case to not install Flash programs, plugins, etc. that are found under Synaptic (although USUALLY this should be the source of most programs used under Ubuntu) but to instead go to the Adobe website (the real one, not one of those fake ones) and download the Adobe Flashplayer tar file from there and then install the program from the installer once you have extracted the files from the tar file.

---

### Post by AtomicQtip on 2009-05-10
I just tryed that and it did not change anything. On some websites it works fine, on some it just loads an empty gray or white square and on others it will just say loading player or something like that and then it will never load. I wish i knew what was causing this it is starting to become somewhat irritating.

---

### Post by exutable on 2009-05-10
the best idea might just be to uninstall everything flash related and then install Adobe's prerelease flash player 10 for 64 bit

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by AtomicQtip on 2009-05-11
I had to uninstall the package called "swfdec-mozilla" and now everything is working fine.

---

