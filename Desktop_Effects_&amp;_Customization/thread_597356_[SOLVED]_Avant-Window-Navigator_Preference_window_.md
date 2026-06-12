---
title: "[SOLVED] Avant-Window-Navigator Preference window does not open!"
date: 2007-10-30
forum: Desktop Effects &amp; Customization
---

### Post by tak1150 on 2007-10-30
I installed AWN using [this guide]("http://ubuntuforums.org/showthread.php?p=2307772"). It works perfectly! ... except the "preference" window. It does not come up when I right click AWN and click on "preference".

Has anybody experienced this and found a solution? Thanks!

---

### Post by uclalinux on 2007-10-31
try opening it with the command line.

---

### Post by tak1150 on 2007-10-31
> try opening it with the command line. 

What is the command? Thanks.

---

### Post by LeopoldBloom on 2007-10-31
It's Terminal. Go to Applications>Accessories>Terminal. You may want to do some more research before you run around in Terminal though.

---

### Post by tak1150 on 2007-10-31
> **LeopoldBloom said:**
> It's Terminal. Go to Applications>Accessories>Terminal. You may want to do some more research before you run around in Terminal though.

OK, I hope I am not being mocked here, but I do know how to open a terminal. I even have a short-cut key combination for it. So that I don't have to click 'n' click. Nevertheless, thank you for replying.

I simply do not know the command to open the preference window for AWN.

---

### Post by mrbungle on 2007-10-31
do you have the bar open? because you can also just right click it and select preferences.

that what i do atleast.   

nevermind i just saw you tried that.

---

### Post by sisco311 on 2007-10-31
awn-manager

---

### Post by tak1150 on 2007-10-31
> **sisco311 said:**
> awn-manager

Thank you.

Now I have an error message to work with.
```
tak@tak1150:~$ awn-manager 
Traceback (most recent call last):
  File "/usr/local/bin/awn-manager", line 43, in <module>
    from awnTheme import AwnThemeManager
ImportError: No module named awnTheme

```

If awn-manger works for you and you're using Gutsy, did you install it from the tuxfamily.org repository?

---

### Post by sisco311 on 2007-10-31
> If awn-manger works for you and you're using Gutsy, did you install it from the tuxfamily.org repository?Yes. I followed [this]("http://ubuntuforums.org/showthread.php?t=385981&highlight=avant-window-dnavigator+howto") guide.

i found [this]("http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=684&page=1&isLive=true") for your problem.

---

### Post by tak1150 on 2007-11-01
> **sisco311 said:**
> Yes. I followed [this]("http://ubuntuforums.org/showthread.php?t=385981&highlight=avant-window-dnavigator+howto") guide.

i found [this]("http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=684&page=1&isLive=true") for your problem.

Thanks Sisco311,

It took me a while to find absolutely everything that has to do with AWN. In the forum you linked, somebody said that deleting the files in /var was sufficient, but that wasn't enough for my system (besides, the deletion of the stuff in /var only lets you download again the same deb files). It most likely was the setting files in my /home that was the problem.

Anyhow, after deleting those things and installing AWN, everything works! Thank you!

Tak

---

### Post by retroactiv on 2008-02-18
I simply installed the manager by typing:

sudo apt-get install awn-manager

Then it worked.

---

