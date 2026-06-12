---
title: "Missing &quot;envelope&quot; icon"
date: 2010-06-14
forum: Desktop Environments
---

### Post by nortoncillo on 2010-06-14
hi, I've lost the "envelope" icon from the main bar... 

I have 10.4

it was there yesterday, but after a reboot it disappeared ... still have the accessiblity icon  ..

ehlp!

---

### Post by nortoncillo on 2010-06-16
found the solution on 
[http://ubuntuforums.org/showthread.php?t=1497925&highlight=missing+icon+volume](http://ubuntuforums.org/showthread.php?t=1497925&highlight=missing+icon+volume)

> Right click on the panel and select Add to Panel... In the window that appears scroll down the list until you find Indicator Applet and Add it.

done

---

### Post by oc666 on 2011-02-20
> **nortoncillo said:**
> found the solution on 
[http://ubuntuforums.org/showthread.php?t=1497925&highlight=missing+icon+volume](http://ubuntuforums.org/showthread.php?t=1497925&highlight=missing+icon+volume)



done

How could I put the envelop icon back to the notification area?

---

### Post by howefield on 2011-02-20
> **oc666 said:**
> How could I put the envelop icon back to the notification area?

Sometimes it is easier to simply put the panels back to default. This means any changes you made to the panel would need to be applied again.

To reset panels to default...

```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

Then

```
killall gnome-panel
```

---

### Post by oc666 on 2011-02-20
> **howefield said:**
> Sometimes it is easier to simply put the panels back to default. This means any changes you made to the panel would need to be applied again.

To reset panels to default...

```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

Then

```
killall gnome-panel
```

Works! Thanks!

---

