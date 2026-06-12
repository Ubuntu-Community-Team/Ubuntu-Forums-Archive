---
title: "/etc/init.d/ssh how soon does it start??"
date: 2009-01-02
forum: General Help
---

### Post by notquiterite on 2009-01-02
First post... so please be nice. ^_^   

   This is my predicament.  I have an iMac G5 with a bad video card.  When i turn it on i get nothing but static (not only when linux starts to load but from the second i press the power button).  If i plug in an external display I get similar distortion and nothing on the screen.  Fortunately I got Ubuntu installed before the video card went and it does an auto login to gnome.  I've also set vnc to start automatically so i can get in just fine.  This is my first serious attempt to get linux running (I tried when i was about 13 but i just couldn't wrap my head around it).  I have everything setup that i need running on the backend.  When i login ssh automatically starts as well(it's in /etc/init.d/ssh).  My question is, if i remove gdm from /etc/init.d will ssh still start automatically?  I've searched, but i can't find a definitive answer to when items in /etc/init.d are loaded.  This is very serious, because if i disable gdm, boot and ssh does not start, I'll have no way to get back into the system EVER.  I'm sure if i worked at it i could get something running again but it would be a huge headache.   
    I realize this post is awfully long for a simple question, i just wanted to give everyone the full picture.

-nqr
    
note: if this information is out there where i could easily find it, I apologize.  Sometimes it hard to search for something when you don't know what you're looking for.

---

### Post by y@w on 2009-01-02
No, don't take it out of /etc/init.d if you want it to start at boot.

---

### Post by notquiterite on 2009-01-02
maybe i didn't make myself clear.  i don NOT want GDM to start.  I want this server to be headless.... well it already is headless... seeing how i have a bum video card.   I just have no need for the gui to start.  I would like to have to boot into a console.  I just don't know if i have it boot directly to a console if that will prevent ssh from starting.

---

### Post by notquiterite on 2009-01-02
anyone?

---

### Post by cariboo on 2009-01-02
Ssh doesn't depend on a gui, so you can safely remove gdm. To remove gdm at the prompt type:

```
sudo update-rc.d -f gdm remove
```

This will remove gdm from startup without effecting anything else.

Jim

---

### Post by y@w on 2009-01-02
> **notquiterite said:**
> maybe i didn't make myself clear.  i don NOT want GDM to start.  I want this server to be headless.... well it already is headless... seeing how i have a bum video card.   I just have no need for the gui to start.  I would like to have to boot into a console.  I just don't know if i have it boot directly to a console if that will prevent ssh from starting.


Sorry.. I guess I can't read very well. :) You were clear enough. cariboo907 was exactly right. SSH will still start after disabling gdm.

---

