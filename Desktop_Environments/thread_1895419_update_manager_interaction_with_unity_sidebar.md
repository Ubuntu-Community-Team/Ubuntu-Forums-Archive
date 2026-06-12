---
title: "update manager interaction with unity sidebar"
date: 2011-12-14
forum: Desktop Environments
---

### Post by gleedadswell on 2011-12-14
I kind of like that when the update manager comes up it just politely appears in the sidebar and that I can right click and choose "install all" from the right click menu.  But, when I left click the update manager icon on the sidebar shouldn't it launch the update manager interface so I can review the available updates and read the descriptions of them?  When I left click the update manager icon nothing happens.  If I want to read the descriptions of the updates I need to launch the update manager from Dash.

Is this a bug or something intentional?  Or have I unknowingly got some setting that causes this?

I'm using 11.10 on an HP 2000-240ca laptop (dual AMD E-350 processors, AMD Radeon HD 6300 graphics card).

---

### Post by jimmydean886-2 on 2011-12-14
I'm not sure if it's actually logged as a bug, but that happens to me too. I just use alt+tab to get to it and it comes right up.

---

### Post by racmar on 2011-12-15
Same thing has been happening to me for the last several weeks.  It is annoying, but I just close it and open a terminal to use apt-get.

Today I was annoyed with it and tried to delete the .update-manager-core from my home folder.

Can you try it and see if it works for you?

```
rm -rf ~/.update-manager-core/
```

---

### Post by racmar on 2011-12-15
After running:
```
update-manager --no-focus-on-map
```

I can see that my proposed fix did not work.

I've also tried:
```

sudo apt-get remove --purge update-manager* update-notifier*
sudo apt-get install update-manager update-notifier

```

I do notice that if I wait a few seconds for the number of packages to show up in the icon that I can open the update-manager after doing the remove/install from above.

Any other suggestions / fixes?

---

### Post by jimmydean886-2 on 2011-12-15
Click on the desktop, then try clicking the launcher again. That worked before alt+tab became habbit for me.

---

### Post by gleedadswell on 2011-12-15
Nope, none of those are working for me.  Clicking on the desktop then on the icon in the sidebar doesn't do anything.  Its icon appears among the others with ALT+Tab, but ALT-Tabbing to it doesn't bring it up.  Still the only way is to open it from Dash.

I notice that the little arrow pointing at it in the sidebar is solid light blue, but the arrows pointing at anything else is clear with a white outline if its not the active window and solid white if it is the active window.  Does the light blue arrow have some special meaning?

---

### Post by thaelim on 2011-12-16
When this happened to me, I go round it by right clicking the icon in the sidebar, clicking Quit/Close (whatever it's called), then manually starting update manager again.

---

### Post by gleedadswell on 2011-12-17
Yes, that's what I do as well.  It's just a minor annoyance to have to do this rather than have it launch properly from the sidebar.

---

### Post by gleedadswell on 2011-12-20
The other thing I've just noticed is that when I right click and choose "install all updates" from the sidebar it doesn't ask me for my password.  It just goes ahead and does the update.  That seems like a potential security hole.

---

