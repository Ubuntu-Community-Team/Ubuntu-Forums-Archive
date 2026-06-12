---
title: "New Wave theme MISSING + new notification style for Volume Control MISSING."
date: 2009-04-23
forum: Desktop Environments
---

### Post by HOLY COW on 2009-04-23
After upgrading from Intrepid to Jaunty i have the following issues :

(please refer to the screenshot image attached herewith, thank you) 

1. The theme "New Wave" was missing from the theme set.
_[U]2. The Volume Control bar is not in the new slick notification style._[/U] - [COLOR="Red"]SOLVED[/COLOR] !
_3. The menu/gui for "some Administration programs" like Synaptic Package Manager,Login window,etc...looks pretty darn lame or windows 95 like when compared to the "theme" itself. _ - [COLOR="Red"]SOLVED[/COLOR] !

Any help would be highly appreciated ! 

Other than that everything else works like a charm.

[IMG]http://dl.getdropbox.com/u/541465/Screenshot1.png[/IMG]

---

### Post by HOLY COW on 2009-04-24
:( Is my post that repulsive ?? Seriously, no takers ? :confused:

---

### Post by roggenschrotbrot on 2009-04-26
regarding question 3:
execute
```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts
```

---

### Post by HOLY COW on 2009-04-26
@ roggenschrotbrot

Thanks a lot, that did the trick for issue # 3. 
It was bugging me quite a bit for some godforsaken reason.

---

### Post by Zunino on 2009-05-06
> **HOLY COW said:**
> After upgrading from Intrepid to Jaunty i have the following issues :

_[U]2. The Volume Control bar is not in the new slick notification style._[/U] - [COLOR="Red"]SOLVED[/COLOR] !
Hi, there! I've been trying to find a solution to the volume applet's appearance issue. Would you mind sharing how you've managed to get it fixed?

Thank you!

---

### Post by HOLY COW on 2009-05-07
> **Zunino said:**
> Hi, there! I've been trying to find a solution to the volume applet's appearance issue. Would you mind sharing how you've managed to get it fixed?

Thank you!

Hey there !

Sorry for the late reply.

The thing is, i had a misunderstanding of the volume applets appearance. By that i mean : i presumed this [IMG]http://dl.getdropbox.com/u/541465/Volume%20Bar.png[/IMG] to be result of when i click on volume control.

But the "new appearance" only shows when you change the volume via a keyboard shortcut. 

Conclusion : the new notification for the volume bar works flawlessly if your other notifications work too.

Either way I just had to install notify.osd via synaptic for all my notification needs.

:)

PS : let "us" know if you still have issues with it ? thanks !

---

### Post by Zunino on 2009-05-07
> **HOLY COW said:**
> But the "new appearance" only shows when you change the volume via a keyboard shortcut. 

Conclusion : the new notification for the volume bar works flawlessly if your other notifications work too.

Either way I just had to install notify.osd via synaptic for all my notification needs.
Hi, there. Thanks for the info. Notifications do seem to work fine here on my system. I get them from at least Pidgin and Rhythmbox. The funny thing is I never had to install anything like you mentioned. Do you have any idea why that was the case for you? Were you, somehow, upgrading from a previous version or did you do a clean install like me?

Thanks again!

---

### Post by HOLY COW on 2009-05-07
Hi,

The reason i had to do it was because i went from ubuntu 8.04 to 8.10 to 9.04 RC then the final ubuntu 9.04. So im guessing thats why i had issues ?!?

So do you still not get the new notification style for your volume bar via a keyboard shortcut or you dont get it period??

:)

---

### Post by Zunino on 2009-05-08
> **HOLY COW said:**
> The reason i had to do it was because i went from ubuntu 8.04 to 8.10 to 9.04 RC then the final ubuntu 9.04. So im guessing thats why i had issues ?!?
Well, that's what I'd suggested. I can't say for sure, but it seems like a reasonable assumption.

> **HOLY COW said:**
> So do you still not get the new notification style for your volume bar via a keyboard shortcut or you dont get it period??
I was actually satisfied to learn that there was nothing wrong or missing on my system. That's why I haven't even tried the keyboard shortcut... OK, I admit it, I don't know the volume shortcuts. :)

---

### Post by HOLY COW on 2009-05-08
:D Fair enough. If you want to check your keyboard shortcuts just go here :

System > Preferences > Keyboard Shortcuts 

There is not much to it :P

---

