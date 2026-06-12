---
title: "mupen64plus"
date: 2008-08-05
forum: Gaming &amp; Leisure
---

### Post by Aclockworkorang on 2008-08-05
I am struggling trying to install this. So I installed the tar file and extracted all of it's contacts into a folder on my destop named mupen

I log into root and well here's what it says:

root@chris-laptop:/home/chris# mupen/install.sh
Installing Mupen64Plus to /usr/local
/usr/bin/install: cannot stat `mupen64plus': No such file or directory
root@chris-laptop:/home/chris# 

And then when I try to move it into the /usr/bin folder it tells me I do not have the permissions. I feel like I already know I shouldn't have moved the file, but I really don't know what else to do, and it's probably something really easy, ha.

While not new to linux, there are often very remedial things I probably should be able to do but am unable to due to Ubuntu's normal ease of use and google helping me with most of my problems. Thank you in advance for any help you can offer.

---

### Post by geekygirl on 2008-08-06
Have you tried the .deb package from GetDeb? I used that and it works like a charm.


Sorry, I would post the link except I cannot access the GetDeb site from the work PC... :D

---

### Post by DirtDawg on 2008-08-06
Hi. You do not need to install mupen64Plus. If you download the Mupen64Plus-1-4-bin-32.zip, simply right-click to extract the package, then double-click the mupen64plus binary located inside the newly extracted directory (it uses a purple-diamondish icon).

Hope this helps.

---

### Post by BigSilly on 2008-08-06
I think the MupenPlus team have actually acknowledged there's a problem with their install script. I'm sure I read that somewhere. I never install it anyway, and just double click the launcher as DirtDawg says. I didn't know there was a .deb on GetDeb though. That would be a better option I reckon if you want to install it.

Sadly I'm going to have to wait for MupenPlus v1.5, as the current one (32bit) crashes a lot on me. Smash Bros., Goldeneye and some others don't get as far as the gameplay, so I'm going to hang on for the next version. :(

---

