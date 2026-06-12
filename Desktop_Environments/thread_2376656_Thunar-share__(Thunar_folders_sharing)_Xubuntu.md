---
title: "Thunar-share ? (Thunar folders sharing) Xubuntu"
date: 2017-11-04
forum: Desktop Environments
---

### Post by mrouilla515 on 2017-11-04
I just realize that there is no extension in Xubuntu (17.10) for Thunar FM to share a folder. I also have Manjaro XFCE 17 installed and Thunar has a sharing extension called Thunar-share available which works fine. Is there a replacement in Xubuntu for that or it is simply not available.
How do you share a local folder then ?

---

### Post by #&amp;thj^% on 2017-11-04
Have  a look here: [https://ubuntuforums.org/showthread.php?t=2311605](https://ubuntuforums.org/showthread.php?t=2311605)
Take your time it is pretty straight  forward.

---

### Post by mrouilla515 on 2017-11-04
Ok thanks, I create the custom action like described and it went ok. I paste the line carefully and verify. However there is no such "share" selection when I right click on a local folder. I am missing something ?

---

### Post by #&amp;thj^% on 2017-11-04
That was pretty fast, are you sure you read all info and links provided?
And lets see what this reports from the terminal:
```
 apt policy samba
```
Not to confuse you any more but another good link is: [https://askubuntu.com/questions/101350/software-similar-to-nautilus-share-in-thunar](https://askubuntu.com/questions/101350/software-similar-to-nautilus-share-in-thunar)
Again take your time to fully understand the given information.

---

### Post by mrouilla515 on 2017-11-04
> **1fallen said:**
> That was pretty fast, are you sure you read all info and links provided?
And lets see what this reports from the terminal:
```
 apt policy samba
```
Not to confuse you any more but another good link is: [https://askubuntu.com/questions/101350/software-similar-to-nautilus-share-in-thunar](https://askubuntu.com/questions/101350/software-similar-to-nautilus-share-in-thunar)
Again take your time to fully understand the given information.


Ok I look at your second link. There is another thing you have to set, it is the type of files affected. I didn't realized that there is another tab in that window. I set it to "folder" and now I can see the shares on my network. So if I understand correctly, I have to create 2 customs entries. One to share and one to turn it off. Pretty cool but Manjaro made it more user friendly.

Thanks !!!

---

### Post by #&amp;thj^% on 2017-11-04
So are you happy with set-up...is it solved?
BTW manjaro is Arch with training wheels>>so a lot of stuff is pre-conconfigured for you the user.
Ubuntu/Debian and just pure Arch requires just a bit more of experience.
But isn't it fun Learning your system?  ;)

---

### Post by mrouilla515 on 2017-11-04
Yes perfect. I learn another thing today. Someone suggest Nautilus as a replacement but I prefer Thunar.
Not sure how to mark that thread solved. Is there a button somewhere ?

Got it !!! -> Solved. Appreciate your help 1Fallen. First class. Now next issue ....

---

### Post by #&amp;thj^% on 2017-11-04
Looks like you found it!
Have Fun!
Kind Regards

---

