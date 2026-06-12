---
title: "Why do I need &quot;compiz --replace&quot; to get Compiz working?"
date: 2011-05-07
forum: Desktop Environments
---

### Post by Navyblue on 2011-05-07
So my Compiz doesn't work any more after Natty upgrade, and Cairo Dock also has a black box around it.

After a bit of research I found that I am not alone and I needed to run "compiz --replace" to get them to work.

Is this a temporary bug that will get fixed in time? Or is it going to be this way from now on?

I am not sure if this is related, I also no longer have the "Visual Effect" tab under "System>Preferences>Appearance".

---

### Post by Frogs Hair on 2011-05-07
I have not tried a dock on 11.04 because I'm running Unity .The visual effects tab has been removed in 11.04 .

---

### Post by Navyblue on 2011-05-07
Thanks. Does that mean that Ubuntu is dropping Compiz?

---

### Post by Jesus_Valdez on 2011-05-08
> **Navyblue said:**
> Thanks. Does that mean that Ubuntu is dropping Compiz?
Unity is nothing but a compiz plugin.

---

### Post by d3v1150m471c on 2011-05-08
i'm not entirely sure why. I sacked gnome some time ago for blackbox. 
```

echo 'compiz --replace &' >> ~/.profile

```That might fix your problem by running it when you login.

---

### Post by Copper Bezel on 2011-05-08
Are you using "Classic" or "Classic - No Effects"?

Your default window manager is set to Metacity somewhere, most likely in gconf. Run gconf-editor and check desktop > gnome > session > required_components.

---

### Post by zteifel on 2011-05-13
Have you tried to log out and choose Ubuntu classic in the session droplist? Im guessing you are running the session Ubuntu classic (no effect)

---

