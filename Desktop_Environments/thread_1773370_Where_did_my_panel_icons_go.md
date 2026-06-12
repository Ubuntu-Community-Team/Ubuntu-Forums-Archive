---
title: "Where did my panel icons go?"
date: 2011-06-02
forum: Desktop Environments
---

### Post by belltown on 2011-06-02
I'm using Ubuntu 11.04 with Gnome Classic. I used to have a set of icons in the top right-hand corner (bluetooth, wireless, mail, battery, volume, shutdown, etc.) I thought I'd try deleting ones I didn't use. I tried to delete the mail icon. This made all the rest of the icons disappear, too. How do I get them back?

---

### Post by mcduck on 2011-06-02
Those icons aren't individual applets, but instead just icons that appear inside the Indicator applet. So when you tried to delete one icon, you actually removed the Indicator applet instead.

...and the solution is simple: right-click on the panel, choose "Add to Panel", find the Indicator Applet and drag&drop it back into your panel. :)

---

### Post by belltown on 2011-06-02
> **mcduck said:**
> Those icons aren't individual applets, but instead just icons that appear inside the Indicator applet. So when you tried to delete one icon, you actually removed the Indicator applet instead.

...and the solution is simple: right-click on the panel, choose "Add to Panel", find the Indicator Applet and drag&drop it back into your panel. :)

Thanks. That worked. I've got them back now. "Indicator Applet Complete" was the one I must have had before.

---

### Post by Copper Bezel on 2011-06-02
You can also remove the individual services that display icons there if you aren't using them. For the mail icon, that's 

```
sudo apt-get remove indicator-messages
```

Since mcduck answered your original question, go ahead and mark the thread as solved via Thread Tools in the upper right.

---

