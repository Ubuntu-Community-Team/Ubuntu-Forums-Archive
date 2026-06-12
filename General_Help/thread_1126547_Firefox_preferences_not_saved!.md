---
title: "Firefox preferences not saved!"
date: 2009-04-15
forum: General Help
---

### Post by archeryguru2000 on 2009-04-15
I had a really weird problem with firefox.  Everytime I opened firefox anew, my preferences were reverted back to the default install values.  However after running the following command (cannot take credit, found it [**_[COLOR="Blue"]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=5270470#post5270472"))
```

sudo chown -R *username*:*username* /home/*username*/.mozilla

```
all preferences were restored.  :-k  That's doesn't seem quite normal.  Technically I do not have a problem (anymore).  However, I would still like to know why this happened in the first place so as to prevent it from happening again.  Any information?

~~archery~~

---

### Post by James_Lochhead on 2009-04-15
Most likely you were fiddling with something and changed the ownership by accident. Try and stay away from doing random commands if you do not have a rough idea of what is happening :-D

---

### Post by Monotoko on 2009-04-15
Well....Chown would give the user ownership over that file, so i think the permissions screwed up somewhere, and the user did not have write access to the mozilla configuration file, so it couldnt be saved and just used the defaults.

---

### Post by archeryguru2000 on 2009-04-15
Yes, I must have somehow changed (or allowed something else change) the ownership settings.  But I'm totally confused as to what it could have been.  I sure do not remember making any modifications within the past day or so.  As a matter of fact, I haven't updated/upgraded anything on my system in probably a week or so.

I'm currently taking a computer class that requires me write java scripts, and I've been creating some python scripts in my spare time... but nothing that requires su operation.

Anyway, I thought I would create this thread to see if anybody out there has any clues as to what have caused this to occur.

Thanks,
~~archery~~

---

### Post by Monotoko on 2009-04-15
You could always take a look at: /var/log/auth.log to see if anything was run as root

---

### Post by archeryguru2000 on 2009-04-16
> **Monotoko said:**
> You could always take a look at: /var/log/auth.log to see if anything was run as root

Good call Monotoko.  Checked each auth.log.* files (including compressed archives), but couldn't locate any references to the .mozilla directory except for my chown call.  Very stumped.

Oh well, I guess.  At least all is returned to normal.  Thanks for the assistance anyway.

~~archery~~

---

