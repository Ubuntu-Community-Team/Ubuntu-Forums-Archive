---
title: "Adjust gwibber notification bubble timeout?"
date: 2011-01-30
forum: Desktop Environments
---

### Post by Vanish00 on 2011-01-30
Simply, I want to adjust the notification bubble timeout for gwibber.  Anybody know how I would go about doing that?

---

### Post by Krytarik on 2011-01-31
> **Vanish00 said:**
> Simply, I want to adjust the notification bubble timeout for gwibber.  Anybody know how I would go about doing that?
Does it also use "notify-osd"? If so, try this:
[http://maketecheasier.com/easily-customize-notifyosd-ubuntu-lucid/2010/05/26](http://maketecheasier.com/easily-customize-notifyosd-ubuntu-lucid/2010/05/26)

---

### Post by Vanish00 on 2011-02-06
I tried out your link and installed NotifyOSD Configuration but notifies coming from the gwibber are still timing out under a second.  Any other suggestions?

---

### Post by sunny_sigara on 2011-10-25
To adjust gwibber notification u need to patch it first. There was a patch in Ubuntu 10.10(Gwibber 2.91.3).
See here:

[**https://bugs.launchpad.net/gwibber/+bug/726666**]("https://bugs.launchpad.net/gwibber/+bug/726666")

1.First patch it, then build & install it from source. 

2.Then open gconf-editor (press alt+F2 & type : gconf-editor).
Navigate to 
```
/apps/gwibber/preferences/notification_display_time
```, 
set the value 10,000 (for 10 sec) or whatever you like.

[IMG]http://img7.imagebanana.com/img/0kly7b5u/ConfigurationEditorpreferences_001.jpeg[/IMG]

3.Restart & you are done.

**[COLOR="Sienna"][SIZE="3"]Remember this patch is for gwibber 2.91.3, it may not work for gwibber 3.0 or higher.[/SIZE][/COLOR]**

---

### Post by gpain on 2011-10-26
I am trying to compile it but I got 2 errors when &quot;make&quot; it.

you can see all the details here:
[https://answers.launchpad.net/gwibber/+question/176397](https://answers.launchpad.net/gwibber/+question/176397)

 any help? thx

---

