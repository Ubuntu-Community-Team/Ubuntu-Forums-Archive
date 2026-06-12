---
title: "rename home directory..."
date: 2007-12-18
forum: Desktop Environments
---

### Post by buccaneere on 2007-12-18
How do I change the name of my home directory? Nothing else.

I have only one folder on this new install, to have to worry about also changing names/ownership settings (although in THAT folder are 15 items).

Thanks........

---

### Post by HermanAB on 2007-12-18
Two things: First you have to log out and log in as root to rename the user home directory.  Then you need to change the user account settings with usermod, to point to the new directory.

Cheers,

Herman

---

### Post by buccaneere on 2007-12-19
> **HermanAB said:**
> Two things: First you have to log out and log in as root to rename the user home directory.  Then you need to change the user account settings with usermod, to point to the new directory.

Cheers,

Herman

Log out, huh? No execution from CLI as root user?

How do I log in as root user?

Change user account settings? From ? To ?

I'm no longer absolute, but nonetheless still a beginnoob.

Thanks tho'...

---

### Post by Nano Geek on 2007-12-19
To change your home directory, **Right-Click** on it and hit **Rename...** and name it whatever you want. Then go to **System=>Administration=>Users and Groups**. Click on your user then click **Properties=>Advanced** then change **Home directory:** to whatever you named yours.
Then reboot, and everything should work fine.

---

### Post by buccaneere on 2007-12-19
> **asjdfwejqrfjcvm msz34rq33 said:**
> To change your home directory, **Right-Click** on it and hit **Rename...** and name it whatever you want. Then go to **System=>Administration=>Users and Groups**. Click on your user then click **Properties=>Advanced** then change **Home directory:** to whatever you named yours.
Then reboot, and everything should work fine.

Thanks there asj-z, 0 -9!

Rt click to bring up rename option don't work. I'm not sure how to log in GUI as root user (I have to do that first, right?)

Users and groups management I can find my way, but I'm guessin' I have to follow your sequence for both steps???

---

### Post by Nano Geek on 2007-12-19
> **buccaneere said:**
> Thanks there asj-z, 0 -9!

Rt click to bring up rename option don't work. I'm not sure how to log in GUI as root user (I have to do that first, right?)

Users and groups management I can find my way, but I'm guessin' I have to follow your sequence for both steps???No, you actually dont' have to log in as root. Sorry for not explaining myself clearly. I mean for you to go to **Places=>Home Folder=>Up** and rename your home folder to whatever you want it to be called. 
Then just follow the steps after that and it should work.

---

### Post by buccaneere on 2007-12-19
> **asjdfwejqrfjcvm msz34rq33 said:**
> No, you actually dont' have to log in as root. Sorry for not explaining myself clearly. I mean for you to go to **[COLOR="Red"]Places=>Home Folder=>Up[/COLOR]** and rename your home folder to whatever you want it to be called. 
Then just follow the steps after that and it should work.

Yeah - I've tried that. Not only does it *not* say 'permission denied', but the rename option is greyed out.

Any clue?

---

### Post by Nano Geek on 2007-12-19
Oh of course, I should have thought of that.
Run **gksudo nautilus** and try it again.
EDIT: **gksudo nautilus** will log you in as a super-user. Be careful in there. ;)

---

