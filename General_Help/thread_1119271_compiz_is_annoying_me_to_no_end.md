---
title: "compiz is annoying me to no end"
date: 2009-04-07
forum: General Help
---

### Post by Daremo_06 on 2009-04-07
And I'm very close to ditching it.  There has to be something I am doing wrong.

I have compiz installed and have not really configured alot of things yet, but I have turned off wobbly windows cause I hate that effect.  The problem is, I have turned it off dozens of times.  Why doesn't it save that setting?  Furthermore, when I open System,Preferences, Appearance Preferences, and then click on the visual effects tab it has reset itself back to "Normal" instead of staying on "Extra" where I have set it at least a dozen times.

Whats going on here?  Do I not have my video configured correctly?  I don't see any issues going on with my dual displays and I am running 8.10 x64 with the newest Nvidia driver 180.44 with a 9400GT card.  Is there some setting somewhere I dont know about?

Thanks!

---

### Post by maheshasolkar on 2009-04-07
You can install compiz config setting manager and turn just wobbly windows plugin:

```
  sudo apt-get install compizconfig-settings-manager
```

That should install the setting manager under System -> Preferences.

---

### Post by Daremo_06 on 2009-04-07
> **maheshasolkar said:**
> You can install compiz config setting manager and turn just wobbly windows plugin:

```
  sudo apt-get install compizconfig-settings-manager
```

That should install the setting manager under System -> Preferences.

That is what i have been using to turn it off!

---

### Post by qamelian on 2009-04-07
> **Daremo_06 said:**
> That is what i have been using to turn it off!
You can't use both  CCSM and the Visual Effects tab in System > Preferences > Appearance. You need to use one or the other. As soon as you take the settings to extra in the Appearnace applet, that turns wobbly windows back on as it is a part of that preset.

---

### Post by Daremo_06 on 2009-04-07
> **qamelian said:**
> You can't use both  CCSM and the Visual Effects tab in System > Preferences > Appearance. You need to use one or the other. As soon as you take the settings to extra in the Appearnace applet, that turns wobbly windows back on as it is a part of that preset.

You would think that would be in one of the 9 billion faqs or posts on compiz.....

---

