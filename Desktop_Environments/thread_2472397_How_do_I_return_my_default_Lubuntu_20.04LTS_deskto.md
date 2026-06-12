---
title: "How do I return my default Lubuntu 20.04LTS desktop to its original defaults?"
date: 2022-02-25
forum: Desktop Environments
---

### Post by goemonburo on 2022-02-25
A "gremlin" has managed to edit and change nearly all my defaults, such as font, wallpaper, screensaver, widgets, and so on.  Even the mouse pointer.  Rather than redo each one, is there any simple command (or folder to delete?) that will reset everything back to how it was?  I just want the plain defaults.  I tried "dconf -f /" but that didn't seem to work.  Anything else I can try?  

I'm on Lubuntu 20.04LTS.

---

### Post by GhX6GZMB on 2022-02-25
"Son, real men don't do backups. But they cry a lot."

Sorry, but that's the way it is. There is no one file that controls all this.

---

### Post by goemonburo on 2022-02-25
Haha, you are kidding me, @ml9104.  Really?!  

So for example, removing my .config file wouldn't do it?  Or copying over a bunch of defaults??

It has to get that way somehow, no?

---

### Post by goemonburo on 2022-02-25
(Love that quote by the way!)

---

### Post by guiverc on 2022-02-25
I don't know what settings you're asking about.

If it was me; then I'd probably create a new user account on your box; and explore what's there. It'll likely contain what you want, so you can always steal what it has & copy files to your own directory (*don't forget to change ownership to you post-copy*) as I've done that before. If you don't want to create another user, use another box; live-session or VM too.

Back to what settings... what comes to mind for me from your question is

[https://packages.ubuntu.com/focal/lubuntu-default-settings](https://packages.ubuntu.com/focal/lubuntu-default-settings)

The files it provides for *focal* or 20.04 can be seen at [https://packages.ubuntu.com/focal/all/lubuntu-default-settings/filelist](https://packages.ubuntu.com/focal/all/lubuntu-default-settings/filelist)

You may have changed other things too, which maybe covered by other packages (lubuntu artwork comes to mind - [https://packages.ubuntu.com/focal/lubuntu-artwork](https://packages.ubuntu.com/focal/lubuntu-artwork)) BUT again that's because I'm thinking global directories & not user directories.

If you're after a single command that fixes everything; sorry I agree with @ml9104

I tend to *test* my changes on other *testboxes* if I feel the results are dangerous, but most probably just spin up a VM & perform the test there, before impacting their own system.  I'm involved in QA (*Quality Assurance*) so having a *clean* install near by is the norm for me (*and I can destroy it as it'll get re-installed soon anyway*) which is why I don't use VMs.  Right now that's [20.04.4 installs]("https://lubuntu.me/focal-4-released/") too.

---

### Post by goemonburo on 2022-02-25
I swear it was not me who did these delightful changes.  Thank you for the suggestions.  :-)

---

### Post by uninvolved on 2022-02-25
I have no idea if it'd work, in fact it probably won't - as it'll have stored your current configurations, but *maybe* reinstalling the desktop? Something like:

```
sudo apt --reinstall install lubuntu-desktop
```

That has some chance of working as memory serves. I seem to recall at least once instance where it overwrote my existing configurations. It could also hose your system, so there's that. Maybe make a backup and try it?

---

### Post by GhX6GZMB on 2022-02-25
guiverc's suggestion of creating a new user and copying the settings to your own account is probably the best idea.

And I hope you've learned from this. Timeshift is your friend.

---

