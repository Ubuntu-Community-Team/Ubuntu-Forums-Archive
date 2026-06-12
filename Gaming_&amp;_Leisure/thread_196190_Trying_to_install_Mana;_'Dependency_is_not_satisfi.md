---
title: "Trying to install Mana; 'Dependency is not satisfiable: libguichan'  ?"
date: 2006-06-13
forum: Gaming &amp; Leisure
---

### Post by Raavea on 2006-06-13
I'm trying to install the Mana World.

 I downloaded the 0.0.16 .deb and double clicked, as I'd heard we could do that. It popped up and at the top of the window it says;

>  Status:  [COLOR="Red"]Error: Dependency is not satisfiable: libguichan[/COLOR]

 So I went into Synaptic and searched for 'guichan' and found libguichan0, which I installed. I open the .deb again, and it still says not satisfiable.

 What's wrong, what do I need to do to fix it? :?


A FAQ entry on their Wiki seemed similar, it directed me to a debian download for guichan.
Will update later if it works in case anyone else has the same issue...

(all the posts i found when i searched were oooold, you see!)



Okay, the guichan download did not work. Installation failed. :-x 
...It wouldn't let me copy paste, but something about can't overwrite babble and a broken pipe... :confused: 

I'm running outta ideas here... Gonna try uninstalling libguichan0 as that was mentioned to do with the thing it couldna overwrite... Done. Trying installing the .deb again...

Success! Now to try TMW...

AUGH! Still not satisfiable. FFS. -_-

---

### Post by Raavea on 2006-06-13
I'm leaving all the stuff in that top post as for all I know it might be useful to someone...

It would be very good if someone can point me in the right direction.... Most of the guides I have found are too old, and might not work with my Dapper installation... And TMW has updated and stuff too. So ya... /swt

---

### Post by Raavea on 2006-06-20
Err... Hate to do this, but mebbe it'll get me some help by the time I get back.

 *BUMP*

---

### Post by seth0x2b on 2006-06-20
```
sudo apt-get install libguichan0 libguichan0-dev
```

Cheers

---

