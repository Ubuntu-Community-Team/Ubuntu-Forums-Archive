---
title: "All left clicks are drags"
date: 2011-03-07
forum: Desktop Environments
---

### Post by Fajner1 on 2011-03-07
I have several desktop environments, the default one of which is Gnome. All of a sudden when I log into Gnome, all left clicks anywhere except the taskbars are seen as drags, so I can't left click anything. Also, the taskbars don't recognize right clicks. Could this have happened because I changed a setting in one of the other environments (KDE, Xfce, LXDE)?

I'm posting this using KDE.

EDIT: Also, I forgot to add that if I load failsafe Gnome, it works normally again. I think the problem might also be due to the sticky notes feature?

---

### Post by Krytarik on 2011-03-07
Please check what is selected in "System -> Preferences -> Mouse -> Mouse Orientation".

---

### Post by Fajner1 on 2011-03-07
It's right handed.

---

### Post by Krytarik on 2011-03-07
How about the "Accessibility" options? I have nothing selected there.

---

### Post by Fajner1 on 2011-03-07
Neither do I. Should I try reinstalling Gnome?

---

### Post by Krytarik on 2011-03-07
> **Fajner1 said:**
> Should I try reinstalling Gnome?
No, not yet. But you could try creating a new user and logging in with those, "System -> Administration -> Users and Groups".

---

### Post by Fajner1 on 2011-03-08
Well, either way I would start with the default menu settings and such, and reinstalling Gnome is easier. I just go on Xfce, open Software Center, remove Gnome, and install Gnome.

---

### Post by Fajner1 on 2011-03-08
Ok, as it turns out, it's hard to uninstall Gnome. Is there a way to reset it?

---

### Post by Krytarik on 2011-03-08
> **Fajner1 said:**
> Is there a way to reset it?
Before trying that, I suggest checking if the issue also occurs with a fresh user account! Therefore add a new user via the respective tool in KDE/XFCE and login with those in Gnome.

---

### Post by Fajner1 on 2011-03-09
I logged into Gnome with both my other accounts; it's normal. But I don't really want to just start using another account unless there's nothing else possible, because I would have to transfer all my files and such, which would be pretty tedious.

---

### Post by Krytarik on 2011-03-09
Try resetting all the mouse settings:
- log into KDE or XFCE
- delete the directory "~/.gconf/desktop/gnome/peripherals/mouse"

Also you mentioned Sticky Notes, does the mouse work normal when you close it, or prevent that it runs at startup?

---

### Post by Fajner1 on 2011-03-09
How do I get to the directory? I know that somewhere there is a folder with a couple hundred folders within it, all beginning with a ".", but I can't find it.

---

### Post by Krytarik on 2011-03-09
> **Fajner1 said:**
> How do I get to the directory?
The "~" stands for "/home/USERNAME".

So the complete path would be like this: "/home/USERNAME/.gconf/desktop/gnome/peripherals/mouse".

---

### Post by Fajner1 on 2011-03-09
That's what I thought. And I remember those files being there once, but for quite a while they haven't been there. Could they be hidden?

---

### Post by Krytarik on 2011-03-09
> **Fajner1 said:**
> That's what I thought. And I remember those files being there once, but for quite a while they haven't been there. Could they be hidden?
All those config dirs are hidden, as well as the other config/log files at the toplevel of your home directory. In Thunar/XFCE you can unhide them by "View -> Show Hidden Files". I don't know the respective option in KDE. You could also simply enter the following command in a terminal/console:
```
rm -rf /home/USERNAME/.gconf/desktop/gnome/peripherals/mouse
```

---

### Post by Fajner1 on 2011-03-09
It worked! :D Thanks man!

---

### Post by Krytarik on 2011-03-09
> **Fajner1 said:**
> It worked! :D Thanks man!
Cool! Probably it was a faulty entry for "/desktop/gnome/peripherals/mouse/drag_threshold", I saw it when I checked on how to reset the mouse settings.

Tip: You can always use "gconf-editor" to see/change all -and even hidden- settings. The path I mentioned is the one you also see/can browse down in gconf-editor. But in your case you may not even have been able to use it.

---

### Post by Fajner1 on 2011-03-09
However, now whenever I change animation settings (right click on desktop -> change desktop background -> visual effects) to anything except "None", the leftclick=drag glitch happens again.

---

### Post by Krytarik on 2011-03-09
Then why did it work after resetting the mouse settings, had you desktop effects disabled at that time?

It seems to be related to Compiz or the running video driver. What video card/chip do you have, what driver are you running, how did you install those?

And does the issue also occur with the other user account, knowing now what the trigger is?

---

### Post by Fajner1 on 2011-03-12
The issue doesn't occur with the other accounts. I'm not sure which card I use, I'll have to check.

---

### Post by Krytarik on 2011-03-12
> **Fajner1 said:**
> The issue doesn't occur with the other accounts. I'm not sure which card I use, I'll have to check.
Not necessary to check it then.

Since I don't know exactly right now what in Compiz is causing this, would you have a problem with resetting *all* Compiz settings? If not, try removing/renaming both directories, "~/.compiz" and "~/.gconf/apps/compiz".

---

### Post by Fajner1 on 2011-03-15
Ok, I'll try that. Also, the problem is still present even though I've upgraded to Maverick, but since  I didn't do a clean install, it's not really a surprise.

---

