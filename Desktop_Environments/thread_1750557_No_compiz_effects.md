---
title: "No compiz effects"
date: 2011-05-05
forum: Desktop Environments
---

### Post by calande on 2011-05-05
Hello,

I just upgraded to natty. I activated Compiz with wobbly windows in System > Preferences > Compiz Config Settings Manager, logged out and logged back in but I don't have the effects. How could I troubleshoot the problem please?
Thanks,

---

### Post by Copper Bezel on 2011-05-05
So you're using the Classic desktop then, and not "Classic (No Effects)", as I'm thinking is a separate session? And you had the wobbly windows after you activated them, but not after logging out and back in?

What happens if you try to run Compiz? 

```
setsid compiz --replace
```

Do your effects apply? 

I'm not certain what the default is in Natty, but if you run [font="Courier New"]gconf-editor[/font] and navigate to desktop > gnome > session > required_components, you should be able to set the command in the field "windowmanager" to [font="Courier New"]compiz[/font].

---

### Post by calande on 2011-05-06
Thanks, it's working now! :)

---

