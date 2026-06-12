---
title: "Compiz in Gutsy"
date: 2008-01-04
forum: Desktop Effects &amp; Customization
---

### Post by thecrimsonalchemist42 on 2008-01-04
I am new to Ubuntu (and even newer to Gutsy Gibbon) and I was wondering how to enable Compiz Fusion in Gutsy. I have my ATI drivers running and I dont have XGL at the moment. I also believe I need Emerald. Anyways, any help I can get on the matter would be appreciated. And when I try to go to desktop effects under appearance, it always says the Composite extension is not available, so what do I do next? Help appreciated, thank you.

---

### Post by lordawesome on 2008-01-04
well, first you need to install compiz if you havent already. The easy way is to go to add/remove and do a search for compiz under all available software. At this point, you will need to check the box labeled advanced desktop effects. In order to run it, open a terminal and type compiz --replace and it should work as long as you have no issues with your video configuration as it stands. If you want it to start when the computer starts, click system then select preferences. Select sessions and add a new entry with the same command you used to start it from the terminal. If you run into any issues getting it to work, there are a lot of other forums here to help you solve your problems. Good luck!

---

### Post by thecrimsonalchemist42 on 2008-01-05
> **lordawesome said:**
> well, first you need to install compiz if you havent already. The easy way is to go to add/remove and do a search for compiz under all available software. At this point, you will need to check the box labeled advanced desktop effects. In order to run it, open a terminal and type compiz --replace and it should work as long as you have no issues with your video configuration as it stands. If you want it to start when the computer starts, click system then select preferences. Select sessions and add a new entry with the same command you used to start it from the terminal. If you run into any issues getting it to work, there are a lot of other forums here to help you solve your problems. Good luck!

Yea, I tried your compiz --replace idea and that didnt work, it still says "Composite extension is not available" and when I enter your compiz --replace code in the terminal it says this:

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

So I'm guessing I need XGL. Is that the problem? And if so how do I install XGL?

---

### Post by r41nz0r on 2008-01-05
Go to System > Preferences > Appearance and then to Visual Effects, Turn them on!


```
sudo apt-get install compizconfig-settings-manager
```

You will now have a new option Preferences to adjust advanced settings! Hope this helps! 

-Rain

---

### Post by thecrimsonalchemist42 on 2008-01-05
> **r41nz0r said:**
> Go to System > Preferences > Appearance and then to Visual Effects, Turn them on!


```
sudo apt-get install compizconfig-settings-manager
```

You will now have a new option Preferences to adjust advanced settings! Hope this helps! 

-Rain

Yea... I've already done that....

---

### Post by kimbledon on 2008-01-05
Maybe you could add your driver in the whitelist? I don't remember where the file that should be edited is, but try to google it.

---

