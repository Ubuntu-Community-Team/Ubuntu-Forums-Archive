---
title: "Conky 1.4.7: can't find .conckyrc"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by Rizlaw on 2007-10-21
I'm running Ubuntu 7.10. I just installed Conky 1.4.7 using Synaptic. I then looked for a menu entry to run Conky and found none, so I open a Terminal and typed "conky" and got Conky in the lower left corner of my screen as an overlay. Not good, since it messes up Avant-Window-Navigator. The conky website indicates that you can modify ".conkyrc" to make Conky open as a moveable window, but I can't find any "conkyrc" file to edit, nor is there a hidden (.conkyrc) folder in my /home folder or anywhere else in my filesystem.

Questions:

1. Where is my hidden ".conkyrc" folder located in Gutsy 7.10?

2. How do I find and edit the conkyrc file which doesn't seem to exist after my installation of Conky via Synaptic Package Manager.

 3. Is there a conkyrc file I can use that will work, in a moveable window, for Gutsy 7.10? Where can I download it and how would I install it?

Thanks for any help.

---

### Post by logos34 on 2007-10-21
it's not a folder but simply a text file.  should be in /home

---

### Post by WiFi Ed on 2007-10-21
[http://ubuntuforums.org/showthread.php?t=353362&highlight=conky]("http://ubuntuforums.org/showthread.php?t=353362&highlight=conky")

[http://ubuntuforums.org/showthread.php?t=281865]("http://ubuntuforums.org/showthread.php?t=281865")


There you will find all you need to know about Conky and examples of .conkyrc files:)

---

### Post by Rizlaw on 2007-10-21
There is no hidden text file or folder named conkyrc anywhere on my system.

---

### Post by NeoLithium on 2007-10-21
You can simply take that generic conkyrc from any of the threads linked to above, then open up a text editor, paste it all in, then save it in your /home/USERNAME directory as
.conkyrc
Ensure you put the . in front of it.  Should get you a base to start from.  Just be careful, customizing conky is pretty addictive :)

---

### Post by picpak on 2007-10-21
> **Rizlaw said:**
> There is no hidden text file or folder named conkyrc anywhere on my system.

Then create it. :)

```
touch .conkyrc
```

---

### Post by Rizlaw on 2007-10-21
Thanks for all the help guys.:) I've got it working now.

 IMO it seems that the Ubuntu folks should provide a default "windowed" conkyrc file as part of the basic Synaptic package installation, along with a menu entry under "Applications > Accessories".

---

### Post by picpak on 2007-10-21
> **Rizlaw said:**
> Thanks for all the help guys.:) I've got it working now.

 IMO it seems that the Ubuntu folks should provide a default "windowed" conkyrc file as part of the basic Synaptic package installation, along with a menu entry under "Applications > Accessories".

What about when you upgrade Conky? Would you then lose your .conkyrc?

---

### Post by Rizlaw on 2007-10-21
> **picpak said:**
> What about when you upgrade Conky? Would you then lose your .conkyrc?

I'm not sure how upgrades of Conky work under Synaptic, but I would think that if an upgrade sees an existing .conkyrc file, then it could either: ask the user if he/she wants to remove the existing file and install the new default.conkyrc file; or, the upgrade could just leave the existing .conkyrc file alone and simply install the main application.

---

