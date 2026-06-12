---
title: "How to select Virtualbox window in Unity?"
date: 2012-12-02
forum: Desktop Environments
---

### Post by Geoff_L on 2012-12-02
Ubuntu 12.04 32bit / Virtualbox 4.1.12

I'm at my wit's end with an issue I have with with multiple Virtualbox windows run fullscreen under Unity. When I click the Virtualbox icon on the Dash, the last-accessed Virtualbox window opens. That's fine if that's the VM I want to work with but not so if I want to work with another since the open VB window prevents me from clicking the Dash icon and so I can't bring up the 'window selector'.

Is there a setting I've missed or some other way to let me switch to the window I want without needing to close down the last-used virtual machine?

TIA,

Geoff

---

### Post by Cheesemill on 2012-12-02
When you're in a VirtualBox window try hitting Right Ctrl to give focus back to Ubuntu and then ALT+` to cycle between VirtualBox instances (the ` key is usually above the TAB key).

If you aren't currently in a VirtualBox window then hold ALT and hit TAB until VirtualBox is highlighted and then without releasing ALT keep hitting ` until you reach the required window.

---

### Post by jerome1232 on 2012-12-02
Also if you click on the virtualbox icon in the launcher twice, you should be taken into scale mode which will show you a tiled view of your open virtualbox windows.

You can also access this scale mode by pressing super+w.

---

### Post by Geoff_L on 2012-12-02
> **Cheesemill said:**
> When you're in a VirtualBox window try hitting Right Ctrl to give focus back to Ubuntu and then ALT+` to cycle between VirtualBox instances (the ` key is usually above the TAB key).

If you aren't currently in a VirtualBox window then hold ALT and hit TAB until VirtualBox is highlighted and then without releasing ALT keep hitting ` until you reach the required window.
Thanks for that. Alt=` seems what I was missing!

It's a bit kludgy, but does work around the issue. It would have been good if clicking and holding on the Dash icon produced the application window thumbnails...

---

### Post by Geoff_L on 2012-12-02
> **jerome1232 said:**
> Also if you click on the virtualbox icon in the launcher twice, you should be taken into scale mode which will show you a tiled view of your open virtualbox windows.

You can also access this scale mode by pressing super+w.
Thanks for the response. Double-clicking the Virtualbox icon wasn't possible as the first click switched focus to the last-accessed VB window, which covered the Launcher icon thus making it impossible to click on that icon a second time!

However, super+w works well -- even if I had to search the Internet to find out that the 'Super' key is what Microsoft call the 'Windows' key. Thanks.

---

