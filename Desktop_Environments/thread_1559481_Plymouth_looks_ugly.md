---
title: "Plymouth looks ugly"
date: 2010-08-23
forum: Desktop Environments
---

### Post by Screatch on 2010-08-23
I am using Linux Mint 9 (Lucid Lynx) and plymouth for some reason looks really ugly there. I downloaded a splash screen from here: 
[http://gnome-look.org/content/show.php/Ubuntu+10.04+and+10.10+Plymouth+Splash?content=128607](http://gnome-look.org/content/show.php/Ubuntu+10.04+and+10.10+Plymouth+Splash?content=128607)

And this is how it looks on my computer: [http://habreffect.ru/files/024/c96d8ab3a/DSC_4821.jpg](http://habreffect.ru/files/024/c96d8ab3a/DSC_4821.jpg)

Any guesses?

===
Solution posted on second page: [http://ubuntuforums.org/showthread.php?p=9761058#post9761058](http://ubuntuforums.org/showthread.php?p=9761058#post9761058)

---

### Post by mhgsys on 2010-08-23
> Note:
-Please before you install this theme make sure the plymouth is configured correctly with the screen resolution.

Arrange the colors and resolution of plymouth: **[http://portalubuntu.blogspot.com/2010/08/arreglar-los-colores-y-la-resollucion.html](http://portalubuntu.blogspot.com/2010/08/arreglar-los-colores-y-la-resollucion.html)**

-No guarantee that this theme be seen correctly in all screen resolutions.

Did you read this? and did you try to (re)arrange the colors and resolution?

And before you say:" I don't read Spanish" ... That's what google translate is for.
So here you go;

[http://translate.google.com/translate?js=y&prev=_t&hl=en&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Fportalubuntu.blogspot.com%2F2010%2F08%2Farreglar-los-colores-y-la-resollucion.html&sl=auto&tl=en](http://translate.google.com/translate?js=y&prev=_t&hl=en&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Fportalubuntu.blogspot.com%2F2010%2F08%2Farreglar-los-colores-y-la-resollucion.html&sl=auto&tl=en)

---

### Post by Screatch on 2010-08-23
Done that, didn't worked..

I've Googled for people with similar problems but none of their solutions didn't work for me.

---

### Post by mhgsys on 2010-08-23
I See; 

In mint it looks even easier btw; 

[http://community.linuxmint.com/tutorial/view/37](http://community.linuxmint.com/tutorial/view/37)


Also; I read here; (but that was in may) that the startup-manager wasn't rewritten for grub2 (yet/then); So if above isn't working out for you .. read this.

[http://forums.linuxmint.com/viewtopic.php?f=46&t=47330](http://forums.linuxmint.com/viewtopic.php?f=46&t=47330)

---

### Post by Screatch on 2010-08-23
Done that too...

Never worked :(
===
Also done what is written in your updated post.

---

### Post by mhgsys on 2010-08-23
You see; 
It's difficult for me to help you since I don't run Mint,. So I can't test it myself.

All I can do to help you right now is to search on the internet.. like you've been doing yourself.
(which is excellent btw.. most people don't do there own homework)

I might just install mint on a small partition on my laptop these days , dual booting it with 10.04.. 
Just because I can't stand the Plymouth problem your facing.

(Also; your original posting was only 2 hours ago... I'll bet (/ hope) there will be more (mint) users trying to help you.
although the most of them will be located here [http://forums.linuxmint.com/](http://forums.linuxmint.com/) I guess.

---

### Post by Screatch on 2010-08-23
Id appreciate that if you would take a look in teamviewer for example, just to check if i've done everything correctly.. maybe i've messed up somewhere... and btw, linux mint community is much smaller than the one on the ubuntuforums, and since mint is pretty much the same as ubuntu, decided to ask for help here. But i guess it'l be wise to wait until someone else will be able to help.

Ty anyway.

---

### Post by mhgsys on 2010-08-23
Sure; I'll take a look at it.. 

EDIT: fixed by now

---

### Post by Screatch on 2010-08-23
Just, can we make it tommorow? :)
I need some sleep, can you PM me your contacts like msn or icq or something, il contact you tommorow then :)

Thanks in advance.

---

### Post by mhgsys on 2010-08-23
Sure;
No Problem.

Actually need some sleep to.

I'll pm you my email 

for now have a good night.

EDIT: fixed by now

---

### Post by Screatch on 2010-08-24
Fixed, for anyone who needs fix.
The problem was in burg, all i needed to do is open
/etc/default/burg and add these 2 lines

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"
GRUB_GFXMODE=1280x1024
```

Replace resolution with what you got.

Then run update-burg and voila, plymouth should be fixed.
I didn't mention about burg at first because i didnt thought that the problem was in burg.

---

### Post by mhgsys on 2010-08-24
I would like to add TeamViewerv actually worked nicely..

---

### Post by nick_goodfate on 2010-08-24
> **Screatch said:**
> Fixed, for anyone who needs fix.
The problem was in burg, all i needed to do is open
/etc/default/burg and add these 2 lines

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"
GRUB_GFXMODE=1280x1024
```

Replace resolution with what you got.

Then run update-burg and voila, plymouth should be fixed.
I didn't mention about burg at first because i didnt thought that the problem was in burg.

Thank you for this solution!!

---

